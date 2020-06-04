---
title: XML 注释异常必须具有“cref”特性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406503"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML 注释异常必须具有“cref”特性

\<exception>标记提供了一种方法来记录可由方法引发的异常。 必需的 `cref` 属性指定由文档生成器检查的成员的名称。 如果该成员存在，则将其转换为文档文件中的规范元素名称。

**错误 ID：** BC42319

## <a name="to-correct-this-error"></a>更正此错误

将 `cref` 属性添加到异常，如下所示：

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>另请参阅

- [\<exception>](../xmldoc/exception.md)
- [如何：创建 XML 文档](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML 注释标记](../xmldoc/index.md)
