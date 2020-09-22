---
title: 默认属性“<propertyname1>”与“<propertyname2>”中的默认属性“<classname>”冲突，因此应声明为“Shadows”
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b857a9ae7875a156179602cbe77558333d07b7b9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874516"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="847d3-102">默认属性“\<propertyname1>”与“\<propertyname2>”中的默认属性“\<classname>”冲突，因此应声明为“Shadows”</span><span class="sxs-lookup"><span data-stu-id="847d3-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>

<span data-ttu-id="847d3-103">使用与基类中定义的属性相同的名称声明属性。</span><span class="sxs-lookup"><span data-stu-id="847d3-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="847d3-104">在这种情况下，此类中的属性应隐藏基类属性。</span><span class="sxs-lookup"><span data-stu-id="847d3-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="847d3-105">此消息是一个警告。</span><span class="sxs-lookup"><span data-stu-id="847d3-105">This message is a warning.</span></span> <span data-ttu-id="847d3-106">默认假定`Shadows` 。</span><span class="sxs-lookup"><span data-stu-id="847d3-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="847d3-107">有关隐藏警告或将警告视为错误的详细信息，请参阅 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="847d3-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="847d3-108">**错误 ID：** BC40007</span><span class="sxs-lookup"><span data-stu-id="847d3-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="847d3-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="847d3-109">To correct this error</span></span>  
  
- <span data-ttu-id="847d3-110">将 `Shadows` 关键字添加到声明中，或更改所声明的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="847d3-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847d3-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="847d3-111">See also</span></span>

- [<span data-ttu-id="847d3-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="847d3-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="847d3-113">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="847d3-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
