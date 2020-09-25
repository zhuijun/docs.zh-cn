---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 8476600769b6099bb885566de4c908c78a2dbbda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201365"
---
# \<certificateValidator>

<span data-ttu-id="16929-101">指定证书验证的自定义类型。</span><span class="sxs-lookup"><span data-stu-id="16929-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="16929-102">仅当 `certificateValidationMode` 元素的属性 [\<certificateValidation>](certificatevalidation.md) 设置为 "Custom" 时才使用此类型。</span><span class="sxs-lookup"><span data-stu-id="16929-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="16929-103">语法</span><span class="sxs-lookup"><span data-stu-id="16929-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16929-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="16929-104">Attributes and Elements</span></span>  

 <span data-ttu-id="16929-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="16929-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16929-106">特性</span><span class="sxs-lookup"><span data-stu-id="16929-106">Attributes</span></span>  
  
|<span data-ttu-id="16929-107">属性</span><span class="sxs-lookup"><span data-stu-id="16929-107">Attribute</span></span>|<span data-ttu-id="16929-108">说明</span><span class="sxs-lookup"><span data-stu-id="16929-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16929-109">type</span><span class="sxs-lookup"><span data-stu-id="16929-109">type</span></span>|<span data-ttu-id="16929-110">指定从类派生的自定义类型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="16929-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="16929-111">将 `certificateValidationMode` 元素的属性设置 [\<certificateValidation>](certificatevalidation.md) 为 "自定义" 可使用此类型。</span><span class="sxs-lookup"><span data-stu-id="16929-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="16929-112">有关如何指定属性的详细信息 `type` ，请参阅 [自定义类型引用](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="16929-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="16929-113">可选。</span><span class="sxs-lookup"><span data-stu-id="16929-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16929-114">子元素</span><span class="sxs-lookup"><span data-stu-id="16929-114">Child Elements</span></span>  

 <span data-ttu-id="16929-115">无</span><span class="sxs-lookup"><span data-stu-id="16929-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16929-116">父元素</span><span class="sxs-lookup"><span data-stu-id="16929-116">Parent Elements</span></span>  
  
|<span data-ttu-id="16929-117">元素</span><span class="sxs-lookup"><span data-stu-id="16929-117">Element</span></span>|<span data-ttu-id="16929-118">描述</span><span class="sxs-lookup"><span data-stu-id="16929-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="16929-119">控制标记处理程序用于验证证书的设置。</span><span class="sxs-lookup"><span data-stu-id="16929-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16929-120">示例</span><span class="sxs-lookup"><span data-stu-id="16929-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
