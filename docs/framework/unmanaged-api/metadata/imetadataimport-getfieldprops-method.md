---
title: IMetaDataImport::GetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491236"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps 方法
获取与指定 FieldDef 标记引用的字段关联的元数据。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>参数  
 `mb`  
 中一个 FieldDef 标记，它表示要为其获取关联元数据的字段。  
  
 `pClass`  
 弄一个指针，指向表示字段所属类的类型的 TypeDef 标记。  
  
 `szField`  
 弄字段的名称。  
  
 `cchField`  
 中*SzField*缓冲区的大小（以宽字符为大小）。  
  
 `pchField`  
 弄返回的缓冲区的实际大小。  
  
 `pdwAttr`  
 弄与字段的元数据关联的标志。  
  
 `ppvSigBlob`  
 中指向描述字段的二进制元数据值的指针。  
  
 `pcbSigBlob`  
 弄的大小（以字节为单位） `ppvSigBlob` 。  
  
 `pdwCPlusTypeFlag`  
 弄指定字段的值类型的标志。  
  
 `ppValue`  
 弄字段的常数值。  
  
 `pcchValue`  
 弄的大小（以字符为字符 `ppValue` ），如果不存在任何字符串，则为零。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** Cor  
  
 **库：** 作为资源包括在 Mscoree.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [IMetaDataImport 接口](imetadataimport-interface.md)
- [IMetaDataImport2 接口](imetadataimport2-interface.md)
