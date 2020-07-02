---
title: 扩展方法
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 55e6a816bbec401fdb061a3394635378b2f37424
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621595"
---
# <a name="extension-methods"></a>扩展方法
扩展方法是一项语言功能，允许使用实例方法调用语法来调用静态方法。 这些方法必须至少采用一个参数，该参数表示方法要操作的实例。

 定义此类扩展方法的类称为 "发起方" 类，并且必须声明为静态。 若要使用扩展方法，必须导入用于定义主办方类的命名空间。

 ❌避免 frivolously 定义扩展方法，特别是对于不属于您的类型。

 如果你有自己的源代码，请考虑改用正则实例方法。 如果不是，并且想要添加方法，请务必小心。 使用扩展方法可能会打乱未设计为具有这些方法的类型的 Api。

 ✔️考虑在以下任何情况下使用扩展方法：

- 若要提供与接口的每个实现相关的帮助器功能，如果可以使用核心接口编写所述的功能。 这是因为不能以其他方式将具体实现分配给接口。 例如， `LINQ to Objects` 运算符实现为所有类型的扩展方法 <xref:System.Collections.Generic.IEnumerable%601> 。 因此，任何 `IEnumerable<>` 实现都会自动启用 LINQ。

- 当实例方法会引入某个类型的依赖项时，但此类依赖项会破坏依赖项管理规则。 例如，从到的依赖 <xref:System.String> 项 <xref:System.Uri?displayProperty=nameWithType> 可能不是必需的，因此， `String.ToUri()` `System.Uri` 从依赖项管理的角度来看，返回的实例方法将是错误的设计。 静态扩展方法 `Uri.ToUri(this string str)` 返回 `System.Uri` 的设计是一个更好的设计。

 ❌避免在上定义扩展方法 <xref:System.Object?displayProperty=nameWithType> 。

 VB 用户将无法使用扩展方法语法对对象引用调用此类方法。 VB 不支持调用此类方法，因为在 VB 中，将引用声明为对象将强制其上的所有方法调用都是后期绑定的（调用的实际成员是在运行时确定的），而扩展方法的绑定是在编译时（早期绑定）确定的。

 请注意，本指南适用于存在相同绑定行为的其他语言，或者不支持扩展方法的其他语言。

 ❌不要将扩展方法放在与扩展类型相同的命名空间中，除非它用于向接口添加方法或用于依赖项管理。

 ❌避免定义具有相同签名的两个或多个扩展方法，即使它们驻留在不同的命名空间中。

 如果类型是一个接口，则✔️考虑在与扩展类型相同的命名空间中定义扩展方法，并且在大多数或所有情况下都使用扩展方法。

 ❌不要定义实现通常与其他功能关联的命名空间中的功能的扩展方法。 而应在与它们所属的功能关联的命名空间中进行定义。

 ❌避免命名空间专用于扩展方法（例如 "Extension"）的命名空间。 请改用描述性名称（例如，"路由"）。

 *部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>请参阅

- [成员设计准则](member.md)
- [框架设计准则](index.md)
