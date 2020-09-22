---
title: 标识符太长
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: 084e3d9306ad84d7e6e36e5fe4bbfc868b8dfac6
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873998"
---
# <a name="identifier-is-too-long"></a><span data-ttu-id="7dfb5-102">标识符太长</span><span class="sxs-lookup"><span data-stu-id="7dfb5-102">Identifier is too long</span></span>

<span data-ttu-id="7dfb5-103">每个编程元素的名称或标识符限制为1023个字符。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="7dfb5-104">此外，完全限定的名称不能超过1023个字符。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="7dfb5-105">这意味着 () 的整个标识符字符串的 `<namespace>.<...>.<namespace>.<class>.<element>` 长度不能超过1023个字符，包括成员访问运算符 (`.`) 字符。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>  
  
 <span data-ttu-id="7dfb5-106">**错误 ID：** BC30033</span><span class="sxs-lookup"><span data-stu-id="7dfb5-106">**Error ID:** BC30033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7dfb5-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="7dfb5-107">To correct this error</span></span>  
  
- <span data-ttu-id="7dfb5-108">减小标识符的长度。</span><span class="sxs-lookup"><span data-stu-id="7dfb5-108">Reduce the length of the identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfb5-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dfb5-109">See also</span></span>

- [<span data-ttu-id="7dfb5-110">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="7dfb5-110">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
