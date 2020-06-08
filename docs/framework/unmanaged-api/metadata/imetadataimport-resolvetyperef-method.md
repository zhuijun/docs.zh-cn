---
title: IMetaDataImport::ResolveTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: f55af87e21b48430807166cb03e1d41271e830a1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503427"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="f81a1-102">IMetaDataImport::ResolveTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="f81a1-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="f81a1-103">解析 <xref:System.Type> 指定的 TypeRef 标记所表示的引用。</span><span class="sxs-lookup"><span data-stu-id="f81a1-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f81a1-104">语法</span><span class="sxs-lookup"><span data-stu-id="f81a1-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f81a1-105">参数</span><span class="sxs-lookup"><span data-stu-id="f81a1-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="f81a1-106">中要为其返回引用的类型信息的 TypeRef 元数据标记。</span><span class="sxs-lookup"><span data-stu-id="f81a1-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="f81a1-107">中要在中返回的接口的 IID `ppIScope` 。</span><span class="sxs-lookup"><span data-stu-id="f81a1-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="f81a1-108">通常，这会 IID_IMetaDataImport。</span><span class="sxs-lookup"><span data-stu-id="f81a1-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="f81a1-109">弄用于定义所引用类型的模块范围的接口。</span><span class="sxs-lookup"><span data-stu-id="f81a1-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="f81a1-110">弄指向表示被引用类型的 TypeDef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="f81a1-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f81a1-111">注解</span><span class="sxs-lookup"><span data-stu-id="f81a1-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f81a1-112">如果加载多个应用程序域，请不要使用此方法。</span><span class="sxs-lookup"><span data-stu-id="f81a1-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="f81a1-113">方法不考虑应用程序域边界。</span><span class="sxs-lookup"><span data-stu-id="f81a1-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="f81a1-114">如果加载程序集的多个版本，并且这些版本包含相同命名空间的相同类型，则该方法将返回它找到的第一个类型的模块范围。</span><span class="sxs-lookup"><span data-stu-id="f81a1-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="f81a1-115">`ResolveTypeRef`方法在其他模块中搜索类型定义。</span><span class="sxs-lookup"><span data-stu-id="f81a1-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="f81a1-116">如果找到类型定义，则 `ResolveTypeRef` 返回该模块范围的接口以及该类型的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="f81a1-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="f81a1-117">如果要解析的类型引用的解析范围为 AssemblyRef，则此 `ResolveTypeRef` 方法仅在已使用调用[IMetaDataDispenser：： OpenScope](imetadatadispenser-openscope-method.md)方法或[IMetaDataDispenser：： OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md)方法打开的元数据范围中搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="f81a1-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="f81a1-118">这是因为， `ResolveTypeRef` 无法仅从磁盘或全局程序集缓存中存储程序集的 AssemblyRef 范围进行确定。</span><span class="sxs-lookup"><span data-stu-id="f81a1-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f81a1-119">要求</span><span class="sxs-lookup"><span data-stu-id="f81a1-119">Requirements</span></span>  
 <span data-ttu-id="f81a1-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f81a1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f81a1-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="f81a1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f81a1-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="f81a1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f81a1-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f81a1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81a1-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f81a1-124">See also</span></span>

- [<span data-ttu-id="f81a1-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="f81a1-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f81a1-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="f81a1-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
