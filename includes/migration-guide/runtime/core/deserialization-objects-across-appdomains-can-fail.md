---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619831"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>跨应用域的对象的反序列化可能失败

#### <a name="details"></a>详细信息

在某些情况下，当应用使用两个或更多带有不同应用程序基的应用域时，尝试跨应用域在逻辑调用上下文中为对象反序列化将引发异常。

#### <a name="suggestion"></a>建议

请参阅[缓解措施：跨应用域的对象反序列化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5.1|
|类型|运行时|
