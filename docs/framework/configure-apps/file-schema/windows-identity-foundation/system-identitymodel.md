---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 216b4c73e06469d6577c61338ad1af0fdd2dc05e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185569"
---
# \<system.identityModel>

<span data-ttu-id="0e689-102">提供用于在应用程序中启用 Windows Identity Foundation (WIF) 选项的配置。</span><span class="sxs-lookup"><span data-stu-id="0e689-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="0e689-103">语法</span><span class="sxs-lookup"><span data-stu-id="0e689-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e689-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0e689-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0e689-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0e689-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e689-106">特性</span><span class="sxs-lookup"><span data-stu-id="0e689-106">Attributes</span></span>  

 <span data-ttu-id="0e689-107">无</span><span class="sxs-lookup"><span data-stu-id="0e689-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e689-108">子元素</span><span class="sxs-lookup"><span data-stu-id="0e689-108">Child Elements</span></span>  
  
|<span data-ttu-id="0e689-109">元素</span><span class="sxs-lookup"><span data-stu-id="0e689-109">Element</span></span>|<span data-ttu-id="0e689-110">描述</span><span class="sxs-lookup"><span data-stu-id="0e689-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="0e689-111">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="0e689-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e689-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0e689-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0e689-113">元素</span><span class="sxs-lookup"><span data-stu-id="0e689-113">Element</span></span>|<span data-ttu-id="0e689-114">描述</span><span class="sxs-lookup"><span data-stu-id="0e689-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="0e689-115">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="0e689-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e689-116">备注</span><span class="sxs-lookup"><span data-stu-id="0e689-116">Remarks</span></span>  

 <span data-ttu-id="0e689-117">将 `<system.identityModel>` 部分添加到配置文件，以便将服务或应用程序配置为使用 Windows Identity Foundation (WIF) 。</span><span class="sxs-lookup"><span data-stu-id="0e689-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="0e689-118">`<system.identityModel>`元素由 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> 类表示。</span><span class="sxs-lookup"><span data-stu-id="0e689-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e689-119">示例</span><span class="sxs-lookup"><span data-stu-id="0e689-119">Example</span></span>  

 <span data-ttu-id="0e689-120">下面的示例演示如何将节添加 `<system.identityModel>` 到配置文件。</span><span class="sxs-lookup"><span data-stu-id="0e689-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="0e689-121">必须首先在元素下添加配置节和命名空间声明 `<configSections>` 。</span><span class="sxs-lookup"><span data-stu-id="0e689-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="0e689-122">然后，可以将 `<system.IdentityModel>` 元素添加到配置文件中，以指定一个或多个标识配置。</span><span class="sxs-lookup"><span data-stu-id="0e689-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e689-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="0e689-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
