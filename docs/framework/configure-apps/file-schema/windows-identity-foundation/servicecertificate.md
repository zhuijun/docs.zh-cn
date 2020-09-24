---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: ce8be6eea5469b099a368a0b62e791faa7e3cbfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156987"
---
# \<serviceCertificate>

<span data-ttu-id="19194-101">配置用于加密和解密令牌的 x.509 证书。</span><span class="sxs-lookup"><span data-stu-id="19194-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="19194-102">语法</span><span class="sxs-lookup"><span data-stu-id="19194-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19194-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="19194-103">Attributes and Elements</span></span>  

 <span data-ttu-id="19194-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19194-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19194-105">特性</span><span class="sxs-lookup"><span data-stu-id="19194-105">Attributes</span></span>  

 <span data-ttu-id="19194-106">无</span><span class="sxs-lookup"><span data-stu-id="19194-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19194-107">子元素</span><span class="sxs-lookup"><span data-stu-id="19194-107">Child Elements</span></span>  
  
|<span data-ttu-id="19194-108">元素</span><span class="sxs-lookup"><span data-stu-id="19194-108">Element</span></span>|<span data-ttu-id="19194-109">描述</span><span class="sxs-lookup"><span data-stu-id="19194-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="19194-110">指定用于在证书存储中查找和验证 x.509 证书的设置。</span><span class="sxs-lookup"><span data-stu-id="19194-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19194-111">父元素</span><span class="sxs-lookup"><span data-stu-id="19194-111">Parent Elements</span></span>  
  
|<span data-ttu-id="19194-112">元素</span><span class="sxs-lookup"><span data-stu-id="19194-112">Element</span></span>|<span data-ttu-id="19194-113">描述</span><span class="sxs-lookup"><span data-stu-id="19194-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="19194-114">包含配置 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 的设置。</span><span class="sxs-lookup"><span data-stu-id="19194-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="19194-115">示例</span><span class="sxs-lookup"><span data-stu-id="19194-115">Example</span></span>  

 <span data-ttu-id="19194-116">下面的 XML 演示如何使用 \<serviceCertificate> 元素。</span><span class="sxs-lookup"><span data-stu-id="19194-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="19194-117">XML 是从示例获取的 `CustomToken` 。</span><span class="sxs-lookup"><span data-stu-id="19194-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
