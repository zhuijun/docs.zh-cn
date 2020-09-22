---
title: 枚举的基础类型 <typename> 不符合 CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 8d27039c28cd3f680e441db9182dd415bd8e91ba
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870262"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="12ba0-102">枚举的基础类型 \<typename> 不符合 CLS</span><span class="sxs-lookup"><span data-stu-id="12ba0-102">Underlying type \<typename> of Enum is not CLS-compliant</span></span>

<span data-ttu-id="12ba0-103">为此枚举指定的数据类型不是 [语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="12ba0-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="12ba0-104">这不是你的组件中的错误，因为 .NET Framework 和 Visual Basic 支持此数据类型。</span><span class="sxs-lookup"><span data-stu-id="12ba0-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="12ba0-105">但是，以严格符合 CLS 的代码编写的另一个组件可能不支持此数据类型。</span><span class="sxs-lookup"><span data-stu-id="12ba0-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="12ba0-106">此类组件可能无法与组件成功交互。</span><span class="sxs-lookup"><span data-stu-id="12ba0-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="12ba0-107">以下 Visual Basic 数据类型不符合 CLS：</span><span class="sxs-lookup"><span data-stu-id="12ba0-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="12ba0-108">SByte 数据类型</span><span class="sxs-lookup"><span data-stu-id="12ba0-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="12ba0-109">UInteger 数据类型</span><span class="sxs-lookup"><span data-stu-id="12ba0-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="12ba0-110">ULong 数据类型</span><span class="sxs-lookup"><span data-stu-id="12ba0-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="12ba0-111">UShort 数据类型</span><span class="sxs-lookup"><span data-stu-id="12ba0-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="12ba0-112">默认情况下，此消息是一个警告。</span><span class="sxs-lookup"><span data-stu-id="12ba0-112">By default, this message is a warning.</span></span> <span data-ttu-id="12ba0-113">有关隐藏警告或将警告视为错误的详细信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="12ba0-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="12ba0-114">**错误 ID：** BC40032</span><span class="sxs-lookup"><span data-stu-id="12ba0-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12ba0-115">更正此错误</span><span class="sxs-lookup"><span data-stu-id="12ba0-115">To correct this error</span></span>  
  
- <span data-ttu-id="12ba0-116">如果你的组件只与其他 .NET Framework 组件交互，或者不与任何其他组件进行交互，则无需更改任何内容。</span><span class="sxs-lookup"><span data-stu-id="12ba0-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="12ba0-117">如果与不是为 .NET Framework 编写的组件进行交互，则可以通过反射或文档来确定它是否支持此数据类型。</span><span class="sxs-lookup"><span data-stu-id="12ba0-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="12ba0-118">如果是这样，则无需更改任何内容。</span><span class="sxs-lookup"><span data-stu-id="12ba0-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="12ba0-119">如果与不支持此数据类型的组件进行交互，则必须将其替换为最接近的符合 CLS 的类型。</span><span class="sxs-lookup"><span data-stu-id="12ba0-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="12ba0-120">例如，如果不需要 2147483647 以上的数值范围，可以使用 `UInteger` 取代 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="12ba0-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="12ba0-121">如果确实需要更大范围，可以用 `UInteger` 代替 `Long`。</span><span class="sxs-lookup"><span data-stu-id="12ba0-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="12ba0-122">如果要与自动化或 COM 对象进行交互，请记住，某些类型的数据宽度与 .NET Framework 中的不同。</span><span class="sxs-lookup"><span data-stu-id="12ba0-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="12ba0-123">例如，`uint` 在其他环境中通常为 16 位。</span><span class="sxs-lookup"><span data-stu-id="12ba0-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="12ba0-124">如果要将16位参数传递给此类组件，请 `UShort` `UInteger` 在托管的 Visual Basic 代码中将其声明为而不是。</span><span class="sxs-lookup"><span data-stu-id="12ba0-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ba0-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12ba0-125">See also</span></span>

- [<span data-ttu-id="12ba0-126">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12ba0-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="12ba0-127">反射</span><span class="sxs-lookup"><span data-stu-id="12ba0-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
