---
title: 使用准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 03eaba3e52cb25619f65637efb4f414c22770440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291339"
---
# <a name="usage-guidelines"></a>使用准则

本部分包含有关在可公开访问的 Api 中使用常见类型的准则。 它处理内置框架类型（如序列化属性）和重载常见运算符的直接使用。
  
<xref:System.IDisposable?displayProperty=nameWithType>此部分未介绍接口，但会在 " [Dispose 模式](../garbage-collection/implementing-dispose.md)" 部分中讨论。

> [!NOTE]
> 有关其他通用内置 .NET Framework 类型的指南和其他信息，请参阅以下主题： <xref:System.DateTime?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset?displayProperty=nameWithType> 、 <xref:System.ICloneable?displayProperty=nameWithType> 、 <xref:System.IComparable%601?displayProperty=nameWithType> 、 <xref:System.IEquatable%601?displayProperty=nameWithType> 、 <xref:System.Nullable%601?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> 、和。

## <a name="in-this-section"></a>本节内容

[数组](arrays.md)  
[特性](attributes.md)  
[集合](guidelines-for-collections.md)  
[序列化](serialization.md)  
[System.web 使用](system-xml-usage.md)  
[相等运算符](equality-operators.md)  

*部分©2005，2009 Microsoft Corporation。保留所有权利。*

*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*
  
## <a name="see-also"></a>另请参阅

- [框架设计准则](index.md)
