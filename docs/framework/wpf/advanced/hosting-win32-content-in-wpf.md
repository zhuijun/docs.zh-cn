---
title: 承载 Win32 内容
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: c0c62f1999feaf591c512314515f01e83fa12591
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052086"
---
# <a name="hosting-win32-content-in-wpf"></a>在 WPF 中承载 Win32 内容

## <a name="prerequisites"></a>先决条件

请参阅[WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)。

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Windows Presentation Framework 中的 Win32 演练（System.windows.interop.hwndhost>）

若要在应用程序中重复使用 Win32 内容 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，请使用 <xref:System.Windows.Interop.HwndHost> ，它是一个使 hwnd 看起来像内容的控件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 与类似 <xref:System.Windows.Interop.HwndSource> ， <xref:System.Windows.Interop.HwndHost> 简单易用：派生自 <xref:System.Windows.Interop.HwndHost> 并实现 `BuildWindowCore` 和 `DestroyWindowCore` 方法，然后实例化 <xref:System.Windows.Interop.HwndHost> 派生类并将其放置在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。

如果已将您的 Win32 逻辑打包为一个控件，则 `BuildWindowCore` 实现方式几乎不会调用 `CreateWindow` 。 例如，若要在 c + + 中创建 Win32 LISTBOX 控件：

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

但是，假设 Win32 代码不是很容易自包含？ 如果是这样，您可以创建一个 Win32 对话框，并将其内容嵌入到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。 此示例演示了 Visual Studio 和 c + + 中的此操作，但也可以用不同的语言或在命令行中执行此操作。

首先，使用一个简单的对话框，该对话框编译为 c + + DLL 项目。

接下来，将对话框引入到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序：

- 将 DLL 编译为托管（ `/clr` ）

- 将对话框变为控件

- <xref:System.Windows.Interop.HwndHost>用 `BuildWindowCore` 和 `DestroyWindowCore` 方法定义的派生类

- 重写 `TranslateAccelerator` 方法以处理对话框键

- 重写 `TabInto` 方法以支持 tab 键

- 重写 `OnMnemonic` 方法以支持助记键

- 实例化 <xref:System.Windows.Interop.HwndHost> 子类，并将其放在右 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素下

### <a name="turn-the-dialog-into-a-control"></a>将对话框变为控件

您可以使用 WS_CHILD 和 DS_CONTROL 样式将对话框转换为子 HWND。 进入对话框定义的资源文件（.rc），并找到对话框定义的开头：

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

将第二行更改为：

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

此操作不会将其完全打包到独立的控件中;你仍需要调用， `IsDialogMessage()` 以便 Win32 可以处理某些消息，但控制更改的确提供了将这些控件放在其他 HWND 中的一种简单方法。

## <a name="subclass-hwndhost"></a>子类 System.windows.interop.hwndhost>

导入下列命名空间：

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

然后创建的派生类 <xref:System.Windows.Interop.HwndHost> ，并重写 `BuildWindowCore` 和 `DestroyWindowCore` 方法：

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

在这里，您将使用 `CreateDialog` 创建真正是控件的对话框。 由于这是在 DLL 中调用的第一个方法，因此还应通过调用稍后定义的函数（称为 `InitializeGlobals()` ：

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>重写 TranslateAccelerator 方法以处理对话框键

如果现在运行此示例，您将看到一个对话框控件，该控件将显示，但会忽略使对话框成为功能对话框的所有键盘处理。 现在应重写 `TranslateAccelerator` 实现（来自 `IKeyboardInputSink` 实现的接口 <xref:System.Windows.Interop.HwndHost> ）。 当应用程序收到 WM_KEYDOWN 和 WM_SYSKEYDOWN 时，将调用此方法。

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

这是一个部分中的大量代码，因此它可以使用一些更详细的解释。 首先，使用 c + + 和 c + + 宏的代码;需要注意，已存在一个名为的宏 `TranslateAccelerator` ，该宏是在 winuser.h 中定义的：

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

因此，请确保定义 `TranslateAccelerator` 方法而不是 `TranslateAcceleratorW` 方法。

同样，还存在非托管的 winuser.h 消息和托管 `Microsoft::Win32::MSG` 结构。 你可以使用 c + + 运算符来区分二者之间的歧义 `::` 。

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

这两个消息具有相同的数据，但有时使用非托管定义会更容易，因此在本示例中，可以定义明显的转换例程：

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

返回到 `TranslateAccelerator` 。 基本原则是调用 Win32 函数 `IsDialogMessage` 来执行尽可能多的工作，但 `IsDialogMessage` 不能访问对话框以外的任何内容。 在对话框周围的 "用户" 选项卡上，当 tab 键在对话框中的最后一个控件之后运行时，需要通过调用将焦点设置到该 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 部分 `IKeyboardInputSite::OnNoMoreStops` 。

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

最后，调用 `IsDialogMessage`。 但方法的责任之一 `TranslateAccelerator` 就是指出是否已 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 处理击键。 如果未处理，输入事件可以通过应用程序的其余部分进行隧道和冒泡。 在这里，你将公开奇怪的键盘 messange 处理和 Win32 中输入体系结构的性质。 遗憾的 `IsDialogMessage` 是，不会以任何方式返回，无论是否处理特定的击键。 更糟的是，它会调用 `DispatchMessage()` 它不应处理的击键！  因此，你将需要进行反向工程 `IsDialogMessage` ，并且仅为你知道它将处理的密钥调用它：

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a>重写 TabInto 方法以支持 Tab 键

现在，你已经实现了 `TranslateAccelerator` ，用户可以在对话框内按 tab 键，然后将其移到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。 但是，用户不能通过 tab 键返回到对话框。 若要解决此情况，请重写 `TabInto` ：

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

`TraversalRequest`参数告诉您选项卡操作是制表符还是 shift 选项卡。

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>重写 OnMnemonic 方法以支持助记键

键盘处理几乎完成，但有一件事丢失–助记键不起作用。 如果用户按下 alt-F，焦点将无法跳到 "First name：" 编辑框。 因此，请重写 `OnMnemonic` 方法：

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

为什么不 `IsDialogMessage` 在此处调用？  你遇到的问题与以前相同，你需要能够通知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 代码你的代码是否已处理击键，而不 `IsDialogMessage` 能执行此操作。 还有另一个问题，因为 `IsDialogMessage` 如果焦点的 HWND 不在对话框内，拒绝处理助记键。

### <a name="instantiate-the-hwndhost-derived-class"></a>实例化 System.windows.interop.hwndhost> 派生类

最后，既然已准备好所有键和选项卡支持，你可以将添加 <xref:System.Windows.Interop.HwndHost> 到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。 如果主要应用程序是用编写的，则将 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 其放在正确的位置的最简单方法是将空元素保留在 <xref:System.Windows.Controls.Border> 要放置的位置 <xref:System.Windows.Interop.HwndHost> 。 在此处创建一个 <xref:System.Windows.Controls.Border> 名为的 `insertHwndHostHere` ：

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

接下来要做的就是在代码序列中找到一个合适的位置来实例化 <xref:System.Windows.Interop.HwndHost> ，并将其连接到 <xref:System.Windows.Controls.Border> 。 在此示例中，将其放在派生类的构造函数中 <xref:System.Windows.Window> ：

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

这为你提供：

![运行的 WPF 应用程序的屏幕截图。](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>请参阅

- [WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)
