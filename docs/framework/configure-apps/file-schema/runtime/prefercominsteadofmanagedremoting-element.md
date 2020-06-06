---
title: <PreferComInsteadOfManagedRemoting> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452248"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<PreferComInsteadOfManagedRemoting> 元素
指定运行时是否将对跨应用程序域边界的所有调用使用 COM 互操作而不是远程处理。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指示运行时是否将使用 COM 互操作，而不是跨应用程序域边界进行远程处理。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|值|说明|  
|-----------|-----------------|  
|`false`|运行时将跨应用程序域边界使用远程处理。 这是默认设置。|  
|`true`|运行时将跨应用程序域边界使用 COM 互操作。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>注解  
 将 `enabled` 属性设置为时 `true` ，运行时的行为如下所示：  
  
- 当[iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)接口通过 COM 接口进入域时，运行时不为[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)接口调用[iunknown：： QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 。 相反，它会在对象周围构造一个[运行时可调用包装](../../../../standard/native-interop/runtime-callable-wrapper.md)器（RCW）。  
  
- 运行时在接收到已 `QueryInterface` 在此域中创建的任何 COM 可[调用包装](../../../../standard/native-interop/com-callable-wrapper.md)器（CCW）的[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)接口调用时返回 E_NOINTERFACE。  
  
 这两个行为确保跨应用程序域边界在托管对象之间对 COM 接口进行的所有调用均使用 COM 和 COM 互操作，而不是远程处理。  
  
## <a name="example"></a>示例  
 下面的示例演示如何指定运行时应跨隔离边界使用 COM 互操作：  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- [运行时设置架构](index.md)
- [配置文件架构](../index.md)
