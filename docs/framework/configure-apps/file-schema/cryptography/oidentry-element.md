---
title: <oidEntry> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088551"
---
# <a name="oidentry-element"></a>\<oidEntry> 元素
将 ASN.1 对象标识符 (OID) 映射到友好名称。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a>语法  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|**OID**|必需的特性。<br /><br /> 指定与您的类实现的算法相对应的第1个 OID。|  
|**name**|必需的特性。<br /><br /> 指定标记中**name**属性的值 [\<nameEntry>](nameentry-element.md) 。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`cryptographySettings`|包含加密设置。|  
|`mscorlib`|包含 `cryptographySettings` 元素。|  
|`oidMap`|包含与类的 ASN 对象标识符（OID）映射。|  
  
## <a name="remarks"></a>注解  
 ASN. 1 对象标识符以某些加密格式标识算法。 将对象标识符映射到要标识的算法的友好名称。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用元素将 **\<oidEntry>** RIPEMD-160 哈希算法的对象标识符映射到该哈希算法的实现。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [配置文件架构](../index.md)
- [密码设置架构](index.md)
- [加密服务](../../../../standard/security/cryptographic-services.md)
- [配置加密类](../../configure-cryptography-classes.md)
- [将对象标识符映射到加密算法](../../map-object-identifiers-to-cryptography-algorithms.md)
