---
title: 数组
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 30277507050091de6b1e9293401d61ac5e351a1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280603"
---
# <a name="arrays"></a>数组
✔️确实更喜欢在公共 Api 中对数组使用集合。 "[集合](guidelines-for-collections.md)" 部分提供了有关如何在集合和数组之间进行选择的详细信息。

 ❌不要使用只读数组字段。 字段本身是只读的并且不能更改，但可以更改数组中的元素。

 ✔️考虑使用交错数组而不是多维数组。

 交错数组是具有同样数组的元素的数组。 构成元素的数组可以是不同大小的，因此，与多维数组相比，某些数据集（例如稀疏矩阵）的浪费空间越少。 此外，CLR 还会优化交错数组的索引操作，因此，在某些情况下，它们可能会表现出更好的运行时性能。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- <xref:System.Array>
- [框架设计准则](index.md)
- [使用准则](usage-guidelines.md)
