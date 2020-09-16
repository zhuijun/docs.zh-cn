---
title: LoadTypeLibWithResolver 函数
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
ms.openlocfilehash: 395d5f63eef12570c07f1f601de7f9e480d62905
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540500"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="42c99-102">LoadTypeLibWithResolver 函数</span><span class="sxs-lookup"><span data-stu-id="42c99-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="42c99-103">加载类型库，并使用提供的 [ITypeLibResolver 接口](itypelibresolver-interface.md) 解析任何内部引用的类型库。</span><span class="sxs-lookup"><span data-stu-id="42c99-103">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c99-104">语法</span><span class="sxs-lookup"><span data-stu-id="42c99-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42c99-105">参数</span><span class="sxs-lookup"><span data-stu-id="42c99-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="42c99-106">中类型库的文件路径。</span><span class="sxs-lookup"><span data-stu-id="42c99-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="42c99-107">中用于控制如何注册类型库的 [REGKIND 枚举](/windows/win32/api/oleauto/ne-oleauto-regkind) 标志。</span><span class="sxs-lookup"><span data-stu-id="42c99-107">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="42c99-108">其可能的值为：</span><span class="sxs-lookup"><span data-stu-id="42c99-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="42c99-109">`REGKIND_DEFAULT`：使用默认注册行为。</span><span class="sxs-lookup"><span data-stu-id="42c99-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="42c99-110">`REGKIND_REGISTER`：注册此类型库。</span><span class="sxs-lookup"><span data-stu-id="42c99-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="42c99-111">`REGKIND_NONE`：请勿注册此类型库。</span><span class="sxs-lookup"><span data-stu-id="42c99-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="42c99-112">中指向 [ITypeLibResolver 接口](itypelibresolver-interface.md)的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="42c99-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="42c99-113">弄对正在加载的类型库的引用。</span><span class="sxs-lookup"><span data-stu-id="42c99-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42c99-114">返回值</span><span class="sxs-lookup"><span data-stu-id="42c99-114">Return Value</span></span>  
 <span data-ttu-id="42c99-115">下表中列出的其中一个 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="42c99-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="42c99-116">返回值</span><span class="sxs-lookup"><span data-stu-id="42c99-116">Return value</span></span>|<span data-ttu-id="42c99-117">含义</span><span class="sxs-lookup"><span data-stu-id="42c99-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="42c99-118">成功。</span><span class="sxs-lookup"><span data-stu-id="42c99-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="42c99-119">内存不足。</span><span class="sxs-lookup"><span data-stu-id="42c99-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="42c99-120">一个或多个指针无效。</span><span class="sxs-lookup"><span data-stu-id="42c99-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="42c99-121">一个或多个参数无效。</span><span class="sxs-lookup"><span data-stu-id="42c99-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="42c99-122">函数无法写入文件。</span><span class="sxs-lookup"><span data-stu-id="42c99-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="42c99-123">无法打开系统注册数据库。</span><span class="sxs-lookup"><span data-stu-id="42c99-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="42c99-124">无法打开类型库。</span><span class="sxs-lookup"><span data-stu-id="42c99-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="42c99-125">未能加载类型库或 DLL。</span><span class="sxs-lookup"><span data-stu-id="42c99-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42c99-126">备注</span><span class="sxs-lookup"><span data-stu-id="42c99-126">Remarks</span></span>  
 <span data-ttu-id="42c99-127">[ (类型库导出程序)Tlbexp.exe](../../tools/tlbexp-exe-type-library-exporter.md)在 `LoadTypeLibWithResolver` 程序集到类型库转换过程中调用该函数。</span><span class="sxs-lookup"><span data-stu-id="42c99-127">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="42c99-128">此函数加载指定的类型库，并对注册表的访问权限降至最低。</span><span class="sxs-lookup"><span data-stu-id="42c99-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="42c99-129">然后，该函数检查类型库以查找内部引用的类型库，其中每个库必须加载并添加到父类型库中。</span><span class="sxs-lookup"><span data-stu-id="42c99-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="42c99-130">在可以加载引用的类型库之前，必须将其引用文件路径解析为完整文件路径。</span><span class="sxs-lookup"><span data-stu-id="42c99-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="42c99-131">这是通过[ITypeLibResolver 接口](itypelibresolver-interface.md)提供的[ResolveTypeLib 方法](resolvetypelib-method.md)实现的，该方法是在参数中传递的 `pTlbResolver` 。</span><span class="sxs-lookup"><span data-stu-id="42c99-131">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="42c99-132">当所引用的类型库的完整文件路径已知时， `LoadTypeLibWithResolver` 函数将加载引用的类型库并将其添加到父类型库中，从而创建组合的主类型库。</span><span class="sxs-lookup"><span data-stu-id="42c99-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="42c99-133">函数解析并加载所有内部引用的类型库后，将在参数中返回对主解析类型库的引用 `pptlib` 。</span><span class="sxs-lookup"><span data-stu-id="42c99-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="42c99-134">`LoadTypeLibWithResolver`函数通常由[Tlbexp.exe (类型库导出程序) ](../../tools/tlbexp-exe-type-library-exporter.md)，后者在参数中提供自己的内部[ITypeLibResolver 接口](itypelibresolver-interface.md)实现 `pTlbResolver` 。</span><span class="sxs-lookup"><span data-stu-id="42c99-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="42c99-135">如果直接调用 `LoadTypeLibWithResolver` ，则必须提供自己的 [ITypeLibResolver 接口](itypelibresolver-interface.md) 实现。</span><span class="sxs-lookup"><span data-stu-id="42c99-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c99-136">要求</span><span class="sxs-lookup"><span data-stu-id="42c99-136">Requirements</span></span>  
 <span data-ttu-id="42c99-137">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42c99-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c99-138">**标头：** TlbRef</span><span class="sxs-lookup"><span data-stu-id="42c99-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="42c99-139">**库：** TlbRef</span><span class="sxs-lookup"><span data-stu-id="42c99-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="42c99-140">**.NET Framework 版本：** 3.5、3.0、2。0</span><span class="sxs-lookup"><span data-stu-id="42c99-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c99-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="42c99-141">See also</span></span>

- [<span data-ttu-id="42c99-142">Tlbexp Helper 函数</span><span class="sxs-lookup"><span data-stu-id="42c99-142">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="42c99-143">LoadTypeLibEx 函数</span><span class="sxs-lookup"><span data-stu-id="42c99-143">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
