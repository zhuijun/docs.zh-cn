---
title: 静态类设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: c906502ed071e8515f101996ec42a04772f72b12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291924"
---
# <a name="static-class-design"></a>静态类设计
静态类定义为仅包含静态成员的类（当然，除了从继承的实例成员 <xref:System.Object?displayProperty=nameWithType> ，还可能是私有构造函数）。 某些语言为静态类提供内置支持。 在 c # 2.0 和更高版本中，将类声明为静态时，它是密封的、抽象的，并且不能重写或声明任何实例成员。

 静态类在面向对象的纯设计和简单性之间是一种折衷方案。 它们通常用于提供对其他操作（例如）的快捷方式 <xref:System.IO.File?displayProperty=nameWithType> 、扩展方法的持有者或为其有人完全面向对象的包装器的功能（如 <xref:System.Environment?displayProperty=nameWithType> ）。

 ✔️尽量少使用静态类。

 静态类只应用作框架的面向对象核心的支持类。

 ❌不要将静态类视为其他存储桶。

 ❌不要在静态类中声明或重写实例成员。

 如果你的编程语言没有对静态类的内置支持，✔️会将静态类声明为密封、抽象并添加私有实例构造函数。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [类型设计准则](type.md)
- [框架设计准则](index.md)
