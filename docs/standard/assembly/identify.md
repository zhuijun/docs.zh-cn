---
title: 如何：确定文件是否为程序集
description: 本文介绍如何以手动和编程方式确定文件是否是 .NET 程序集。
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: fb1bcfa50ec380f10ab67cc47331f91dc3e4b32d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380149"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c563f-103">如何：确定文件是否为程序集</span><span class="sxs-lookup"><span data-stu-id="c563f-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="c563f-104">当且仅当程序集处于托管状态，并在其元数据中包含程序集条目时，该文件才为程序集。</span><span class="sxs-lookup"><span data-stu-id="c563f-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="c563f-105">有关程序集和元数据的详细信息，请参阅[程序集清单](manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="c563f-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c563f-106">如何手动确定文件是否为程序集</span><span class="sxs-lookup"><span data-stu-id="c563f-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="c563f-107">启动 [Ildasm.exe（IL 反汇编程序）](../../framework/tools/ildasm-exe-il-disassembler.md)。</span><span class="sxs-lookup"><span data-stu-id="c563f-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="c563f-108">加载要测试的文件。</span><span class="sxs-lookup"><span data-stu-id="c563f-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="c563f-109">如果 **ILDASM** 报告文件不是可移植的可执行 (PE) 文件，则不是程序集。</span><span class="sxs-lookup"><span data-stu-id="c563f-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="c563f-110">有关详细信息，请参阅主题[如何：查看程序集内容](view-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="c563f-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="c563f-111">如何以编程方式确定文件是否为程序集</span><span class="sxs-lookup"><span data-stu-id="c563f-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="c563f-112">调用 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法，传递要测试的文件的完整文件路径和名称。</span><span class="sxs-lookup"><span data-stu-id="c563f-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="c563f-113">如果引发 <xref:System.BadImageFormatException> 异常，则该文件不是程序集。</span><span class="sxs-lookup"><span data-stu-id="c563f-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c563f-114">示例</span><span class="sxs-lookup"><span data-stu-id="c563f-114">Example</span></span>  
<span data-ttu-id="c563f-115">此示例测试 DLL 以查看其是否为程序集。</span><span class="sxs-lookup"><span data-stu-id="c563f-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<span data-ttu-id="c563f-116"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> 方法加载测试文件，然后在读取信息之后释放它。</span><span class="sxs-lookup"><span data-stu-id="c563f-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c563f-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="c563f-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="c563f-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c563f-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c563f-119">编程概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c563f-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="c563f-120">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="c563f-120">Assemblies in .NET</span></span>](index.md)
