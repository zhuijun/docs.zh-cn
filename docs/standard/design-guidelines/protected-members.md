---
title: 受保护的成员
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: afcb92e48996d594fcedc5b579922b179f754b9d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286114"
---
# <a name="protected-members"></a>受保护的成员
受保护的成员不提供任何可扩展性，但它们可以通过创建更强大的子类进行扩展。 它们可用于公开高级自定义项选项，而不会使主公共接口复杂化。

 框架设计人员需要小心处理受保护的成员，因为名称 "protected" 可以提供虚假的安全性理解。 任何人都可以为未密封的类提供子类并访问受保护的成员，因此用于公共成员的所有相同的防御性编码方法都适用于受保护的成员。

 ✔️考虑使用受保护的成员进行高级自定义。

 ✔️将未密封类中的受保护成员视为公共的，目的是为了实现安全、文档和兼容性分析。

 任何人都可以从类继承并访问受保护的成员。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [框架设计准则](index.md)
- [扩展性设计](designing-for-extensibility.md)
