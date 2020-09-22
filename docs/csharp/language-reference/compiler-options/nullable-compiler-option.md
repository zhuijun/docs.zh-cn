---
description: -nullable（C# 编译器选项）
title: -nullable（C# 编译器选项）
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125041"
---
# <a name="-nullable-c-compiler-options"></a>-nullable（C# 编译器选项）

使用 -nullable 选项可指定所需的可为空上下文。

## <a name="syntax"></a>语法

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>自变量

`+` &#124; `-`  
指定 `+` 或仅指定 -nullable 会使编译器启用可为空的上下文。 指定 `-`（等效于未指定 -nullable）会禁用可为空的上下文。

`enable` &#124；`disable` &#124；`warnings` &#124；`annotations`  
指定可为空上下文选项。 与 `+` 或 `-` 类似，若要启用和禁用，只需允许更细粒度的可为空上下文特异性。 `enable` 参数（等效于指定 -nullable）会启用可为空的上下文。 指定 `disable` 将禁用可为空上下文。 如果提供 `warnings` 参数 -nullable:warnings，则将启用可为空警告上下文。 如果指定 `annotations` 参数 -nullable:annotations，则将启用可为空注释上下文。

## <a name="remarks"></a>备注

流分析用于在可执行代码中推断变量的为空性。 推断出的变量的为空性与变量声明的为空性无关。 即使有条件地省略方法调用，也会对其进行分析。 例如，发布模式下的 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。

采用以下特性进行注释的方法调用也将影响流分析：

- 简单的前提条件：<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- 简单的后置条件：<xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- 有条件后置条件：<xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>（例如 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 的 `DoesNotReturnIf(false)`）和 <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- 成员后置条件：<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和 <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>在项目中设置此编译器选项

编辑 .csproj 文件，将 `<Nullable>` 标记添加到 `Project/PropertyGroup` 层次结构中：

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>请参阅

- [C# 编译器选项](./index.md)
- [可为空引用类型](../../nullable-references.md)
