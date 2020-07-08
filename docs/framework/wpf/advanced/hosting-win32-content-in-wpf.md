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
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="79cd8-102">在 WPF 中承载 Win32 内容</span><span class="sxs-lookup"><span data-stu-id="79cd8-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79cd8-103">先决条件</span><span class="sxs-lookup"><span data-stu-id="79cd8-103">Prerequisites</span></span>

<span data-ttu-id="79cd8-104">请参阅[WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="79cd8-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="79cd8-105">Windows Presentation Framework 中的 Win32 演练（System.windows.interop.hwndhost>）</span><span class="sxs-lookup"><span data-stu-id="79cd8-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="79cd8-106">若要在应用程序中重复使用 Win32 内容 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，请使用 <xref:System.Windows.Interop.HwndHost> ，它是一个使 hwnd 看起来像内容的控件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="79cd8-107">与类似 <xref:System.Windows.Interop.HwndSource> ， <xref:System.Windows.Interop.HwndHost> 简单易用：派生自 <xref:System.Windows.Interop.HwndHost> 并实现 `BuildWindowCore` 和 `DestroyWindowCore` 方法，然后实例化 <xref:System.Windows.Interop.HwndHost> 派生类并将其放置在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="79cd8-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="79cd8-108">如果已将您的 Win32 逻辑打包为一个控件，则 `BuildWindowCore` 实现方式几乎不会调用 `CreateWindow` 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="79cd8-109">例如，若要在 c + + 中创建 Win32 LISTBOX 控件：</span><span class="sxs-lookup"><span data-stu-id="79cd8-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

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

<span data-ttu-id="79cd8-110">但是，假设 Win32 代码不是很容易自包含？</span><span class="sxs-lookup"><span data-stu-id="79cd8-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="79cd8-111">如果是这样，您可以创建一个 Win32 对话框，并将其内容嵌入到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="79cd8-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="79cd8-112">此示例演示了 Visual Studio 和 c + + 中的此操作，但也可以用不同的语言或在命令行中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="79cd8-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="79cd8-113">首先，使用一个简单的对话框，该对话框编译为 c + + DLL 项目。</span><span class="sxs-lookup"><span data-stu-id="79cd8-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="79cd8-114">接下来，将对话框引入到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序：</span><span class="sxs-lookup"><span data-stu-id="79cd8-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="79cd8-115">将 DLL 编译为托管（ `/clr` ）</span><span class="sxs-lookup"><span data-stu-id="79cd8-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="79cd8-116">将对话框变为控件</span><span class="sxs-lookup"><span data-stu-id="79cd8-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="79cd8-117"><xref:System.Windows.Interop.HwndHost>用 `BuildWindowCore` 和 `DestroyWindowCore` 方法定义的派生类</span><span class="sxs-lookup"><span data-stu-id="79cd8-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="79cd8-118">重写 `TranslateAccelerator` 方法以处理对话框键</span><span class="sxs-lookup"><span data-stu-id="79cd8-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="79cd8-119">重写 `TabInto` 方法以支持 tab 键</span><span class="sxs-lookup"><span data-stu-id="79cd8-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="79cd8-120">重写 `OnMnemonic` 方法以支持助记键</span><span class="sxs-lookup"><span data-stu-id="79cd8-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="79cd8-121">实例化 <xref:System.Windows.Interop.HwndHost> 子类，并将其放在右 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素下</span><span class="sxs-lookup"><span data-stu-id="79cd8-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="79cd8-122">将对话框变为控件</span><span class="sxs-lookup"><span data-stu-id="79cd8-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="79cd8-123">您可以使用 WS_CHILD 和 DS_CONTROL 样式将对话框转换为子 HWND。</span><span class="sxs-lookup"><span data-stu-id="79cd8-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="79cd8-124">进入对话框定义的资源文件（.rc），并找到对话框定义的开头：</span><span class="sxs-lookup"><span data-stu-id="79cd8-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="79cd8-125">将第二行更改为：</span><span class="sxs-lookup"><span data-stu-id="79cd8-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="79cd8-126">此操作不会将其完全打包到独立的控件中;你仍需要调用， `IsDialogMessage()` 以便 Win32 可以处理某些消息，但控制更改的确提供了将这些控件放在其他 HWND 中的一种简单方法。</span><span class="sxs-lookup"><span data-stu-id="79cd8-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="79cd8-127">子类 System.windows.interop.hwndhost></span><span class="sxs-lookup"><span data-stu-id="79cd8-127">Subclass HwndHost</span></span>

<span data-ttu-id="79cd8-128">导入下列命名空间：</span><span class="sxs-lookup"><span data-stu-id="79cd8-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="79cd8-129">然后创建的派生类 <xref:System.Windows.Interop.HwndHost> ，并重写 `BuildWindowCore` 和 `DestroyWindowCore` 方法：</span><span class="sxs-lookup"><span data-stu-id="79cd8-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="79cd8-130">在这里，您将使用 `CreateDialog` 创建真正是控件的对话框。</span><span class="sxs-lookup"><span data-stu-id="79cd8-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="79cd8-131">由于这是在 DLL 中调用的第一个方法，因此还应通过调用稍后定义的函数（称为 `InitializeGlobals()` ：</span><span class="sxs-lookup"><span data-stu-id="79cd8-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="79cd8-132">重写 TranslateAccelerator 方法以处理对话框键</span><span class="sxs-lookup"><span data-stu-id="79cd8-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="79cd8-133">如果现在运行此示例，您将看到一个对话框控件，该控件将显示，但会忽略使对话框成为功能对话框的所有键盘处理。</span><span class="sxs-lookup"><span data-stu-id="79cd8-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="79cd8-134">现在应重写 `TranslateAccelerator` 实现（来自 `IKeyboardInputSink` 实现的接口 <xref:System.Windows.Interop.HwndHost> ）。</span><span class="sxs-lookup"><span data-stu-id="79cd8-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="79cd8-135">当应用程序收到 WM_KEYDOWN 和 WM_SYSKEYDOWN 时，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="79cd8-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="79cd8-136">这是一个部分中的大量代码，因此它可以使用一些更详细的解释。</span><span class="sxs-lookup"><span data-stu-id="79cd8-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="79cd8-137">首先，使用 c + + 和 c + + 宏的代码;需要注意，已存在一个名为的宏 `TranslateAccelerator` ，该宏是在 winuser.h 中定义的：</span><span class="sxs-lookup"><span data-stu-id="79cd8-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="79cd8-138">因此，请确保定义 `TranslateAccelerator` 方法而不是 `TranslateAcceleratorW` 方法。</span><span class="sxs-lookup"><span data-stu-id="79cd8-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="79cd8-139">同样，还存在非托管的 winuser.h 消息和托管 `Microsoft::Win32::MSG` 结构。</span><span class="sxs-lookup"><span data-stu-id="79cd8-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="79cd8-140">你可以使用 c + + 运算符来区分二者之间的歧义 `::` 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}
```

<span data-ttu-id="79cd8-141">这两个消息具有相同的数据，但有时使用非托管定义会更容易，因此在本示例中，可以定义明显的转换例程：</span><span class="sxs-lookup"><span data-stu-id="79cd8-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>

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

<span data-ttu-id="79cd8-142">返回到 `TranslateAccelerator` 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-142">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="79cd8-143">基本原则是调用 Win32 函数 `IsDialogMessage` 来执行尽可能多的工作，但 `IsDialogMessage` 不能访问对话框以外的任何内容。</span><span class="sxs-lookup"><span data-stu-id="79cd8-143">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="79cd8-144">在对话框周围的 "用户" 选项卡上，当 tab 键在对话框中的最后一个控件之后运行时，需要通过调用将焦点设置到该 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 部分 `IKeyboardInputSite::OnNoMoreStops` 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="79cd8-145">最后，调用 `IsDialogMessage`。</span><span class="sxs-lookup"><span data-stu-id="79cd8-145">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="79cd8-146">但方法的责任之一 `TranslateAccelerator` 就是指出是否已 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 处理击键。</span><span class="sxs-lookup"><span data-stu-id="79cd8-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="79cd8-147">如果未处理，输入事件可以通过应用程序的其余部分进行隧道和冒泡。</span><span class="sxs-lookup"><span data-stu-id="79cd8-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="79cd8-148">在这里，你将公开奇怪的键盘 messange 处理和 Win32 中输入体系结构的性质。</span><span class="sxs-lookup"><span data-stu-id="79cd8-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="79cd8-149">遗憾的 `IsDialogMessage` 是，不会以任何方式返回，无论是否处理特定的击键。</span><span class="sxs-lookup"><span data-stu-id="79cd8-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="79cd8-150">更糟的是，它会调用 `DispatchMessage()` 它不应处理的击键！</span><span class="sxs-lookup"><span data-stu-id="79cd8-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="79cd8-151">因此，你将需要进行反向工程 `IsDialogMessage` ，并且仅为你知道它将处理的密钥调用它：</span><span class="sxs-lookup"><span data-stu-id="79cd8-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="79cd8-152">重写 TabInto 方法以支持 Tab 键</span><span class="sxs-lookup"><span data-stu-id="79cd8-152">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="79cd8-153">现在，你已经实现了 `TranslateAccelerator` ，用户可以在对话框内按 tab 键，然后将其移到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="79cd8-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="79cd8-154">但是，用户不能通过 tab 键返回到对话框。</span><span class="sxs-lookup"><span data-stu-id="79cd8-154">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="79cd8-155">若要解决此情况，请重写 `TabInto` ：</span><span class="sxs-lookup"><span data-stu-id="79cd8-155">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="79cd8-156">`TraversalRequest`参数告诉您选项卡操作是制表符还是 shift 选项卡。</span><span class="sxs-lookup"><span data-stu-id="79cd8-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="79cd8-157">重写 OnMnemonic 方法以支持助记键</span><span class="sxs-lookup"><span data-stu-id="79cd8-157">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="79cd8-158">键盘处理几乎完成，但有一件事丢失–助记键不起作用。</span><span class="sxs-lookup"><span data-stu-id="79cd8-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="79cd8-159">如果用户按下 alt-F，焦点将无法跳到 "First name：" 编辑框。</span><span class="sxs-lookup"><span data-stu-id="79cd8-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="79cd8-160">因此，请重写 `OnMnemonic` 方法：</span><span class="sxs-lookup"><span data-stu-id="79cd8-160">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="79cd8-161">为什么不 `IsDialogMessage` 在此处调用？</span><span class="sxs-lookup"><span data-stu-id="79cd8-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="79cd8-162">你遇到的问题与以前相同，你需要能够通知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 代码你的代码是否已处理击键，而不 `IsDialogMessage` 能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="79cd8-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="79cd8-163">还有另一个问题，因为 `IsDialogMessage` 如果焦点的 HWND 不在对话框内，拒绝处理助记键。</span><span class="sxs-lookup"><span data-stu-id="79cd8-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="79cd8-164">实例化 System.windows.interop.hwndhost> 派生类</span><span class="sxs-lookup"><span data-stu-id="79cd8-164">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="79cd8-165">最后，既然已准备好所有键和选项卡支持，你可以将添加 <xref:System.Windows.Interop.HwndHost> 到更大的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="79cd8-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="79cd8-166">如果主要应用程序是用编写的，则将 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 其放在正确的位置的最简单方法是将空元素保留在 <xref:System.Windows.Controls.Border> 要放置的位置 <xref:System.Windows.Interop.HwndHost> 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="79cd8-167">在此处创建一个 <xref:System.Windows.Controls.Border> 名为的 `insertHwndHostHere` ：</span><span class="sxs-lookup"><span data-stu-id="79cd8-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="79cd8-168">接下来要做的就是在代码序列中找到一个合适的位置来实例化 <xref:System.Windows.Interop.HwndHost> ，并将其连接到 <xref:System.Windows.Controls.Border> 。</span><span class="sxs-lookup"><span data-stu-id="79cd8-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="79cd8-169">在此示例中，将其放在派生类的构造函数中 <xref:System.Windows.Window> ：</span><span class="sxs-lookup"><span data-stu-id="79cd8-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="79cd8-170">这为你提供：</span><span class="sxs-lookup"><span data-stu-id="79cd8-170">Which gives you:</span></span>

![运行的 WPF 应用程序的屏幕截图。](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="79cd8-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="79cd8-172">See also</span></span>

- [<span data-ttu-id="79cd8-173">WPF 和 Win32 互操作</span><span class="sxs-lookup"><span data-stu-id="79cd8-173">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
