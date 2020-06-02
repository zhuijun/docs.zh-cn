---
title: 接口设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: f589d47d5b945179430275598996b2fb77e92848
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289026"
---
# <a name="interface-design"></a>接口设计
尽管大多数 Api 是使用类和结构进行最佳建模的，但在某些情况下，接口更合适，或者是唯一的选择。

 CLR 不支持多重继承（即，CLR 类不能从多个基类继承），但它允许类型实现一个或多个接口，还可以从基类继承。 因此，接口通常用于实现多重继承的效果。 例如， <xref:System.IDisposable> 是一个接口，该接口允许类型独立于要参与的任何其他继承层次结构来支持 disposability。

 定义接口的另一种情况是在创建可由多种类型（包括某些值类型）支持的公共接口。 值类型不能从的类型继承 <xref:System.ValueType> ，但它们可以实现接口，因此，使用接口是提供公共基类型的唯一选项。

 如果需要某些包含值类型的类型集支持某些常见 API，✔️确实要定义接口。

 ✔️如果需要在已从其他类型继承的类型上支持其功能，请考虑定义接口。

 ❌避免使用标记接口（没有成员的接口）。

 如果需要将类标记为具有特定的特性（标记），通常使用自定义特性而不是接口。

 ✔️提供至少一种类型作为接口的实现。

 这样做有助于验证界面的设计。 例如， <xref:System.Collections.Generic.List%601> 是接口的实现 <xref:System.Collections.Generic.IList%601> 。

 ✔️提供至少一个使用你定义的每个接口的 API （将接口用作参数的方法或类型化为接口的属性）。

 这样做有助于验证接口设计。 例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 使用 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 接口。

 ❌不要将成员添加到之前已发货的接口。

 这样做会中断接口的实现。 应创建新的接口，以避免版本控制问题。

 除了这些准则中描述的情况外，一般还应选择 "类"，而不是在设计托管代码可重用库中选择 "接口"。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [类型设计准则](type.md)
- [框架设计准则](index.md)
