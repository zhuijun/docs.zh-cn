---
title: 类型 <typename> 不符合 CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386953"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="4f1b9-102">类型 \<typename> 不符合 CLS</span><span class="sxs-lookup"><span data-stu-id="4f1b9-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="4f1b9-103">使用不符合 CLS 的数据类型声明了变量、属性或函数返回。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="4f1b9-104">为了使应用程序符合[语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md)（CLS），该应用程序必须只使用符合 CLS 的类型。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="4f1b9-105">以下 Visual Basic 数据类型不符合 CLS：</span><span class="sxs-lookup"><span data-stu-id="4f1b9-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="4f1b9-106">SByte 数据类型</span><span class="sxs-lookup"><span data-stu-id="4f1b9-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="4f1b9-107">UInteger 数据类型</span><span class="sxs-lookup"><span data-stu-id="4f1b9-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="4f1b9-108">ULong 数据类型</span><span class="sxs-lookup"><span data-stu-id="4f1b9-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="4f1b9-109">UShort 数据类型</span><span class="sxs-lookup"><span data-stu-id="4f1b9-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="4f1b9-110">**错误 ID：** BC40041</span><span class="sxs-lookup"><span data-stu-id="4f1b9-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f1b9-111">更正此错误</span><span class="sxs-lookup"><span data-stu-id="4f1b9-111">To correct this error</span></span>  
  
- <span data-ttu-id="4f1b9-112">如果你的应用程序需要符合 CLS，请将此元素的数据类型更改为最接近的符合 CLS 的类型。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="4f1b9-113">例如，如果不需要 2147483647 以上的数值范围，可以使用 `UInteger` 取代 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="4f1b9-114">如果确实需要更大范围，可以用 `UInteger` 代替 `Long`。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="4f1b9-115">如果你的应用程序不需要符合 CLS，则无需更改任何内容。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="4f1b9-116">不过，您应该知道其不相容性。</span><span class="sxs-lookup"><span data-stu-id="4f1b9-116">You should be aware of its noncompliance, however.</span></span>
