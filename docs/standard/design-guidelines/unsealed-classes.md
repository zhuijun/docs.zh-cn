---
title: 未密封类
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 8e332a6382cf644c82d5e26cf5234cea08dcc693
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289546"
---
# <a name="unsealed-classes"></a>未密封类
密封类不能从继承，它们会阻止可扩展性。 相反，可以从继承的类称为非密封类。

 ✔️考虑使用未密封的类，而不添加虚拟成员或受保护成员，这是为框架提供廉价但非常感谢的扩展性的极佳方式。

 开发人员通常需要从未密封的类中继承，以便添加便利成员，如自定义构造函数、新方法或方法重载。 例如， `System.Messaging.MessageQueue` 是未密封的，因此允许用户创建默认为特定队列路径的自定义队列，或者添加自定义方法来简化特定方案的 API。

 默认情况下，大多数编程语言中都不密封类，这也是框架中大多数类的建议默认值。 由于与未密封的类型相关的测试成本相对较低，因此框架用户非常感谢非密封类型提供的扩展性，并且提供的扩展成本要高得多。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [框架设计准则](index.md)
- [扩展性设计](designing-for-extensibility.md)
- [密封](sealing.md)
