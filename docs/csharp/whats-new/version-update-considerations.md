---
title: 面向 C# 开发人员的版本和更新注意事项
description: 在库中引入新语言功能可能会影响使用它的代码。
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: 6de0e3ba33af34edba73819dcb9268f40f8a5ea4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552422"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="60649-103">面向 C# 开发人员的版本和更新注意事项</span><span class="sxs-lookup"><span data-stu-id="60649-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="60649-104">兼容性是一个非常重要的目标，因为新功能已添加到 C# 语言中。</span><span class="sxs-lookup"><span data-stu-id="60649-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="60649-105">在几乎所有情况下，都可以使用新的编译器版本重新编译现有代码，不会出现任何问题。</span><span class="sxs-lookup"><span data-stu-id="60649-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="60649-106">在库中采用新语言功能时，可能需要多加注意。</span><span class="sxs-lookup"><span data-stu-id="60649-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="60649-107">你可能要使用最新版本中提供的功能创建一个新库，并且需要确保使用以前版本的编译器生成的应用可以使用它。</span><span class="sxs-lookup"><span data-stu-id="60649-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="60649-108">或者，你可能要升级现有库，但许多用户可能还没有升级版本。</span><span class="sxs-lookup"><span data-stu-id="60649-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="60649-109">在决定采用新功能时，需要考虑两种兼容性：源兼容和二进制兼容。</span><span class="sxs-lookup"><span data-stu-id="60649-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="60649-110">二进制兼容的更改</span><span class="sxs-lookup"><span data-stu-id="60649-110">Binary compatible changes</span></span>

<span data-ttu-id="60649-111">如果更新的库可以在不重新生成应用程序和使用它的库的情况下使用，那么对库的更改属于二进制兼容  的更改。</span><span class="sxs-lookup"><span data-stu-id="60649-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="60649-112">不需要重新生成从属程序集，也不需要更改任何源代码。</span><span class="sxs-lookup"><span data-stu-id="60649-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="60649-113">二进制兼容的更改也是源兼容的更改。</span><span class="sxs-lookup"><span data-stu-id="60649-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="60649-114">源兼容的更改</span><span class="sxs-lookup"><span data-stu-id="60649-114">Source compatible changes</span></span>

<span data-ttu-id="60649-115">如果使用库的应用程序和库不需要更改源代码，但必须根据新版本重新编译源才能正常工作，那么对库的更改属于源兼容  的更改。</span><span class="sxs-lookup"><span data-stu-id="60649-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="60649-116">不兼容的更改</span><span class="sxs-lookup"><span data-stu-id="60649-116">Incompatible changes</span></span>

<span data-ttu-id="60649-117">如果更改既不是源兼容  的更改，也不是二进制兼容  的更改，则需要在从属库和应用程序中进行源代码更改和重新编译。</span><span class="sxs-lookup"><span data-stu-id="60649-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="60649-118">评估库</span><span class="sxs-lookup"><span data-stu-id="60649-118">Evaluate your library</span></span>

<span data-ttu-id="60649-119">这些兼容性概念会影响库的公共声明和受保护声明，而不会影响其内部实现。</span><span class="sxs-lookup"><span data-stu-id="60649-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="60649-120">在内部采用任何新功能始终是二进制兼容  的更改。</span><span class="sxs-lookup"><span data-stu-id="60649-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="60649-121">二进制兼容  的更改提供新语法，可以生成与旧语法相同的公共声明的已编译代码。</span><span class="sxs-lookup"><span data-stu-id="60649-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="60649-122">例如，将方法更改为 expression-bodied 的成员是二进制兼容  的更改：</span><span class="sxs-lookup"><span data-stu-id="60649-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="60649-123">原始代码：</span><span class="sxs-lookup"><span data-stu-id="60649-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="60649-124">新代码：</span><span class="sxs-lookup"><span data-stu-id="60649-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="60649-125"> 源兼容的更改引入了可更改公共成员的已编译代码的语法，只不过是通过与现有调用站点兼容的方式执行。</span><span class="sxs-lookup"><span data-stu-id="60649-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="60649-126">例如，将方法签名从 by 值参数更改为 `in` by 引用参数是源兼容的更改，但不是二进制兼容的更改：</span><span class="sxs-lookup"><span data-stu-id="60649-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="60649-127">原始代码：</span><span class="sxs-lookup"><span data-stu-id="60649-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="60649-128">新代码：</span><span class="sxs-lookup"><span data-stu-id="60649-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="60649-129">[新增功能](./csharp-9.md)一文说明了引入会影响公共声明的功能是源兼容的更改还是二进制兼容的更改。</span><span class="sxs-lookup"><span data-stu-id="60649-129">The [What's new](./csharp-9.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
