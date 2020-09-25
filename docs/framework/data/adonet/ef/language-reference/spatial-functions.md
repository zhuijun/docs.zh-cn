---
title: 空间函数
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7d0979b5166c847244cbeec97acf4fa4f745a259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169578"
---
# <a name="spatial-functions"></a><span data-ttu-id="bced7-102">空间函数</span><span class="sxs-lookup"><span data-stu-id="bced7-102">Spatial Functions</span></span>

<span data-ttu-id="bced7-103">空间类型没有文本格式。</span><span class="sxs-lookup"><span data-stu-id="bced7-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="bced7-104">但是，您可以使用规范实体实体框架函数，这些函数可使用已知文本格式的字符串来调用。</span><span class="sxs-lookup"><span data-stu-id="bced7-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="bced7-105">例如，以下函数调用会生成一个几何点：</span><span class="sxs-lookup"><span data-stu-id="bced7-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="bced7-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>方法具有所有空间规范实体框架方法。</span><span class="sxs-lookup"><span data-stu-id="bced7-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="bced7-107">请单击相关方法以查看应向函数传递哪些参数。</span><span class="sxs-lookup"><span data-stu-id="bced7-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
