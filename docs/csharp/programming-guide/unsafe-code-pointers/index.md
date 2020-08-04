---
title: 不安全代码和指针 - C# 编程指南
Description: 了解不安全代码和指针。 C# 不支持指针，但你可以定义一个不安全的上下文，在该上下文中你可以将指针与“不安全”关键字一起使用。
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381770"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="4d79f-104">不安全代码和指针（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4d79f-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="4d79f-105">为了保持类型安全性，默认情况下，C# 不支持指针算法。</span><span class="sxs-lookup"><span data-stu-id="4d79f-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="4d79f-106">但是，通过使用 [unsafe](../../language-reference/keywords/unsafe.md) 关键字，可以定义可在其中使用指针的不安全上下文。</span><span class="sxs-lookup"><span data-stu-id="4d79f-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="4d79f-107">若要详细了解指针，请参阅[指针类型](pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4d79f-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d79f-108">在公共语言运行时 (CLR) 中，不安全代码是指无法验证的代码。</span><span class="sxs-lookup"><span data-stu-id="4d79f-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="4d79f-109">C# 中的不安全代码不一定是危险的；只是 CLR 无法验证该代码的安全性。</span><span class="sxs-lookup"><span data-stu-id="4d79f-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="4d79f-110">因此，CLR 将仅执行完全信任的程序集中的不安全代码。</span><span class="sxs-lookup"><span data-stu-id="4d79f-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="4d79f-111">如果你使用不安全代码，你应该负责确保代码不会引发安全风险或指针错误。</span><span class="sxs-lookup"><span data-stu-id="4d79f-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="4d79f-112">不安全代码概述</span><span class="sxs-lookup"><span data-stu-id="4d79f-112">Unsafe code overview</span></span>

<span data-ttu-id="4d79f-113">不安全代码具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="4d79f-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="4d79f-114">可将方法、类型和代码块定义为不安全。</span><span class="sxs-lookup"><span data-stu-id="4d79f-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="4d79f-115">在某些情况下，通过移除数组绑定检查，不安全代码可提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="4d79f-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="4d79f-116">调用需要指针的本机函数时，需使用不安全代码。</span><span class="sxs-lookup"><span data-stu-id="4d79f-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="4d79f-117">使用不安全代码将引发安全风险和稳定性风险。</span><span class="sxs-lookup"><span data-stu-id="4d79f-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="4d79f-118">必须使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 编译器选项来编译包含不安全块的代码。</span><span class="sxs-lookup"><span data-stu-id="4d79f-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="4d79f-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="4d79f-119">Related sections</span></span>

<span data-ttu-id="4d79f-120">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="4d79f-120">For more information, see:</span></span>

- [<span data-ttu-id="4d79f-121">指针类型</span><span class="sxs-lookup"><span data-stu-id="4d79f-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="4d79f-122">固定大小的缓冲区</span><span class="sxs-lookup"><span data-stu-id="4d79f-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="4d79f-123">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="4d79f-123">C# language specification</span></span>

<span data-ttu-id="4d79f-124">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[不安全代码](~/_csharplang/spec/unsafe-code.md)主题。</span><span class="sxs-lookup"><span data-stu-id="4d79f-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4d79f-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="4d79f-125">See also</span></span>

- [<span data-ttu-id="4d79f-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="4d79f-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4d79f-127">unsafe</span><span class="sxs-lookup"><span data-stu-id="4d79f-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
