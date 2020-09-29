---
description: '#pragma warning - C# 参考'
title: '#pragma warning - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5b67d384e37a5e509ce8ebcc5ddeb16a4437ea2b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168525"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="915a9-103">#pragma warning（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="915a9-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="915a9-104">`#pragma warning` 可以启用或禁用特定警告。</span><span class="sxs-lookup"><span data-stu-id="915a9-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915a9-105">语法</span><span class="sxs-lookup"><span data-stu-id="915a9-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="915a9-106">参数</span><span class="sxs-lookup"><span data-stu-id="915a9-106">Parameters</span></span>  

 `warning-list`  
 <span data-ttu-id="915a9-107">以逗号分隔的警告编号的列表。</span><span class="sxs-lookup"><span data-stu-id="915a9-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="915a9-108">“CS”前缀是可选的。</span><span class="sxs-lookup"><span data-stu-id="915a9-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="915a9-109">未指定警告编号时，`disable` 会禁用所有警告，`restore` 会启用所有警告。</span><span class="sxs-lookup"><span data-stu-id="915a9-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="915a9-110">若要在 Visual Studio 中查找警告编号，请生成项目，然后在“输出”\*\*\*\* 窗口中查找警告编号。</span><span class="sxs-lookup"><span data-stu-id="915a9-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="915a9-111">示例</span><span class="sxs-lookup"><span data-stu-id="915a9-111">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="915a9-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="915a9-112">See also</span></span>

- [<span data-ttu-id="915a9-113">C# 参考</span><span class="sxs-lookup"><span data-stu-id="915a9-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="915a9-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="915a9-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="915a9-115">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="915a9-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="915a9-116">C# 编译器错误</span><span class="sxs-lookup"><span data-stu-id="915a9-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
