---
title: ISymUnmanagedAsyncMethod 接口
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504447"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="f4c01-102">ISymUnmanagedAsyncMethod 接口</span><span class="sxs-lookup"><span data-stu-id="f4c01-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="f4c01-103">此接口是[ISymUnmanagedAsyncMethodPropertiesWriter 接口](isymunmanagedasyncmethodpropertieswriter-interface.md)的读取补充。</span><span class="sxs-lookup"><span data-stu-id="f4c01-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c01-104">语法</span><span class="sxs-lookup"><span data-stu-id="f4c01-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="f4c01-105">方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-105">Methods</span></span>  
 <span data-ttu-id="f4c01-106">此接口包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="f4c01-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="f4c01-107">方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-107">Method</span></span>|<span data-ttu-id="f4c01-108">说明</span><span class="sxs-lookup"><span data-stu-id="f4c01-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4c01-109">GetAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="f4c01-110">请参阅[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c01-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="f4c01-111">GetAsyncStepInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="f4c01-112">请参阅[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c01-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="f4c01-113">GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="f4c01-114">请参阅[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c01-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="f4c01-115">GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="f4c01-116">请参阅[DefineKickoffMethod 方法](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c01-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="f4c01-117">HasCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="f4c01-118">请参阅[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c01-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="f4c01-119">IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="f4c01-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="f4c01-120">检查方法是否有异步信息。</span><span class="sxs-lookup"><span data-stu-id="f4c01-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="f4c01-121">如果此方法返回，则 `FALSE` 调用此接口中的任何其他方法无效。</span><span class="sxs-lookup"><span data-stu-id="f4c01-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="f4c01-122">`E_UNEXPECTED`在这种情况下，它们都将返回。</span><span class="sxs-lookup"><span data-stu-id="f4c01-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4c01-123">要求</span><span class="sxs-lookup"><span data-stu-id="f4c01-123">Requirements</span></span>  
 <span data-ttu-id="f4c01-124">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="f4c01-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c01-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4c01-125">See also</span></span>

- [<span data-ttu-id="f4c01-126">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="f4c01-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
