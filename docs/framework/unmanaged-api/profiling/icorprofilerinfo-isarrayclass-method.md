---
title: ICorProfilerInfo::IsArrayClass 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 2a3f5bb0c54935e524cc955a5e11aac75b0c0923
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497551"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass 方法
确定指定的类是否为数组类。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>参数  
 `classId`  
 中要检查的类的 ID。  
  
 `pBaseElemType`  
 弄指向 CorElementType 枚举的值的指针，该枚举指示数组元素的类型。  
  
 `pBaseClassId`  
 弄指向数组元素的类 ID 的指针（如果可用）。  
  
 `pcRank`  
 弄指向一个整数的指针，该整数指示数组的秩（即维度的数目）。  
  
## <a name="remarks"></a>注解  
 如果指定的类是一个数组类，则该 `IsArrayClass` 方法将返回 S_OK HRESULT 和任何非 null 输出参数的值。 否则，它将返回 S_FALSE。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorProfilerInfo 接口](icorprofilerinfo-interface.md)
