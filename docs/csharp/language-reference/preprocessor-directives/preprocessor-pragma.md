---
description: '#pragma - C# 参考'
title: '#pragma - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 2788c2589bee149676c5cb2b4212ec7a060a47af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168512"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="1a903-103">#pragma（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="1a903-103">#pragma (C# Reference)</span></span>

<span data-ttu-id="1a903-104">`#pragma` 为编译器给出特殊指令以编译它所在的文件。</span><span class="sxs-lookup"><span data-stu-id="1a903-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="1a903-105">这些指令必须受编译器支持。</span><span class="sxs-lookup"><span data-stu-id="1a903-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="1a903-106">即是说，不可使用 `#pragma` 创建自定义处理指令。</span><span class="sxs-lookup"><span data-stu-id="1a903-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="1a903-107">Microsoft C# 编译器支持以下两种 `#pragma` 指令：</span><span class="sxs-lookup"><span data-stu-id="1a903-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="1a903-108">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="1a903-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="1a903-109">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="1a903-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="1a903-110">语法</span><span class="sxs-lookup"><span data-stu-id="1a903-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a903-111">参数</span><span class="sxs-lookup"><span data-stu-id="1a903-111">Parameters</span></span>  

 `pragma-name`  
 <span data-ttu-id="1a903-112">已识别杂注的名称。</span><span class="sxs-lookup"><span data-stu-id="1a903-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="1a903-113">特定于杂注的参数。</span><span class="sxs-lookup"><span data-stu-id="1a903-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a903-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="1a903-114">See also</span></span>

- [<span data-ttu-id="1a903-115">C# 参考</span><span class="sxs-lookup"><span data-stu-id="1a903-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1a903-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="1a903-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1a903-117">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="1a903-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="1a903-118">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="1a903-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="1a903-119">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="1a903-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
