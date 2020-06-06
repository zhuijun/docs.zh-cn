---
title: 密码设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087996"
---
# <a name="cryptography-settings-schema"></a>密码设置架构
加密设置架构包含元素，这些元素指定如何将友好算法名称映射到实现加密算法的类。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|元素|说明|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|包含加密类的列表，这些类具有到元素中的友好名称的映射 **\<nameEntry>** 。|  
|[**\<cryptoClass**>](cryptoclass-element.md)|包含一个加密类，该类具有到元素中的友好名称的映射 **\<nameEntry>** 。|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|包含加密设置。|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|包含类到友好名称的映射。|  
|[**\<mscorlib>** 用于加密设置的元素](mscorlib-element-for-cryptography-settings.md)|包含 **\<cryptographySettings>** 元素。|  
|[**\<nameEntry>**](nameentry-element.md)|将类名称映射到友好算法名称，允许一个类具有多个友好名称。|  
|[**\<oidEntry>**](oidentry-element.md)|将 ASN.1 对象标识符 (OID) 映射到友好名称。|  
|[**\<oidMap>**](oidmap-element.md)|包含映射到类的 ASN.1 OID。|  
  
## <a name="see-also"></a>请参阅

- [配置文件架构](../index.md)
- [加密服务](../../../../standard/security/cryptographic-services.md)
