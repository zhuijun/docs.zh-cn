---
title: 调用 DLL 函数
description: 查看有关调用可能令人感到迷惑的 DLL 函数的问题。 函数调用过程有所不同，具体取决于返回类型是否为 blittable。
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 90f8f47148e652a9942a35be1564bed94c155216
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620893"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="c36b3-104">调用 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="c36b3-104">Calling a DLL Function</span></span>
<span data-ttu-id="c36b3-105">尽管调用非托管 DLL 函数与调用其他托管代码几乎完全相同，但有一些差异会使 DLL 函数一开始令人感到迷惑。</span><span class="sxs-lookup"><span data-stu-id="c36b3-105">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="c36b3-106">本部分介绍的主题描述了与一些与调用相关的异常问题。</span><span class="sxs-lookup"><span data-stu-id="c36b3-106">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="c36b3-107">从平台调用返回的结构必须是在托管代码和非托管代码中表示形式相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c36b3-107">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="c36b3-108">这些类型称为 blittable 类型，因为它们不需要转换（请参阅 [Blittable 类型和非 Blittable 类型](blittable-and-non-blittable-types.md)）。</span><span class="sxs-lookup"><span data-stu-id="c36b3-108">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="c36b3-109">若要调用返回类型为 non-blittable 结构的函数，可定义与 non-blittable 类型大小相同的 blittable 帮助程序类型，并在函数返回后转换数据。</span><span class="sxs-lookup"><span data-stu-id="c36b3-109">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c36b3-110">本节内容</span><span class="sxs-lookup"><span data-stu-id="c36b3-110">In This Section</span></span>  
 [<span data-ttu-id="c36b3-111">传递结构</span><span class="sxs-lookup"><span data-stu-id="c36b3-111">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="c36b3-112">确定使用预定义布局传递数据结构的问题。</span><span class="sxs-lookup"><span data-stu-id="c36b3-112">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="c36b3-113">回调函数</span><span class="sxs-lookup"><span data-stu-id="c36b3-113">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="c36b3-114">提供有关回调函数的基本信息。</span><span class="sxs-lookup"><span data-stu-id="c36b3-114">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="c36b3-115">如何：实现回调函数</span><span class="sxs-lookup"><span data-stu-id="c36b3-115">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="c36b3-116">描述如何在托管代码中实现回调函数。</span><span class="sxs-lookup"><span data-stu-id="c36b3-116">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c36b3-117">相关章节</span><span class="sxs-lookup"><span data-stu-id="c36b3-117">Related Sections</span></span>  
 [<span data-ttu-id="c36b3-118">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="c36b3-118">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="c36b3-119">描述如何使用平台调用调用非托管 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="c36b3-119">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="c36b3-120">用平台调用封送数据</span><span class="sxs-lookup"><span data-stu-id="c36b3-120">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="c36b3-121">描述如何声明方法形参以及如何将实参传递给由非托管库导出的函数。</span><span class="sxs-lookup"><span data-stu-id="c36b3-121">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
