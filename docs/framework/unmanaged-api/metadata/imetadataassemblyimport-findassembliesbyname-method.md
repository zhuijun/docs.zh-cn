---
title: IMetaDataAssemblyImport::FindAssembliesByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: d2693a94f02214df6d7265b26e3d70d91adcf8a7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503830"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="9150c-102">IMetaDataAssemblyImport::FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="9150c-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="9150c-103">`szAssemblyName`使用由公共语言运行时（CLR）用于解析引用的标准规则，获取具有指定参数的程序集的数组。</span><span class="sxs-lookup"><span data-stu-id="9150c-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9150c-104">语法</span><span class="sxs-lookup"><span data-stu-id="9150c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9150c-105">参数</span><span class="sxs-lookup"><span data-stu-id="9150c-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="9150c-106">中要在其中搜索给定程序集的根目录。</span><span class="sxs-lookup"><span data-stu-id="9150c-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="9150c-107">如果此值设置为 `null` ， `FindAssembliesByName` 则将仅在程序集的全局程序集缓存中查找。</span><span class="sxs-lookup"><span data-stu-id="9150c-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="9150c-108">中要在其中搜索程序集的根目录下以分号分隔的子目录（例如 "bin; bin2"）的列表。</span><span class="sxs-lookup"><span data-stu-id="9150c-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="9150c-109">除了在默认探测规则中指定的目录之外，还会探测这些目录。</span><span class="sxs-lookup"><span data-stu-id="9150c-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="9150c-110">中要查找的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="9150c-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="9150c-111">此字符串的格式在的 "类引用" 页中定义 <xref:System.Reflection.AssemblyName> 。</span><span class="sxs-lookup"><span data-stu-id="9150c-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="9150c-112">中要在其中放置接口指针的[IUnknown](/cpp/atl/iunknown)类型的数组 `IMetadataAssemblyImport` 。</span><span class="sxs-lookup"><span data-stu-id="9150c-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9150c-113">弄可放置的接口指针的最大数目 `ppIUnk` 。</span><span class="sxs-lookup"><span data-stu-id="9150c-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="9150c-114">弄返回的接口指针的数目。</span><span class="sxs-lookup"><span data-stu-id="9150c-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="9150c-115">即，实际置于中的接口指针的数目 `ppIUnk` 。</span><span class="sxs-lookup"><span data-stu-id="9150c-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9150c-116">返回值</span><span class="sxs-lookup"><span data-stu-id="9150c-116">Return Value</span></span>  
  
|<span data-ttu-id="9150c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9150c-117">HRESULT</span></span>|<span data-ttu-id="9150c-118">说明</span><span class="sxs-lookup"><span data-stu-id="9150c-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9150c-119">`FindAssembliesByName`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="9150c-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9150c-120">没有程序集。</span><span class="sxs-lookup"><span data-stu-id="9150c-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9150c-121">注解</span><span class="sxs-lookup"><span data-stu-id="9150c-121">Remarks</span></span>  
 <span data-ttu-id="9150c-122">在给定程序集名称的 `FindAssembliesByName` 情况下，方法通过遵循用于解析程序集引用的标准规则查找程序集。</span><span class="sxs-lookup"><span data-stu-id="9150c-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="9150c-123">（有关详细信息，请参阅[运行时如何定位程序集](../../deployment/how-the-runtime-locates-assemblies.md)。）`FindAssembliesByName`允许调用方配置程序集解析程序上下文的各个方面，例如应用程序基和专用搜索路径。</span><span class="sxs-lookup"><span data-stu-id="9150c-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="9150c-124">`FindAssembliesByName`方法要求在进程中初始化 CLR，以便调用程序集解析逻辑。</span><span class="sxs-lookup"><span data-stu-id="9150c-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="9150c-125">因此，在调用之前，必须先调用[CoInitializeEE](../hosting/coinitializeee-function.md) （传递 COINITEE_DEFAULT） `FindAssembliesByName` ，然后调用[CoUninitializeCor](../hosting/couninitializecor-function.md)。</span><span class="sxs-lookup"><span data-stu-id="9150c-125">Therefore, you must call [CoInitializeEE](../hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="9150c-126">`FindAssembliesByName`返回一个[IMetaDataImport](imetadataimport-interface.md)指针，该指针指向包含传入的程序集名称的程序集清单的文件。</span><span class="sxs-lookup"><span data-stu-id="9150c-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="9150c-127">如果给定的程序集名称未完全指定（例如，如果不包含版本），则可能会返回多个程序集。</span><span class="sxs-lookup"><span data-stu-id="9150c-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="9150c-128">`FindAssembliesByName`在编译时尝试查找引用的程序集的编译器通常使用。</span><span class="sxs-lookup"><span data-stu-id="9150c-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9150c-129">要求</span><span class="sxs-lookup"><span data-stu-id="9150c-129">Requirements</span></span>  
 <span data-ttu-id="9150c-130">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9150c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9150c-131">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="9150c-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9150c-132">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="9150c-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9150c-133">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9150c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9150c-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="9150c-134">See also</span></span>

- [<span data-ttu-id="9150c-135">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="9150c-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9150c-136">IMetaDataAssemblyImport 接口</span><span class="sxs-lookup"><span data-stu-id="9150c-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
