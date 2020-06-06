---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773943"
---
# \<client>
`client` 元素定义客户端可以连接的终结点的列表。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a>语法

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性
 无

### <a name="child-elements"></a>子元素

|元素|说明|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|包含终结点元素的集合，这些元素指定此客户端可以连接到的终结点。|
|[\<metadata>](metadata.md)|包含用于处理元数据的设置。|

### <a name="parent-elements"></a>父元素

|元素|说明|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|所有 Windows Communication Foundation (WCF) 配置元素的根元素。|

## <a name="remarks"></a>注解
 `client` 节定义客户端可以连接的终结点的列表。 客户端节中列出的每个终结点都定义了它自己的绑定、行为和协定。 它由 `name` 和 `contract` 属性共同进行唯一标识。 客户端代码指定要连接到该客户端实现的服务终结点的 `name`。 如果省略 `name` 属性，则该终结点将作为其实现的协定的默认终结点。

 此外，本节还指定了用于处理元数据的设置。

## <a name="example"></a>示例

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [WCF 客户端配置](../../../wcf/feature-details/client-configuration.md)
- [客户端](../../../wcf/feature-details/clients.md)
