---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251858"
---
# \<serviceCertificate>
<span data-ttu-id="2c4c9-101">配置用于加密和解密令牌的 x.509 证书。</span><span class="sxs-lookup"><span data-stu-id="2c4c9-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="2c4c9-102">语法</span><span class="sxs-lookup"><span data-stu-id="2c4c9-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c4c9-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2c4c9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2c4c9-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2c4c9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c4c9-105">特性</span><span class="sxs-lookup"><span data-stu-id="2c4c9-105">Attributes</span></span>  
 <span data-ttu-id="2c4c9-106">无</span><span class="sxs-lookup"><span data-stu-id="2c4c9-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c4c9-107">子元素</span><span class="sxs-lookup"><span data-stu-id="2c4c9-107">Child Elements</span></span>  
  
|<span data-ttu-id="2c4c9-108">元素</span><span class="sxs-lookup"><span data-stu-id="2c4c9-108">Element</span></span>|<span data-ttu-id="2c4c9-109">说明</span><span class="sxs-lookup"><span data-stu-id="2c4c9-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="2c4c9-110">指定用于在证书存储中查找和验证 x.509 证书的设置。</span><span class="sxs-lookup"><span data-stu-id="2c4c9-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c4c9-111">父元素</span><span class="sxs-lookup"><span data-stu-id="2c4c9-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2c4c9-112">元素</span><span class="sxs-lookup"><span data-stu-id="2c4c9-112">Element</span></span>|<span data-ttu-id="2c4c9-113">说明</span><span class="sxs-lookup"><span data-stu-id="2c4c9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="2c4c9-114">包含配置 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的设置。</span><span class="sxs-lookup"><span data-stu-id="2c4c9-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2c4c9-115">示例</span><span class="sxs-lookup"><span data-stu-id="2c4c9-115">Example</span></span>  
 <span data-ttu-id="2c4c9-116">下面的 XML 演示如何使用 \<serviceCertificate> 元素。</span><span class="sxs-lookup"><span data-stu-id="2c4c9-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="2c4c9-117">XML 是从示例获取的 `CustomToken` 。</span><span class="sxs-lookup"><span data-stu-id="2c4c9-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
