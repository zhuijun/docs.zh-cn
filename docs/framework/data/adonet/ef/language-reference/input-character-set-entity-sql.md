---
title: 输入字符集 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 94615a8f4aec51347f451d6f6a53b9d5b459a336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203652"
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="7a0dd-102">输入字符集 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7a0dd-102">Input Character Set (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7a0dd-103">接受使用 UTF-16 进行编码的 UNICODE 字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-103">accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="7a0dd-104">字符串文字可以包含用单引号括起来的任何 UTF-16 字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="7a0dd-105">例如，N'文字列リテラル'。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="7a0dd-106">比较字符串文字时，将使用原始的 UTF-16 值。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="7a0dd-107">例如，N'ABC' 在日语代码页和拉丁语代码页中是不同的。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="7a0dd-108">注释可包含任何 UTF-16 字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="7a0dd-109">转义标识符可以包含用方括号括起来的任何 UTF-16 字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="7a0dd-110">例如，[エスケープされた識別子]。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="7a0dd-111">UTF-16 转义标识符的比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7a0dd-112">将看上去相同但来自不同代码页的字母视为不同的字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-112">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="7a0dd-113">例如，如果 [ABC] 和 [abc] 的字符来自同一代码页，则 [ABC] 等效于 [abc]。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="7a0dd-114">但如果这两个标识符来自不同的代码页，它们就不等效。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="7a0dd-115">空白是任何 UTF-16 空白字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="7a0dd-116">换行符是任何标准化的 UTF-16 换行符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="7a0dd-117">例如，'\n' 和 '\r\n' 被视为换行符，但 '\r' 不是换行符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="7a0dd-118">关键字、表达式和标点可以是任何标准化为拉丁语的 UTF-16 字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="7a0dd-119">例如，SELECT 在日语代码页中是有效的关键字。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="7a0dd-120">关键字、表达式和标点只能是拉丁语字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="7a0dd-121">`SELECT` 在日语代码页中不是关键字。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="7a0dd-122">+、-、 \* 、/、=、 (、) 、'、[，] 以及此处不带引号的任何其他语言构造只能是拉丁字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-122">+, -, \*, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="7a0dd-123">简单标识符只能为拉丁字符。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="7a0dd-124">这可以避免比较时的不确定性，因为比较时使用的是原始值。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="7a0dd-125">例如，在日语和拉丁语代码页中，ABC 将有所不同。</span><span class="sxs-lookup"><span data-stu-id="7a0dd-125">For example, ABC would be different in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0dd-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a0dd-126">See also</span></span>

- [<span data-ttu-id="7a0dd-127">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="7a0dd-127">Entity SQL Overview</span></span>](entity-sql-overview.md)
