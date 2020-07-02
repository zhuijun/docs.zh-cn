---
title: 兼容性
description: 了解代码更改如何影响 .NET 中的兼容性。
ms.date: 06/10/2019
ms.openlocfilehash: 1cf14b7ff4143367653bd1c305cc1dda6711f980
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415688"
---
# <a name="how-code-changes-can-affect-compatibility"></a><span data-ttu-id="b13a6-103">代码更改如何影响兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-103">How code changes can affect compatibility</span></span>

<span data-ttu-id="b13a6-104">兼容性是指在 .NET 实现版本（而不是最初开发代码的版本）上编译或执行代码的能力。</span><span class="sxs-lookup"><span data-stu-id="b13a6-104">*Compatibility* refers to the ability to compile or execute code on a version of a .NET implementation other than the one with which the code was originally developed.</span></span> <span data-ttu-id="b13a6-105">[特殊的变更](index.md)可能会以六种不同的方式影响兼容性：</span><span class="sxs-lookup"><span data-stu-id="b13a6-105">A [particular change](index.md) can affect compatibility in six different ways:</span></span>

- [<span data-ttu-id="b13a6-106">行为变更</span><span class="sxs-lookup"><span data-stu-id="b13a6-106">Behavioral change</span></span>](#behavioral-change)
- [<span data-ttu-id="b13a6-107">二进制兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-107">Binary compatibility</span></span>](#binary-compatibility)
- [<span data-ttu-id="b13a6-108">源兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-108">Source compatibility</span></span>](#source-compatibility)
- [<span data-ttu-id="b13a6-109">设计时兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-109">Design-time compatibility</span></span>](#design-time-compatibility)
- [<span data-ttu-id="b13a6-110">后向兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-110">Backwards compatibility</span></span>](#backwards-compatibility)
- <span data-ttu-id="b13a6-111">[前向兼容性](#forward-compatibility)（不是 .NET Core 的目标）</span><span class="sxs-lookup"><span data-stu-id="b13a6-111">[Forward compatibility](#forward-compatibility) (not a goal of .NET Core)</span></span>

## <a name="behavioral-change"></a><span data-ttu-id="b13a6-112">行为变更</span><span class="sxs-lookup"><span data-stu-id="b13a6-112">Behavioral change</span></span>

<span data-ttu-id="b13a6-113">行为变更表示对成员行为的更改。</span><span class="sxs-lookup"><span data-stu-id="b13a6-113">A behavioral change represents a change to the behavior of a member.</span></span> <span data-ttu-id="b13a6-114">此更改可能对外部可见（例如一种方法可能引发不同的异常），或者它可能表示一种更改的实现（例如，计算返回值的方式更改、添加或删除内部方法调用，或甚至显著性能改进）。</span><span class="sxs-lookup"><span data-stu-id="b13a6-114">The change may be externally visible (for example, a method may throw a different exception), or it may represent a changed implementation (for example, a change in the way a return value is calculated, the addition or removal of internal method calls, or even a significant performance improvement).</span></span>

<span data-ttu-id="b13a6-115">当行为变更对外部可见并修改类型的公共协定时，由于它们影响二进制兼容性，因此易于评估。</span><span class="sxs-lookup"><span data-stu-id="b13a6-115">When behavioral changes are externally visible and modify a type's public contract, they are easy to evaluate since they affect binary compatibility.</span></span> <span data-ttu-id="b13a6-116">实现更改更难评估；取决于更改的性质以及使用 API 的频率和模式，更改的影响可能从严重到无害。</span><span class="sxs-lookup"><span data-stu-id="b13a6-116">Implementation changes are much more difficult to evaluate; depending on the nature of the change and the frequency and patterns of use of the API, the impact of a change can range from severe to innocuous.</span></span>

## <a name="binary-compatibility"></a><span data-ttu-id="b13a6-117">二进制兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-117">Binary compatibility</span></span>

<span data-ttu-id="b13a6-118">二进制兼容性指的是 API 使用者无需重新编译即可在更新的版本上使用 API。</span><span class="sxs-lookup"><span data-stu-id="b13a6-118">Binary compatibility refers to the ability of a consumer of an API to use the API on a newer version without recompilation.</span></span> <span data-ttu-id="b13a6-119">添加方法或向类型添加新接口实现等此类更改不影响二进制兼容性。</span><span class="sxs-lookup"><span data-stu-id="b13a6-119">Such changes as adding methods or adding a new interface implementation to a type do not affect binary compatibility.</span></span> <span data-ttu-id="b13a6-120">但是，删除或更改程序集的公共签名，以便使用者无法再访问该程序集公开的同一接口，这会影响二进制兼容性。</span><span class="sxs-lookup"><span data-stu-id="b13a6-120">However, removing or altering an assembly's public signatures so that consumers can no longer access the same interface exposed by the assembly does affect binary compatibility.</span></span> <span data-ttu-id="b13a6-121">此类更改称为“二进制不兼容的更改”。</span><span class="sxs-lookup"><span data-stu-id="b13a6-121">A change of this kind is termed a *binary incompatible change*.</span></span>

## <a name="source-compatibility"></a><span data-ttu-id="b13a6-122">源兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-122">Source compatibility</span></span>

<span data-ttu-id="b13a6-123">源兼容性指的是 API 的现有使用者无需进行任何源更改即可根据更新的版本重新编译。</span><span class="sxs-lookup"><span data-stu-id="b13a6-123">Source compatibility refers to the ability of existing consumers of an API to recompile against a newer version without any source changes.</span></span> <span data-ttu-id="b13a6-124">当使用者需要更改源代码以根据更新版本的 API 成功生成时，会发生源不兼容的更改。</span><span class="sxs-lookup"><span data-stu-id="b13a6-124">A *source incompatible change* occurs when a consumer needs to modify source code for it to build successfully against a newer version of an API.</span></span>

## <a name="design-time-compatibility"></a><span data-ttu-id="b13a6-125">设计时兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-125">Design-time compatibility</span></span>

<span data-ttu-id="b13a6-126">设计时兼容性指的是保留不同版本的 Visual Studio 和其他设计时环境中的体验。</span><span class="sxs-lookup"><span data-stu-id="b13a6-126">Design-time compatibility refers to preserving the design-time experience across versions of Visual Studio and other design-time environments.</span></span> <span data-ttu-id="b13a6-127">虽然这可能涉及到设计器的行为或 UI，但设计时兼容性最重要的方面是项目兼容性。</span><span class="sxs-lookup"><span data-stu-id="b13a6-127">While this can involve the behavior or the UI of designers, the most important aspect of design-time compatibility concerns project compatibility.</span></span> <span data-ttu-id="b13a6-128">项目或解决方案必须能够在设计时环境的更新版本中打开和使用。</span><span class="sxs-lookup"><span data-stu-id="b13a6-128">A project or solution must be able to be opened and used on a newer version of the design-time environment.</span></span>

## <a name="backwards-compatibility"></a><span data-ttu-id="b13a6-129">后向兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-129">Backwards compatibility</span></span>

<span data-ttu-id="b13a6-130">向后兼容性指的是 API 的现有使用者能够在操作方式相同的情况下在新版本中运行。</span><span class="sxs-lookup"><span data-stu-id="b13a6-130">Backwards compatibility refers to the ability of an existing consumer of an API to run against a new version while behaving in the same way.</span></span> <span data-ttu-id="b13a6-131">行为变更和二进制兼容性更改都会影响向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="b13a6-131">Both behavioral changes and changes in binary compatibility affect backwards compatibility.</span></span> <span data-ttu-id="b13a6-132">如果使用者无法在运行更新版本的 API 时以不同方式运行或操作，则 API 是向后不兼容的。</span><span class="sxs-lookup"><span data-stu-id="b13a6-132">If a consumer is not able to run or behaves differently when running against the newer version of the API, the API is *backwards incompatible*.</span></span>

<span data-ttu-id="b13a6-133">建议不做出影响向后兼容性的更改，因为开发人员需要更新版本的 API 中的向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="b13a6-133">Changes that affect backwards compatibility are discouraged, since developers expect backwards compatibility in newer versions of an API.</span></span>

## <a name="forward-compatibility"></a><span data-ttu-id="b13a6-134">向前兼容性</span><span class="sxs-lookup"><span data-stu-id="b13a6-134">Forward compatibility</span></span>

<span data-ttu-id="b13a6-135">向前兼容性指的是 API 的现有使用者能够在进行相同操作的情况下在旧版本中运行。</span><span class="sxs-lookup"><span data-stu-id="b13a6-135">Forward compatibility refers to the ability of an existing consumer of an API to run against an older version while exhibiting the same behavior.</span></span> <span data-ttu-id="b13a6-136">如果使用者无法在运行旧版本的 API 时以不同方式运行或操作，则 API 是向前不兼容的。</span><span class="sxs-lookup"><span data-stu-id="b13a6-136">If a consumer is not able to run or behaves differently when run against an older version of the API, the API is *forward incompatible*.</span></span>

<span data-ttu-id="b13a6-137">保持向前兼容性实际上排除了版本之间的任何更改或添加，因为这些更改会阻止面向较新版本的消费者在较低版本下运行。</span><span class="sxs-lookup"><span data-stu-id="b13a6-137">Maintaining forward compatibility virtually precludes any changes or additions from version to version, since those changes prevent a consumer that targets a later version from running under an earlier version.</span></span> <span data-ttu-id="b13a6-138">开发人员认为依赖于较新 API 的使用者可能无法正常运行较旧的 API。</span><span class="sxs-lookup"><span data-stu-id="b13a6-138">Developers expect that a consumer that relies on a newer API may not function correctly against the older API.</span></span>

<span data-ttu-id="b13a6-139">保持向前兼容性不是 .NET Core 的目标。</span><span class="sxs-lookup"><span data-stu-id="b13a6-139">Maintaining forward compatibility is not a goal of .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="b13a6-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="b13a6-140">See also</span></span>

- [<span data-ttu-id="b13a6-141">评估 .NET Core 中的中断性变更</span><span class="sxs-lookup"><span data-stu-id="b13a6-141">Evaluate breaking changes in .NET Core</span></span>](index.md)
