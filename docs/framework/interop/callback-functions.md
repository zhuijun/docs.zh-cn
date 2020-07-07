---
title: 回调函数
description: 了解回调函数，这些函数是具有托管应用程序的代码，可帮助非托管 DLL 函数完成一项任务。
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: e28756b5ed935aff83363b38d6f33982e87718b2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621712"
---
# <a name="callback-functions"></a><span data-ttu-id="e3eaf-103">回调函数</span><span class="sxs-lookup"><span data-stu-id="e3eaf-103">Callback Functions</span></span>
<span data-ttu-id="e3eaf-104">回调函数是托管应用程序中的代码，可帮助非托管 DLL 函数完成一项任务。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-104">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="e3eaf-105">对回调函数的调用间接从托管应用程序中进行传递、经过 DLL 函数，再回到托管实现。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-105">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="e3eaf-106">一些通过平台调用的 DLL 函数需要托管代码中的回调函数才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-106">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="e3eaf-107">若要从托管代码中调用大部分 DLL 函数，则可以创建函数的托管定义，然后再调用它。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-107">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="e3eaf-108">此过程相当简单。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-108">The process is straightforward.</span></span>  
  
 <span data-ttu-id="e3eaf-109">使用需要回调函数的 DLL 函数还有一些其他步骤。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-109">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="e3eaf-110">首先，必须通过查看函数的文档来确定该函数是否需要回调。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-110">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="e3eaf-111">然后，需要在托管应用程序中创建回调函数。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-111">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="e3eaf-112">最后，调用 DLL 函数，将指针作为一个参数传递给回调函数。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-112">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="e3eaf-113">下图汇总了回调函数和实现步骤：</span><span class="sxs-lookup"><span data-stu-id="e3eaf-113">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![显示平台调用回调过程的图。](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="e3eaf-115">回调函数非常适合用于需要重复执行一项任务的情况。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="e3eaf-116">另一个常见用法是与枚举函数配合使用，如 Windows API 中的“EnumFontFamilies”、“EnumPrinters”和“EnumWindows”  。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="e3eaf-117">EnumWindows 函数通过计算机上所有现有的窗口进行枚举，调用每个窗口上的回调函数以执行任务。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="e3eaf-118">有关说明和示例，请参阅[如何：实现回调函数](how-to-implement-callback-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="e3eaf-118">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3eaf-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="e3eaf-119">See also</span></span>

- [<span data-ttu-id="e3eaf-120">如何：实现回调函数</span><span class="sxs-lookup"><span data-stu-id="e3eaf-120">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="e3eaf-121">调用 DLL 函数</span><span class="sxs-lookup"><span data-stu-id="e3eaf-121">Calling a DLL Function</span></span>](calling-a-dll-function.md)
