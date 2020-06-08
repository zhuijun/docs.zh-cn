---
title: IMetaDataImport::EnumPermissionSets 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
ms.openlocfilehash: 79b1493d262288c1d85a56538810e35a73441595
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491746"
---
# <a name="imetadataimportenumpermissionsets-method"></a>IMetaDataImport::EnumPermissionSets 方法
枚举指定的元数据范围内的对象的权限。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>参数  
 `phEnum`  
 [in，out]指向枚举器的指针。 第一次调用此方法时，此值必须为 NULL。  
  
 `tk`  
 中一个元数据令牌，用于限制搜索范围，或为 NULL 以搜索尽可能大的范围。  
  
 `dwActions`  
 中表示 <xref:System.Security.Permissions.SecurityAction> 要包含在中的值的标志 `rPermission` ，若要返回所有操作，则为零。  
  
 `rPermission`  
 弄用于存储权限令牌的数组。  
  
 `cMax`  
 [in] `rPermission` 数组的最大大小。  
  
 `pcTokens`  
 弄中返回的权限令牌数 `rPermission` 。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|说明|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets`已成功返回。|  
|`S_FALSE`|没有要枚举的令牌。 在这种情况下， `pcTokens` 为零。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [IMetaDataImport 接口](imetadataimport-interface.md)
- [IMetaDataImport2 接口](imetadataimport2-interface.md)
