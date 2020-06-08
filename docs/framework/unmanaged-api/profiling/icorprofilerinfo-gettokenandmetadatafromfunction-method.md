---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
ms.openlocfilehash: 1cc05f4c10f4a5b042ff14c05f3c85a7b5935184
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497889"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="7941c-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction 方法</span><span class="sxs-lookup"><span data-stu-id="7941c-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="7941c-103">获取可用于指定函数的标记的元数据标记和元数据接口实例。</span><span class="sxs-lookup"><span data-stu-id="7941c-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7941c-104">语法</span><span class="sxs-lookup"><span data-stu-id="7941c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7941c-105">参数</span><span class="sxs-lookup"><span data-stu-id="7941c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7941c-106">中要获取其元数据标记和元数据接口的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="7941c-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="7941c-107">中要获取其实例的元数据接口的引用 ID。</span><span class="sxs-lookup"><span data-stu-id="7941c-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="7941c-108">弄一个指针，指向可用于指定函数的标记的元数据接口实例的地址。</span><span class="sxs-lookup"><span data-stu-id="7941c-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="7941c-109">弄指向指定函数的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="7941c-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7941c-110">要求</span><span class="sxs-lookup"><span data-stu-id="7941c-110">Requirements</span></span>  
 <span data-ttu-id="7941c-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7941c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7941c-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7941c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7941c-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7941c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7941c-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7941c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7941c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7941c-115">See also</span></span>

- [<span data-ttu-id="7941c-116">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="7941c-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
