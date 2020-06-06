---
title: <UseSmallInternalThreadStacks> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 2fd776ce8605e6dcf288dcb3852ded16638a1873
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73114923"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks> 元素
请求公共语言运行时（CLR）在创建其内部使用的某些线程时，通过指定显式堆栈大小来减少内存使用，而不是使用这些线程的默认堆栈大小。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|已启用|必需的特性。<br /><br /> 指定是否请求 CLR 在创建其内部使用的某些线程时使用显式堆栈大小而不是默认堆栈大小。 显式堆栈大小小于默认堆栈大小 1 MB。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|值|说明|  
|-----------|-----------------|  
|true|请求显式堆栈大小。|  
|false|使用默认堆栈大小。 这是 .NET Framework 4 的默认值。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>注解  
 此配置元素用于请求进程中减少的虚拟内存使用，因为 CLR 用于其内部线程的显式线程大小（如果请求被接受）小于默认大小。  
  
> [!IMPORTANT]
> 此配置元素是对 CLR 的请求，而不是绝对要求。 在 .NET Framework 4 中，请求仅适用于 x86 体系结构。 在未来版本的 CLR 中，可能会完全忽略此元素，或将其替换为所选内部线程始终使用的显式堆栈大小。  
  
 如果 CLR 接受请求，则指定此配置元素会在较小的虚拟内存使用情况下提高可靠性，因为较小的堆栈大小可能会导致堆栈溢出。  
  
## <a name="example"></a>示例  
 下面的示例演示如何请求 CLR 对其内部使用的某些线程使用显式堆栈大小。  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- [运行时设置架构](index.md)
- [配置文件架构](../index.md)
