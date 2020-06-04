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
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="070a1-102">XML 注释异常必须具有“cref”特性</span><span class="sxs-lookup"><span data-stu-id="070a1-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="070a1-103">\<exception>标记提供了一种方法来记录可由方法引发的异常。</span><span class="sxs-lookup"><span data-stu-id="070a1-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="070a1-104">必需的 `cref` 属性指定由文档生成器检查的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="070a1-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="070a1-105">如果该成员存在，则将其转换为文档文件中的规范元素名称。</span><span class="sxs-lookup"><span data-stu-id="070a1-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="070a1-106">**错误 ID：** BC42319</span><span class="sxs-lookup"><span data-stu-id="070a1-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="070a1-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="070a1-107">To correct this error</span></span>

<span data-ttu-id="070a1-108">将 `cref` 属性添加到异常，如下所示：</span><span class="sxs-lookup"><span data-stu-id="070a1-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="070a1-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="070a1-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="070a1-110">如何：创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="070a1-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="070a1-111">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="070a1-111">XML Comment Tags</span></span>](../xmldoc/index.md)
