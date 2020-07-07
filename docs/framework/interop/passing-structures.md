---
title: 传递结构
description: 了解如何将结构和类传递到非托管函数。 了解用于定义格式化类型的 StructLayoutAttribute 属性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: eae28d6746cd89d98b659b9eb957f158e1319190
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620815"
---
# <a name="passing-structures"></a><span data-ttu-id="4874f-104">传递结构</span><span class="sxs-lookup"><span data-stu-id="4874f-104">Passing Structures</span></span>
<span data-ttu-id="4874f-105">许多未托管的函数希望你以函数参数的形式传递结构成员（Visual Basic 中用户定义的类型），或托管代码中定义的类的成员。</span><span class="sxs-lookup"><span data-stu-id="4874f-105">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="4874f-106">使用平台调用将结构或类传递给非托管代码时，必须提供其他信息以保留原始布局和对齐方式。</span><span class="sxs-lookup"><span data-stu-id="4874f-106">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="4874f-107">本主题介绍用于定义格式化类型的 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="4874f-107">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="4874f-108">对于托管结构和类，可从 LayoutKind 枚举提供的几种可预测布局行为中进行选择。</span><span class="sxs-lookup"><span data-stu-id="4874f-108">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="4874f-109">本主题提出的概念核心是结构和类类型之间的重要区别。</span><span class="sxs-lookup"><span data-stu-id="4874f-109">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="4874f-110">结构是值类型，类是引用类型 - 类始终提供至少一个级别的内存间接（指向值的指针）。</span><span class="sxs-lookup"><span data-stu-id="4874f-110">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="4874f-111">这种差异很重要，因为未托管的函数通常要求间接，如下表第一列中的签名所示。</span><span class="sxs-lookup"><span data-stu-id="4874f-111">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="4874f-112">其余列中的托管结构和类声明显示可在声明中调整间接级别的程度。Visual Basic 和 Visual C# 均提供有声明。</span><span class="sxs-lookup"><span data-stu-id="4874f-112">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="4874f-113">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="4874f-113">Unmanaged signature</span></span>|<span data-ttu-id="4874f-114">托管的声明：</span><span class="sxs-lookup"><span data-stu-id="4874f-114">Managed declaration:</span></span> <br /><span data-ttu-id="4874f-115">非间接</span><span class="sxs-lookup"><span data-stu-id="4874f-115">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="4874f-116">托管的声明：</span><span class="sxs-lookup"><span data-stu-id="4874f-116">Managed declaration:</span></span> <br /><span data-ttu-id="4874f-117">一级间接</span><span class="sxs-lookup"><span data-stu-id="4874f-117">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="4874f-118">要求零级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-118">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="4874f-119">添加零级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-119">Adds zero levels of indirection.</span></span>|<span data-ttu-id="4874f-120">不可能，因为已存在一级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-120">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="4874f-121">要求一级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-121">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="4874f-122">添加一级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-122">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="4874f-123">添加零级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-123">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="4874f-124">要求二级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-124">Demands two levels of indirection.</span></span>|<span data-ttu-id="4874f-125">不可能，因为不能使用 ByRef ByRef 或 `ref` `ref`。</span><span class="sxs-lookup"><span data-stu-id="4874f-125">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="4874f-126">添加一级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-126">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="4874f-127">该表介绍了以下平台调用声明的准则：</span><span class="sxs-lookup"><span data-stu-id="4874f-127">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="4874f-128">当未托管的函数不要求间接时，使用由值传递的结构。</span><span class="sxs-lookup"><span data-stu-id="4874f-128">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="4874f-129">当未托管的函数要求一级间接时，使用由引用传递的结构或由值传递的类。</span><span class="sxs-lookup"><span data-stu-id="4874f-129">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="4874f-130">当未托管的函数要求二级间接时，使用由引用传递的类。</span><span class="sxs-lookup"><span data-stu-id="4874f-130">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="4874f-131">声明和传递结构</span><span class="sxs-lookup"><span data-stu-id="4874f-131">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="4874f-132">以下示例演示了如何在托管代码中定义 `Point` 和 `Rect` 结构，并将类型作为参数传递给 User32.dll 文件中的 PtInRect 函数。</span><span class="sxs-lookup"><span data-stu-id="4874f-132">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="4874f-133">PtInRect 具有以下非托管签名：</span><span class="sxs-lookup"><span data-stu-id="4874f-133">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="4874f-134">请注意，必须通过引用传递 Rect 结构，因为该函数需要指向 RECT 类型的指针。</span><span class="sxs-lookup"><span data-stu-id="4874f-134">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="4874f-135">声明和传递类</span><span class="sxs-lookup"><span data-stu-id="4874f-135">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="4874f-136">只要类具有固定成员布局，就可将类的成员传递给非托管 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="4874f-136">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="4874f-137">以下示例演示如何将按顺序定义的 `MySystemTime` 类的成员传递给 User32.dll 文件中的 GetSystemTime。</span><span class="sxs-lookup"><span data-stu-id="4874f-137">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="4874f-138">GetSystemTime 具有以下非托管签名：</span><span class="sxs-lookup"><span data-stu-id="4874f-138">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="4874f-139">与值类型不同，类总是至少具有一级间接。</span><span class="sxs-lookup"><span data-stu-id="4874f-139">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;
    public ushort wMonth;  
    public ushort wDayOfWeek;
    public ushort wDay;
    public ushort wHour;
    public ushort wMinute;
    public ushort wSecond;
    public ushort wMilliseconds;
}  
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4874f-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="4874f-140">See also</span></span>

- [<span data-ttu-id="4874f-141">调用 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="4874f-141">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
