---
title: “<interfacename>.<membername>”已经由基类“<baseclassname>”实现。 假定重新实现 <type>
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 6525ae08b90cc530a8f6a469d35d9ab8c27fb5e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402819"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="d62f5-103">“\<interfacename>.\<membername>”已经由基类“\<baseclassname>”实现。</span><span class="sxs-lookup"><span data-stu-id="d62f5-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="d62f5-104">假定重新实现 \<type></span><span class="sxs-lookup"><span data-stu-id="d62f5-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="d62f5-105">派生类中的属性、过程或事件使用子句，用于 `Implements` 指定已在基类中实现的接口成员。</span><span class="sxs-lookup"><span data-stu-id="d62f5-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="d62f5-106">派生类可以重新实现由其基类实现的接口成员。</span><span class="sxs-lookup"><span data-stu-id="d62f5-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="d62f5-107">这与重写基类实现不同。</span><span class="sxs-lookup"><span data-stu-id="d62f5-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="d62f5-108">有关详细信息，请参阅 [Implements](../statements/implements-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="d62f5-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="d62f5-109">默认情况下，此消息是一个警告。</span><span class="sxs-lookup"><span data-stu-id="d62f5-109">By default, this message is a warning.</span></span> <span data-ttu-id="d62f5-110">有关隐藏警告或将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="d62f5-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d62f5-111">**错误 ID：** BC42015</span><span class="sxs-lookup"><span data-stu-id="d62f5-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d62f5-112">更正此错误</span><span class="sxs-lookup"><span data-stu-id="d62f5-112">To correct this error</span></span>  
  
- <span data-ttu-id="d62f5-113">如果要重新实现接口成员，则无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d62f5-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="d62f5-114">派生类中的代码访问重新实现成员，除非使用 `MyBase` 关键字访问基类实现。</span><span class="sxs-lookup"><span data-stu-id="d62f5-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="d62f5-115">如果不打算重新实现接口成员，请从属性、过程或事件声明中删除 `Implements` 子句。</span><span class="sxs-lookup"><span data-stu-id="d62f5-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62f5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d62f5-116">See also</span></span>

- [<span data-ttu-id="d62f5-117">接口</span><span class="sxs-lookup"><span data-stu-id="d62f5-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
