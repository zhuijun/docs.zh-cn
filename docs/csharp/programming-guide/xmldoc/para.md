---
title: <para> - C# 编程指南
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: d1fe81b1752d066c6b2e1ffe27f0c43fc4068edf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287293"
---
# <a name="para-c-programming-guide"></a>\<para>（C# 编程指南）

## <a name="syntax"></a>语法

```xml
<para>content</para>
```

## <a name="parameters"></a>参数

- `content`

  段落文本。

## <a name="remarks"></a>备注

`<para>` 标记用于标记内，例如 [\<summary>](./summary.md)、[\<remarks>](./remarks.md) 或 [\<returns>](./returns.md)，允许向文本添加结构。

使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。

## <a name="example"></a>示例

有关使用 `<para>` 的示例，请参阅 [\<summary>](./summary.md)。

## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [建议的文档注释标记](./recommended-tags-for-documentation-comments.md)
