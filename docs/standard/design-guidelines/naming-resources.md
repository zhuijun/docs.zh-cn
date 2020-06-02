---
title: 命名资源
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 762ba99c4751ba40f5f33e99455cf950af35cdf6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290144"
---
# <a name="naming-resources"></a>命名资源
由于可以通过某些对象来引用可本地化的资源，就像它们是属性一样，因此资源的命名准则与属性准则类似。

 ✔️在资源键中使用 PascalCasing。

 ✔️提供描述性而不是短标识符。

 ❌不要使用主要 CLR 语言的特定于语言的关键字。

 ✔️在命名资源中仅使用字母数字字符和下划线。

 ✔️对异常消息资源使用以下命名约定。

 资源标识符应为异常类型名称和异常的简短标识符：

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [框架设计准则](index.md)
- [命名准则](naming-guidelines.md)
