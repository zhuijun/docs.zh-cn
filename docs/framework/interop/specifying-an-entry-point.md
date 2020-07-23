---
title: 指定入口点
description: 了解如何指定在 DLL 中标识函数位置的入口点。 可以通过将入口点映射到另一个名称来重命名该函数。
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: 5628c54103410d127c2f9c4f56e1c6f897ada754
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282016"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="0bc23-104">指定入口点</span><span class="sxs-lookup"><span data-stu-id="0bc23-104">Specifying an Entry Point</span></span>

<span data-ttu-id="0bc23-105">入口点标识 DLL 中的函数位置。</span><span class="sxs-lookup"><span data-stu-id="0bc23-105">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="0bc23-106">在托管项目中，目标函数的原始名称或序号入口点跨越互操作边界标识该函数。</span><span class="sxs-lookup"><span data-stu-id="0bc23-106">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="0bc23-107">此外，可将入口点映射到其他名称，有效地重命名该函数。</span><span class="sxs-lookup"><span data-stu-id="0bc23-107">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="0bc23-108">以下列表列出了重命名 DLL 函数的可能原因：</span><span class="sxs-lookup"><span data-stu-id="0bc23-108">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="0bc23-109">避免使用区分大小写的 API 函数名</span><span class="sxs-lookup"><span data-stu-id="0bc23-109">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="0bc23-110">符合现有的命名标准</span><span class="sxs-lookup"><span data-stu-id="0bc23-110">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="0bc23-111">提供采用不同数据类型的函数（通过声明同一 DLL 函数的多个版本）</span><span class="sxs-lookup"><span data-stu-id="0bc23-111">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="0bc23-112">简化对包含 ANSI 和 Unicode 版本的 API 的使用</span><span class="sxs-lookup"><span data-stu-id="0bc23-112">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="0bc23-113">本主题说明如何在托管代码中重命名 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="0bc23-113">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="0bc23-114">重命名 Visual Basic 中的函数</span><span class="sxs-lookup"><span data-stu-id="0bc23-114">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="0bc23-115">Visual Basic 在 Declare 语句中使用 Function 关键字设置 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 字段。</span><span class="sxs-lookup"><span data-stu-id="0bc23-115">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="0bc23-116">下面的示例演示了一个基本声明。</span><span class="sxs-lookup"><span data-stu-id="0bc23-116">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="0bc23-117">如下例所示，通过在定义中包括 Alias 关键字，可以用 MsgBox 替换 MessageBox 入口点  。</span><span class="sxs-lookup"><span data-stu-id="0bc23-117">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="0bc23-118">在这两个示例中，Auto 关键字使你无需指定入口点的字符集版本。</span><span class="sxs-lookup"><span data-stu-id="0bc23-118">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="0bc23-119">有关选择字符集的详细信息，请参阅[指定字符集](specifying-a-character-set.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc23-119">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="0bc23-120">重命名 C# 和 C++ 中的函数</span><span class="sxs-lookup"><span data-stu-id="0bc23-120">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="0bc23-121">可使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 字段通过名称或序号指定 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="0bc23-121">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="0bc23-122">如果方法定义中函数的名称与 DLL 中入口点的名称相同，则不必使用 EntryPoint 字段显式地标识函数。</span><span class="sxs-lookup"><span data-stu-id="0bc23-122">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="0bc23-123">否则，使用以下属性形式之一指示名称或序号：</span><span class="sxs-lookup"><span data-stu-id="0bc23-123">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="0bc23-124">请注意，序号前必须带有井号 (#)。</span><span class="sxs-lookup"><span data-stu-id="0bc23-124">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="0bc23-125">下面的示例演示如何使用 EntryPoint 字段将代码中的 MessageBoxA 替换为 MsgBox  。</span><span class="sxs-lookup"><span data-stu-id="0bc23-125">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="0bc23-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="0bc23-126">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="0bc23-127">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="0bc23-127">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="0bc23-128">平台调用示例</span><span class="sxs-lookup"><span data-stu-id="0bc23-128">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="0bc23-129">用平台调用封送数据</span><span class="sxs-lookup"><span data-stu-id="0bc23-129">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
