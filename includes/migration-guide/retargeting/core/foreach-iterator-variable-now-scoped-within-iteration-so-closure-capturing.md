---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617123"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="f4e1d-101">Foreach 迭代器变量现在已在迭代范围内，因此闭包捕获语义会不同（在 C#5 中）</span><span class="sxs-lookup"><span data-stu-id="f4e1d-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="f4e1d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f4e1d-102">Details</span></span>

<span data-ttu-id="f4e1d-103">从 C# 5 (Visual Studio 2012) 开始，`foreach` 迭代器变量在迭代范围内。</span><span class="sxs-lookup"><span data-stu-id="f4e1d-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="f4e1d-104">如果代码以前依靠变量而不在 `foreach` 闭包内，这可能会导致中断。</span><span class="sxs-lookup"><span data-stu-id="f4e1d-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="f4e1d-105">此更改的特征如下：传递到委托的迭代器变量将视为委托创建时它拥有的值，而非调用委托时它拥有的值。</span><span class="sxs-lookup"><span data-stu-id="f4e1d-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f4e1d-106">建议</span><span class="sxs-lookup"><span data-stu-id="f4e1d-106">Suggestion</span></span>

<span data-ttu-id="f4e1d-107">理想情况下，应更新代码以使用新的编译器行为。</span><span class="sxs-lookup"><span data-stu-id="f4e1d-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="f4e1d-108">如果需要旧语义，迭代器变量可替换为显式置于循环范围外的单独变量。</span><span class="sxs-lookup"><span data-stu-id="f4e1d-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="f4e1d-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="f4e1d-109">Name</span></span>    | <span data-ttu-id="f4e1d-110">“值”</span><span class="sxs-lookup"><span data-stu-id="f4e1d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f4e1d-111">范围</span><span class="sxs-lookup"><span data-stu-id="f4e1d-111">Scope</span></span>   | <span data-ttu-id="f4e1d-112">主要</span><span class="sxs-lookup"><span data-stu-id="f4e1d-112">Major</span></span>       |
| <span data-ttu-id="f4e1d-113">Version</span><span class="sxs-lookup"><span data-stu-id="f4e1d-113">Version</span></span> | <span data-ttu-id="f4e1d-114">4.5</span><span class="sxs-lookup"><span data-stu-id="f4e1d-114">4.5</span></span>         |
| <span data-ttu-id="f4e1d-115">类型</span><span class="sxs-lookup"><span data-stu-id="f4e1d-115">Type</span></span>    | <span data-ttu-id="f4e1d-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="f4e1d-116">Retargeting</span></span> |
