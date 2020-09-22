---
title: 未定义 Property Let 过程，并且 Property Get 过程未返回对象
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871091"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="09210-102">未定义 Property Let 过程，并且 Property Get 过程未返回对象</span><span class="sxs-lookup"><span data-stu-id="09210-102">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="09210-103">某些属性、方法和操作只能应用于 `Collection` 对象。</span><span class="sxs-lookup"><span data-stu-id="09210-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="09210-104">指定的操作或属性专用于集合，但该对象不是集合。</span><span class="sxs-lookup"><span data-stu-id="09210-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09210-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="09210-105">To correct this error</span></span>  
  
1. <span data-ttu-id="09210-106">检查对象或属性名称的拼写，或验证对象是否为 `Collection` 对象。</span><span class="sxs-lookup"><span data-stu-id="09210-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="09210-107">查看 `Add` 用于将对象添加到集合的方法，以确保语法正确，并且所有标识符拼写正确。</span><span class="sxs-lookup"><span data-stu-id="09210-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09210-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09210-108">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
