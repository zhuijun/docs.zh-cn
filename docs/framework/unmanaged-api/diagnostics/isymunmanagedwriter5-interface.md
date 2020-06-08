---
title: ISymUnmanagedWriter5 接口
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493573"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="73f3a-102">ISymUnmanagedWriter5 接口</span><span class="sxs-lookup"><span data-stu-id="73f3a-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="73f3a-103">ISymUnmanagedWriter5 接口。</span><span class="sxs-lookup"><span data-stu-id="73f3a-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f3a-104">语法</span><span class="sxs-lookup"><span data-stu-id="73f3a-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="73f3a-105">方法</span><span class="sxs-lookup"><span data-stu-id="73f3a-105">Methods</span></span>  
 <span data-ttu-id="73f3a-106">此接口包含下列方法：</span><span class="sxs-lookup"><span data-stu-id="73f3a-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="73f3a-107">方法</span><span class="sxs-lookup"><span data-stu-id="73f3a-107">Method</span></span>|<span data-ttu-id="73f3a-108">说明</span><span class="sxs-lookup"><span data-stu-id="73f3a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73f3a-109">CloseMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="73f3a-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="73f3a-110">关闭 "特定自定义数据" 部分以获取令牌到源范围的映射信息。</span><span class="sxs-lookup"><span data-stu-id="73f3a-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="73f3a-111">关闭后，不能再添加映射信息。</span><span class="sxs-lookup"><span data-stu-id="73f3a-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="73f3a-112">MapTokenToSourceSpan 方法</span><span class="sxs-lookup"><span data-stu-id="73f3a-112">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="73f3a-113">将给定的元数据标记映射到指定源文件中的给定源行范围。</span><span class="sxs-lookup"><span data-stu-id="73f3a-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="73f3a-114">必须在对[OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)的调用之间调用。</span><span class="sxs-lookup"><span data-stu-id="73f3a-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="73f3a-115">OpenMapTokensToSourceSpans 方法</span><span class="sxs-lookup"><span data-stu-id="73f3a-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="73f3a-116">打开一个特殊的自定义数据部分，将令牌到源范围的映射信息发送到。</span><span class="sxs-lookup"><span data-stu-id="73f3a-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="73f3a-117">如果方法已打开（或相反），则打开此节是错误的。</span><span class="sxs-lookup"><span data-stu-id="73f3a-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73f3a-118">要求</span><span class="sxs-lookup"><span data-stu-id="73f3a-118">Requirements</span></span>  
 <span data-ttu-id="73f3a-119">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="73f3a-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f3a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73f3a-120">See also</span></span>

- [<span data-ttu-id="73f3a-121">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="73f3a-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="73f3a-122">ISymUnmanagedWriter4 接口</span><span class="sxs-lookup"><span data-stu-id="73f3a-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
