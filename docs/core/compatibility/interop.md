---
title: 互操作中断性变更
description: 列出 .NET Core 和 .NET 5.0 及更高版本中互操作的中断性变更。
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438032"
---
# <a name="interop-breaking-changes"></a>互操作中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | :-: |
| [将 RCW 强制转换为 `InterfaceIsIInspectable` 接口会引发 PlatformNotSupportedException](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | 5.0 |
| [不在非 Windows 平台上探测 A/W 后缀](#no-aw-suffix-probing-on-non-windows-platforms) | 5.0 |
| [已从 .NET 中删除对 WinRT 的内置支持](#built-in-support-for-winrt-is-removed-from-net) | 5.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
