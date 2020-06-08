---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492182"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法
枚举由指定实现的所有接口 `TypeDef` 。
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>参数  
 `phEnum`  
 [in，out]指向枚举器的指针。  
  
 `td`  
 中要枚举其 MethodDef 标记表示接口实现的 TypeDef 的标记。  
  
 `rImpls`  
 弄用于存储 MethodDef 标记的数组。  
  
 `cMax`  
 中数组的最大长度 `rImpls` 。  
  
 `pcImpls`  
 弄返回的标记的实际数量 `rImpls` 。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|说明|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`已成功返回。|  
|`S_FALSE`|没有要枚举的 MethodDef 标记。 在这种情况下， `pcImpls` 设置为零。|  

## <a name="remarks"></a>注解

枚举返回 `mdInterfaceImpl` 由指定的实现的每个接口的令牌集合 `TypeDef` 。 接口令牌按指定的顺序（通过 `DefineTypeDef` 或 `SetTypeDefProps` ）返回。 `mdInterfaceImpl`可以使用[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)查询返回的标记的属性。
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [IMetaDataImport 接口](imetadataimport-interface.md)
- [IMetaDataImport2 接口](imetadataimport2-interface.md)
