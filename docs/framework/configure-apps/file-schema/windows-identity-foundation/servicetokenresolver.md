---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152575"
---
# \<serviceTokenResolver>
注册令牌处理程序集合中的处理程序使用的服务令牌解析程序。 服务令牌解析器用于解析传入令牌和消息的加密令牌。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|属性|说明|  
|---------------|-----------------|  
|type|指定服务令牌解析程序的类型。 <xref:System.IdentityModel.Selectors.SecurityTokenResolver>类型或派生自类的类型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。 有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用]。 必需。|  
  
### <a name="child-elements"></a>子元素  
 无  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|为安全标记处理程序的集合提供配置。|  
  
## <a name="remarks"></a>注解  
 服务令牌解析程序可用于解析传入令牌和消息的加密令牌。 它用于检索应该用于解密传入令牌的密钥。 您必须指定 `type` 属性。 指定的类型可以是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 或从类派生的自定义类型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。  
  
 某些标记处理程序允许您在配置中指定服务令牌解析器设置。 各个标记处理程序上的设置将替代在安全令牌处理程序集合中指定的设置。  
  
> [!NOTE]
> 将 `<serviceTokenResolver>` 元素指定为元素的子元素 [\<identityConfiguration>](identityconfiguration.md) 已不推荐使用，但仍支持向后兼容。 元素上的设置将 `<securityTokenHandlerConfiguration>` 替代元素上的设置 `<identityConfiguration>` 。  
  
## <a name="example"></a>示例  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
