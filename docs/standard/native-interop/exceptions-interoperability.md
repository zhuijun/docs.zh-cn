---
title: 异常互操作性
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 90774b5d1b64feb34e01f48708d94f8f841a7c9d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550867"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="cd627-102">在非托管代码中处理互操作异常</span><span class="sxs-lookup"><span data-stu-id="cd627-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="cd627-103">仅在 Windows 平台上支持非托管代码异常互操作。</span><span class="sxs-lookup"><span data-stu-id="cd627-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="cd627-104">非 Windows 平台上会出现可移植性问题。</span><span class="sxs-lookup"><span data-stu-id="cd627-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="cd627-105">由于 Unix ABI 没有异常处理的定义，因此托管代码无法知道异常机制的内部工作方式。</span><span class="sxs-lookup"><span data-stu-id="cd627-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="cd627-106">因此，异常最终可能导致不可预知的行为和故障。</span><span class="sxs-lookup"><span data-stu-id="cd627-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="cd627-107">Setjmp/Longjmp 行为</span><span class="sxs-lookup"><span data-stu-id="cd627-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="cd627-108">不支持与 `setjmp` 和 `longjmp` C 函数的互操作。</span><span class="sxs-lookup"><span data-stu-id="cd627-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="cd627-109">无法使用 `longjmp` 跳过托管帧。</span><span class="sxs-lookup"><span data-stu-id="cd627-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="cd627-110">有关详细信息，请参阅 [longjmp 文档](/cpp/c-runtime-library/reference/longjmp)。</span><span class="sxs-lookup"><span data-stu-id="cd627-110">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd627-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd627-111">See also</span></span>

- [<span data-ttu-id="cd627-112">异常</span><span class="sxs-lookup"><span data-stu-id="cd627-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="cd627-113">与本机库的互操作</span><span class="sxs-lookup"><span data-stu-id="cd627-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
