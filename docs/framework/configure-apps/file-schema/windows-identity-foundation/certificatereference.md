---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c21e5186b8afdf8c72cbfc605af94c95bc2bc0d5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201366"
---
# \<certificateReference>

<span data-ttu-id="975b2-101">指定用于在证书存储中查找和验证 x.509 证书的设置。</span><span class="sxs-lookup"><span data-stu-id="975b2-101">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="975b2-102">语法</span><span class="sxs-lookup"><span data-stu-id="975b2-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="975b2-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="975b2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="975b2-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="975b2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="975b2-105">特性</span><span class="sxs-lookup"><span data-stu-id="975b2-105">Attributes</span></span>  
  
|<span data-ttu-id="975b2-106">属性</span><span class="sxs-lookup"><span data-stu-id="975b2-106">Attribute</span></span>|<span data-ttu-id="975b2-107">描述</span><span class="sxs-lookup"><span data-stu-id="975b2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="975b2-108">storeName</span><span class="sxs-lookup"><span data-stu-id="975b2-108">storeName</span></span>|<span data-ttu-id="975b2-109">X.509 证书存储区的名称。</span><span class="sxs-lookup"><span data-stu-id="975b2-109">The name of the X.509 certificate store.</span></span> <span data-ttu-id="975b2-110">默认值为 "My"。</span><span class="sxs-lookup"><span data-stu-id="975b2-110">The default is "My".</span></span> <span data-ttu-id="975b2-111">可选。</span><span class="sxs-lookup"><span data-stu-id="975b2-111">Optional.</span></span>|  
|<span data-ttu-id="975b2-112">storeLocation</span><span class="sxs-lookup"><span data-stu-id="975b2-112">storeLocation</span></span>|<span data-ttu-id="975b2-113">一个 <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 值，该值指定 x.509 证书存储区的位置。</span><span class="sxs-lookup"><span data-stu-id="975b2-113">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="975b2-114">默认值为 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="975b2-114">The default value is "LocalMachine".</span></span> <span data-ttu-id="975b2-115">可选。</span><span class="sxs-lookup"><span data-stu-id="975b2-115">Optional.</span></span>|  
|<span data-ttu-id="975b2-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="975b2-116">x509FindType</span></span>|<span data-ttu-id="975b2-117">一个 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 值，该值指定要执行的搜索的类型。</span><span class="sxs-lookup"><span data-stu-id="975b2-117">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="975b2-118">默认值为 "FindBySubjectDistinguishedName"。</span><span class="sxs-lookup"><span data-stu-id="975b2-118">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="975b2-119">可选。</span><span class="sxs-lookup"><span data-stu-id="975b2-119">Optional.</span></span>|  
|<span data-ttu-id="975b2-120">findValue</span><span class="sxs-lookup"><span data-stu-id="975b2-120">findValue</span></span>|<span data-ttu-id="975b2-121">要在 X.509 证书存储区中搜索的值。</span><span class="sxs-lookup"><span data-stu-id="975b2-121">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="975b2-122">可选。</span><span class="sxs-lookup"><span data-stu-id="975b2-122">Optional.</span></span>|  
|<span data-ttu-id="975b2-123">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="975b2-123">isChainIncluded</span></span>|<span data-ttu-id="975b2-124">指定是否应通过使用证书链来执行验证。</span><span class="sxs-lookup"><span data-stu-id="975b2-124">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="975b2-125">默认值为 "true";验证是通过使用证书链来执行的。</span><span class="sxs-lookup"><span data-stu-id="975b2-125">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="975b2-126">可选。</span><span class="sxs-lookup"><span data-stu-id="975b2-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="975b2-127">子元素</span><span class="sxs-lookup"><span data-stu-id="975b2-127">Child Elements</span></span>  

 <span data-ttu-id="975b2-128">无</span><span class="sxs-lookup"><span data-stu-id="975b2-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="975b2-129">父元素</span><span class="sxs-lookup"><span data-stu-id="975b2-129">Parent Elements</span></span>  
  
|<span data-ttu-id="975b2-130">元素</span><span class="sxs-lookup"><span data-stu-id="975b2-130">Element</span></span>|<span data-ttu-id="975b2-131">描述</span><span class="sxs-lookup"><span data-stu-id="975b2-131">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="975b2-132">配置用于加密和解密令牌的证书。</span><span class="sxs-lookup"><span data-stu-id="975b2-132">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="975b2-133">备注</span><span class="sxs-lookup"><span data-stu-id="975b2-133">Remarks</span></span>  

 <span data-ttu-id="975b2-134">`<certificateReference>`元素指定用于在证书存储区中查找和验证 x.509 证书的设置。</span><span class="sxs-lookup"><span data-stu-id="975b2-134">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="975b2-135">指定为元素的子元素时 `<serviceCertificate>` ，它将指定用于加密和解密令牌的 x.509 证书的位置和验证设置。</span><span class="sxs-lookup"><span data-stu-id="975b2-135">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="975b2-136">`<certificateReference>`元素由 <xref:System.ServiceModel.Configuration.CertificateReferenceElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="975b2-136">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
