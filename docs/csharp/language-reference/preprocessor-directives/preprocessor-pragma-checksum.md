---
description: '#pragma checksum - C# 参考'
title: '#pragma checksum - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: df665704ac813adbbf6473e81fad0a1c7ff616d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168564"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="aac7d-103">#pragma checksum（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="aac7d-103">#pragma checksum (C# Reference)</span></span>

<span data-ttu-id="aac7d-104">生成源文件的校验和以帮助调试 ASP.NET 页面。</span><span class="sxs-lookup"><span data-stu-id="aac7d-104">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac7d-105">语法</span><span class="sxs-lookup"><span data-stu-id="aac7d-105">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="aac7d-106">参数</span><span class="sxs-lookup"><span data-stu-id="aac7d-106">Parameters</span></span>  

 `"filename"`  
 <span data-ttu-id="aac7d-107">需要监视更改或更新的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="aac7d-107">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="aac7d-108">哈希算法的全局唯一标识符 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="aac7d-108">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="aac7d-109">表示校验和字节的十六进制数字的字符串。</span><span class="sxs-lookup"><span data-stu-id="aac7d-109">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="aac7d-110">必须是偶数个十六进制数字。</span><span class="sxs-lookup"><span data-stu-id="aac7d-110">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="aac7d-111">奇数个十六进制数字会导致编译时警告出现，且指令遭忽略。</span><span class="sxs-lookup"><span data-stu-id="aac7d-111">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aac7d-112">备注</span><span class="sxs-lookup"><span data-stu-id="aac7d-112">Remarks</span></span>  

 <span data-ttu-id="aac7d-113">Visual Studio 调试器使用校验和确保它可始终找到正确的源。</span><span class="sxs-lookup"><span data-stu-id="aac7d-113">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="aac7d-114">编译器为源文件计算校验和，然后将输出发出到程序数据库 (PDB) 文件。</span><span class="sxs-lookup"><span data-stu-id="aac7d-114">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="aac7d-115">调试器随后使用 PDB 针对它为源文件计算的校验和进行比较。</span><span class="sxs-lookup"><span data-stu-id="aac7d-115">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="aac7d-116">此解决方案不适用于 ASP.NET 项目，因为计算的校验和用于生成的源文件，而不用于 .aspx 文件。</span><span class="sxs-lookup"><span data-stu-id="aac7d-116">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="aac7d-117">为解决此问题，`#pragma checksum` 为 ASP.NET 页面提供校验和支持。</span><span class="sxs-lookup"><span data-stu-id="aac7d-117">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="aac7d-118">在 Visual C# 中创建 ASP.NET 项目时，生成的源文件包含 .aspx 文件（从该文件生成源）的校验和。</span><span class="sxs-lookup"><span data-stu-id="aac7d-118">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="aac7d-119">编译器随后将此信息写入 PDB 文件中。</span><span class="sxs-lookup"><span data-stu-id="aac7d-119">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="aac7d-120">如果编译器在文件中未遇到 `#pragma checksum` 指令，则它会计算校验和并将值写入 PDB 文件中。</span><span class="sxs-lookup"><span data-stu-id="aac7d-120">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aac7d-121">示例</span><span class="sxs-lookup"><span data-stu-id="aac7d-121">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="aac7d-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="aac7d-122">See also</span></span>

- [<span data-ttu-id="aac7d-123">C# 参考</span><span class="sxs-lookup"><span data-stu-id="aac7d-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aac7d-124">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="aac7d-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aac7d-125">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="aac7d-125">C# Preprocessor Directives</span></span>](./index.md)
