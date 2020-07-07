---
title: 创建用于容纳 DLL 函数的类
description: 在 .NET 中创建用于容纳 DLL 函数的托管类包装器，这有助于封装平台功能。
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622167"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="eb4be-103">创建用于容纳 DLL 函数的类</span><span class="sxs-lookup"><span data-stu-id="eb4be-103">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="eb4be-104">将常用的 DLL 函数包装在托管类中，这是封装平台功能的一种有效方式。</span><span class="sxs-lookup"><span data-stu-id="eb4be-104">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="eb4be-105">虽然不必在每种情形下都这样做，但由于定义 DLL 函数相当麻烦且容易出错，所以提供类包装器非常简便。</span><span class="sxs-lookup"><span data-stu-id="eb4be-105">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="eb4be-106">如果使用 Visual Basic 或 C# 进行编程，必须在一个类或 Visual Basic 模块中声明 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="eb4be-106">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="eb4be-107">在一个类中，为每个要调用的 DLL 函数定义静态方法。</span><span class="sxs-lookup"><span data-stu-id="eb4be-107">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="eb4be-108">定义中可以包括附加信息，例如传递方法参数使用的字符集或调用约定；如果省略这些信息，则选择默认设置。</span><span class="sxs-lookup"><span data-stu-id="eb4be-108">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="eb4be-109">有关声明选项及其默认设置的完整列表，请参阅[在托管代码中创建原型](creating-prototypes-in-managed-code.md)。</span><span class="sxs-lookup"><span data-stu-id="eb4be-109">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="eb4be-110">包装之后，就可按照调用任何其他类上的静态方法的方式来调用该类上的方法。</span><span class="sxs-lookup"><span data-stu-id="eb4be-110">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="eb4be-111">平台调用自动处理基础导出函数。</span><span class="sxs-lookup"><span data-stu-id="eb4be-111">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="eb4be-112">为平台调用设计托管类时，应考虑类和 DLL 函数之间的关系。</span><span class="sxs-lookup"><span data-stu-id="eb4be-112">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="eb4be-113">例如，你可以：</span><span class="sxs-lookup"><span data-stu-id="eb4be-113">For example, you can:</span></span>  
  
- <span data-ttu-id="eb4be-114">在现有类内声明 DLL 函数。</span><span class="sxs-lookup"><span data-stu-id="eb4be-114">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="eb4be-115">分别为每个 DLL 函数创建一个类，使函数相互独立，易于查找。</span><span class="sxs-lookup"><span data-stu-id="eb4be-115">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="eb4be-116">为一组相关 DLL 函数创建一个类，形成逻辑分组并减少开销。</span><span class="sxs-lookup"><span data-stu-id="eb4be-116">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="eb4be-117">可对该类及其方法随意命名。</span><span class="sxs-lookup"><span data-stu-id="eb4be-117">You can name the class and its methods as you please.</span></span> <span data-ttu-id="eb4be-118">有关演示如何构造要用于平台调用、基于 .NET 的声明的示例，请参阅[用平台调用封送数据](marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="eb4be-118">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4be-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="eb4be-119">See also</span></span>

- [<span data-ttu-id="eb4be-120">使用非托管 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="eb4be-120">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="eb4be-121">标识 DLL 中的函数</span><span class="sxs-lookup"><span data-stu-id="eb4be-121">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="eb4be-122">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="eb4be-122">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="eb4be-123">调用 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="eb4be-123">Calling a DLL Function</span></span>](calling-a-dll-function.md)
