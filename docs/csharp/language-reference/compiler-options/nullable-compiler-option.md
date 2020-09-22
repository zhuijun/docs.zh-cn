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
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="ddf42-103">-nullable（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="ddf42-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="ddf42-104">使用 -nullable 选项可指定所需的可为空上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-104">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="ddf42-105">语法</span><span class="sxs-lookup"><span data-stu-id="ddf42-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="ddf42-106">自变量</span><span class="sxs-lookup"><span data-stu-id="ddf42-106">Arguments</span></span>

<span data-ttu-id="ddf42-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ddf42-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="ddf42-108">指定 `+` 或仅指定 -nullable 会使编译器启用可为空的上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-108">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="ddf42-109">指定 `-`（等效于未指定 -nullable）会禁用可为空的上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-109">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="ddf42-110">`enable` &#124；`disable` &#124；`warnings` &#124；`annotations`</span><span class="sxs-lookup"><span data-stu-id="ddf42-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="ddf42-111">指定可为空上下文选项。</span><span class="sxs-lookup"><span data-stu-id="ddf42-111">Specifies the nullable context option.</span></span> <span data-ttu-id="ddf42-112">与 `+` 或 `-` 类似，若要启用和禁用，只需允许更细粒度的可为空上下文特异性。</span><span class="sxs-lookup"><span data-stu-id="ddf42-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="ddf42-113">`enable` 参数（等效于指定 -nullable）会启用可为空的上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="ddf42-114">指定 `disable` 将禁用可为空上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="ddf42-115">如果提供 `warnings` 参数 -nullable:warnings，则将启用可为空警告上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="ddf42-116">如果指定 `annotations` 参数 -nullable:annotations，则将启用可为空注释上下文。</span><span class="sxs-lookup"><span data-stu-id="ddf42-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="ddf42-117">备注</span><span class="sxs-lookup"><span data-stu-id="ddf42-117">Remarks</span></span>

<span data-ttu-id="ddf42-118">流分析用于在可执行代码中推断变量的为空性。</span><span class="sxs-lookup"><span data-stu-id="ddf42-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="ddf42-119">推断出的变量的为空性与变量声明的为空性无关。</span><span class="sxs-lookup"><span data-stu-id="ddf42-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="ddf42-120">即使有条件地省略方法调用，也会对其进行分析。</span><span class="sxs-lookup"><span data-stu-id="ddf42-120">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="ddf42-121">例如，发布模式下的 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ddf42-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="ddf42-122">采用以下特性进行注释的方法调用也将影响流分析：</span><span class="sxs-lookup"><span data-stu-id="ddf42-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="ddf42-123">简单的前提条件：<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="ddf42-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="ddf42-124">简单的后置条件：<xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="ddf42-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="ddf42-125">有条件后置条件：<xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="ddf42-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="ddf42-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>（例如 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 的 `DoesNotReturnIf(false)`）和 <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="ddf42-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="ddf42-127">成员后置条件：<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和 <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="ddf42-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="ddf42-128">在项目中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="ddf42-128">To set this compiler option in a project</span></span>

<span data-ttu-id="ddf42-129">编辑 .csproj 文件，将 `<Nullable>` 标记添加到 `Project/PropertyGroup` 层次结构中：</span><span class="sxs-lookup"><span data-stu-id="ddf42-129">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="ddf42-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="ddf42-130">See also</span></span>

- [<span data-ttu-id="ddf42-131">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="ddf42-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ddf42-132">可为空引用类型</span><span class="sxs-lookup"><span data-stu-id="ddf42-132">Nullable reference types</span></span>](../../nullable-references.md)
