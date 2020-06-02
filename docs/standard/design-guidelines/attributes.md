---
title: 特性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 12a67d75a5f9642408cca69b2e3764a67f101549
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280577"
---
# <a name="attributes"></a>特性

<xref:System.Attribute?displayProperty=nameWithType>用于定义自定义属性的基类。

 特性是可以添加到编程元素（如程序集、类型、成员和参数）的批注。 它们存储在程序集的元数据中，并且可在运行时使用反射 Api 进行访问。 例如，.NET 定义 <xref:System.ObsoleteAttribute> 属性，该属性可应用于类型或成员，以指示类型或成员已弃用。

 特性可以具有一个或多个属性，这些属性包含与特性相关的其他数据。 例如， `ObsoleteAttribute` 可能会携带有关已弃用类型或成员的发布的附加信息，以及替换已过时 api 的新 api 的说明。

 应用特性时，必须指定特性的某些属性。 它们被称为必需的属性或必需的参数，因为它们表示为位置构造函数参数。 例如， <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 的属性 <xref:System.Diagnostics.ConditionalAttribute> 是必需的属性。

 应用特性时不一定要指定的属性称为可选属性（或可选参数）。 它们由可设置的属性表示。 应用特性时，编译器提供了用于设置这些属性的特殊语法。 例如， <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 属性表示可选参数。

 ✔️命名具有后缀 "Attribute" 的自定义属性类。

 ✔️将应用 <xref:System.AttributeUsageAttribute> 到自定义属性。

 ✔️提供可选参数的可设置属性。

 ✔️确实提供必需参数的只需属性。

 ✔️提供构造函数参数来初始化对应于所需参数的属性。 每个参数都应具有与相应属性相同的名称（但大小写不同）。

 ❌避免提供构造函数参数来初始化对应于可选参数的属性。

 换句话说，不能使用构造函数和 setter 来设置属性。 此准则非常明确，哪些参数是可选的，哪些是必需的，并且避免了两种方法来执行相同的操作。

 ❌避免重载自定义特性构造函数。

 只有一个构造函数清楚地向用户传达需要哪些参数，哪些参数是可选的。

 如果可能，✔️确实密封自定义特性类。 这样可以更快地查找属性。

 *部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [框架设计准则](index.md)
- [使用准则](usage-guidelines.md)
