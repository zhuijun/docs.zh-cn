---
title: 通用命名约定
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: c90987fd28d5157cfb7f7eea4680b5ab4be1a200
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290949"
---
# <a name="general-naming-conventions"></a>通用命名约定

本部分介绍与 word 选项相关的常规命名约定、有关使用缩写和首字母缩写词的准则，以及如何避免使用特定于语言的名称的建议。

## <a name="word-choice"></a>Word 选项
 ✔️选择易于阅读的标识符名称。

 例如，名为的属性的 `HorizontalAlignment` 可读性比更强 `AlignmentHorizontal` 。

 ✔️提高可读性比简洁。

 属性名称 `CanScrollHorizontally` 比 `ScrollableX` （对 X 轴的模糊引用）更好。

 ❌不要使用下划线、连字符或任何其他非字母数字字符。

 ❌不要使用匈牙利表示法。

 ❌避免使用与广泛使用的编程语言的关键字冲突的标识符。

 根据公共语言规范（CLS）的规则4，所有符合语言都必须提供一种机制，以允许访问使用该语言的关键字作为标识符的已命名项。 例如，在这种情况下，c # 使用 @ 符号作为转义机制。 不过，最好是避免使用常见关键字，因为使用转义序列的方法比没有它的方法更难。

## <a name="using-abbreviations-and-acronyms"></a>使用缩写和首字母缩写
 ❌不要使用缩写或缩写作为标识符名称的一部分。

 例如，使用 `GetWindow` 而不是 `GetWin` 。

 ❌不要使用未被广泛接受的任何首字母缩写，甚至在必要时才使用。

## <a name="avoiding-language-specific-names"></a>避免特定于语言的名称
 ✔️确实使用有语义的名称，而不是类型名称的特定于语言的关键字。

 例如， `GetLength` 是比更好的名称 `GetInt` 。

 在极少数情况下，如果标识符没有超出其类型的语义含义，则✔️使用泛型 CLR 类型名称，而不是特定于语言的名称。

 例如，转换为的方法 <xref:System.Int64> 应命名为 `ToInt64` ，而不是 `ToLong` （因为 <xref:System.Int64> 是特定于 c # 的别名的 CLR 名称 `long` ）。 下表显示了几种使用 CLR 类型名称的基本数据类型（以及 c #、Visual Basic 和 c + + 的相应类型名称）。

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|sbyte|**SByte**|**char**|**SByte**|
|byte|**Byte**|**unsigned char**|**Byte**|
|**short**|**短暂**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**整数**|**int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Long**|**__int64**|**Int64**|
|**ulong**|**UInt64**|unsigned __int64 |**UInt64**|
|**float**|**单精度**|**float**|**单精度**|
|**double**|**双精度**|**double**|**双精度**|
|**bool**|**布尔值**|**bool**|**布尔值**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**字符串**|**字符串**|**字符串**|
|对象|**Object**|**Object**|**Object**|

 ✔️使用公用名（如 `value` 或 `item` ），而不是重复类型名称，在极少数情况下，标识符没有语义含义，并且参数的类型并不重要。

## <a name="naming-new-versions-of-existing-apis"></a>命名现有 Api 的新版本
 创建现有 API 的新版本时，✔️使用类似于旧 API 的名称。

 这有助于突出显示 Api 之间的关系。

 ✔️确实更喜欢添加后缀（而非前缀）来指示现有 API 的新版本。

 这将有助于在浏览文档或使用 IntelliSense 时发现。 旧版本的 API 将被组织到新的 Api 附近，因为大多数浏览器和 IntelliSense 都按字母顺序显示标识符。

 ✔️考虑使用全新但有意义的标识符，而不是添加后缀或前缀。

 ✔️使用数字后缀来指示现有 API 的新版本，尤其当 API 的现有名称是有意义的唯一名称（即，如果它是行业标准），并且如果添加任何有意义的后缀（或更改名称）不是合适的选项。

 ❌不要使用标识符的 "Ex" （或类似的）后缀来区分它与早期版本的同一 API。

 当引入对64位整数（长整数）而不是32位整数运行的 Api 版本时，✔️确实使用 "64" 后缀。 仅当存在现有的32位 API 时，才需要采用此方法;请勿使用只有64位版本的新 Api。

 *部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*

 *皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*

## <a name="see-also"></a>另请参阅

- [框架设计准则](index.md)
- [命名准则](naming-guidelines.md)
- [EditorConfig 适用的 .NET 命名约定](/visualstudio/ide/editorconfig-naming-conventions)
