---
title: 处理 COM 互操作异常
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 9c8eb374058ddbd2ba3d866079f0f40b292b69ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286101"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="5164a-102">处理 COM 互操作异常</span><span class="sxs-lookup"><span data-stu-id="5164a-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="5164a-103">托管和非托管代码可协同工作来处理异常。</span><span class="sxs-lookup"><span data-stu-id="5164a-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="5164a-104">如果方法在托管代码中引发异常，公共语言运行时可将 HRESULT 传递至 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="5164a-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="5164a-105">如果方法因返回失败 HRESULT 而在非托管代码中失败，运行时会引发可由托管代码捕获的异常。</span><span class="sxs-lookup"><span data-stu-id="5164a-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="5164a-106">运行时自动将 HRESULT 从 COM 互操作映射到更具体的异常。</span><span class="sxs-lookup"><span data-stu-id="5164a-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="5164a-107">例如，E_ACCESSDENIED 成为 <xref:System.UnauthorizedAccessException>、E_OUTOFMEMORY 成为 <xref:System.OutOfMemoryException>，依次类推。</span><span class="sxs-lookup"><span data-stu-id="5164a-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="5164a-108">如果 HRESULT 为自定义结果或运行时不知道它，运行时会将泛型 <xref:System.Runtime.InteropServices.COMException> 传递到客户端。</span><span class="sxs-lookup"><span data-stu-id="5164a-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="5164a-109">COMException 的 ErrorCode 属性包含 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="5164a-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="5164a-110">处理 IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="5164a-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="5164a-111">当错误从 COM 传递至托管代码时，运行时会将错误信息填充至异常对象。</span><span class="sxs-lookup"><span data-stu-id="5164a-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="5164a-112">支持 IErrorInfo 并返回 HRESULT 的 COM 对象将向托管代码异常提供此信息。</span><span class="sxs-lookup"><span data-stu-id="5164a-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="5164a-113">例如，运行时将“说明”从 COM 错误映射至异常的 <xref:System.Exception.Message%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="5164a-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="5164a-114">如果 HRESULT 未提供任何其他错误信息，运行时将对很多异常的属性填充默认值。</span><span class="sxs-lookup"><span data-stu-id="5164a-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="5164a-115">如果方法在非托管代码中失败，则异常可以传递至托管代码段中。</span><span class="sxs-lookup"><span data-stu-id="5164a-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="5164a-116">主题 [HRESULTS 和异常](../../framework/interop/how-to-map-hresults-and-exceptions.md)中的表展示了如何将 HRESULTS 映射到运行时异常对象。</span><span class="sxs-lookup"><span data-stu-id="5164a-116">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="5164a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5164a-117">See also</span></span>

- [<span data-ttu-id="5164a-118">异常</span><span class="sxs-lookup"><span data-stu-id="5164a-118">Exceptions</span></span>](index.md)
