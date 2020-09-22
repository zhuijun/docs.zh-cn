---
title: 语句在方法/多行 lambda 内无效
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: d5d756f1772b9519613e163119b88a3057d36cf3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870620"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="b7681-102">语句在方法/多行 lambda 内无效</span><span class="sxs-lookup"><span data-stu-id="b7681-102">Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="b7681-103">语句在 `Sub` 、 `Function` 、属性 `Get` 或属性过程中无效 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="b7681-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="b7681-104">某些语句可以放置在模块或类级别。</span><span class="sxs-lookup"><span data-stu-id="b7681-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="b7681-105">其他类（如 `Option Strict` ）必须位于命名空间级别，并位于所有其他声明之前。</span><span class="sxs-lookup"><span data-stu-id="b7681-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="b7681-106">**错误 ID：** BC30024</span><span class="sxs-lookup"><span data-stu-id="b7681-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7681-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="b7681-107">To correct this error</span></span>  
  
- <span data-ttu-id="b7681-108">删除过程中的语句。</span><span class="sxs-lookup"><span data-stu-id="b7681-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7681-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7681-109">See also</span></span>

- [<span data-ttu-id="b7681-110">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="b7681-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="b7681-111">Function 语句</span><span class="sxs-lookup"><span data-stu-id="b7681-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="b7681-112">Get 语句</span><span class="sxs-lookup"><span data-stu-id="b7681-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="b7681-113">Set 语句</span><span class="sxs-lookup"><span data-stu-id="b7681-113">Set Statement</span></span>](../statements/set-statement.md)
