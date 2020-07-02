---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619846"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a>Sql_variant 数据使用 sql_variant 排序规则而不是数据库排序规则

#### <a name="details"></a>详细信息

<code>sql_variant</code> 数据使用 <code>sql_variant</code> 排序规则而不是数据库排序规则。

#### <a name="suggestion"></a>建议

如果数据库排序规则与 <code>sql_variant</code> 排序规则不同，则此更改将解决可能的数据损坏。 依赖损坏的数据的应用程序可能会失败。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |透明|
|Version|4.5|
|类型|运行时|
