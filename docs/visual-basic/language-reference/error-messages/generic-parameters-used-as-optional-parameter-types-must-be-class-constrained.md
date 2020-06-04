---
title: 用作可选参数类型的泛型参数必须受类约束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 273ea592e73be5d76a4ffef077e691014a108347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402922"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="90fd7-102">用作可选参数类型的泛型参数必须受类约束</span><span class="sxs-lookup"><span data-stu-id="90fd7-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="90fd7-103">使用可选参数声明过程，该参数使用的类型参数不被约束为引用类型。</span><span class="sxs-lookup"><span data-stu-id="90fd7-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="90fd7-104">必须始终为每个可选参数提供默认值。</span><span class="sxs-lookup"><span data-stu-id="90fd7-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="90fd7-105">如果参数为引用类型，则可选值必须为 `Nothing` ，它是任何引用类型的有效值。</span><span class="sxs-lookup"><span data-stu-id="90fd7-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="90fd7-106">但是，如果参数是值类型，则该类型必须是由 Visual Basic 预定义的基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="90fd7-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="90fd7-107">这是因为组合值类型（如用户定义的结构）没有有效的默认值。</span><span class="sxs-lookup"><span data-stu-id="90fd7-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="90fd7-108">将类型参数用于可选参数时，必须确保它是引用类型，以避免不具有有效默认值的值类型。</span><span class="sxs-lookup"><span data-stu-id="90fd7-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="90fd7-109">这意味着必须使用 `Class` 关键字或特定类的名称来约束类型参数。</span><span class="sxs-lookup"><span data-stu-id="90fd7-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="90fd7-110">**错误 ID：** BC32124</span><span class="sxs-lookup"><span data-stu-id="90fd7-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90fd7-111">更正此错误</span><span class="sxs-lookup"><span data-stu-id="90fd7-111">To correct this error</span></span>  
  
- <span data-ttu-id="90fd7-112">约束类型参数以仅接受引用类型，或不将其用于可选参数。</span><span class="sxs-lookup"><span data-stu-id="90fd7-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fd7-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90fd7-113">See also</span></span>

- [<span data-ttu-id="90fd7-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90fd7-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="90fd7-115">Type List</span><span class="sxs-lookup"><span data-stu-id="90fd7-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="90fd7-116">Class 语句</span><span class="sxs-lookup"><span data-stu-id="90fd7-116">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="90fd7-117">可选参数</span><span class="sxs-lookup"><span data-stu-id="90fd7-117">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="90fd7-118">结构</span><span class="sxs-lookup"><span data-stu-id="90fd7-118">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="90fd7-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="90fd7-119">Nothing</span></span>](../nothing.md)
