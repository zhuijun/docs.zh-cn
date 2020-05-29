---
title: 全球化中断性变更
description: 列出 .NET Core 中全球化过程内的中断性变更。
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702283"
---
# <a name="globalization-breaking-changes"></a>全球化中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | :-: |
| [全球化 API 在 Windows 上使用 ICU 库](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [StringInfo 和 TextElementEnumerator 现在与 UAX29 兼容](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| [“C”区域设置映射到固定区域设置](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
