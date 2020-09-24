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
ms.openlocfilehash: 0215851f83a13ee48547144f08c5c693ec2d90bf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149525"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="cd7e1-102">密码设置架构</span><span class="sxs-lookup"><span data-stu-id="cd7e1-102">Cryptography Settings Schema</span></span>

<span data-ttu-id="cd7e1-103">加密设置架构包含元素，这些元素指定如何将友好算法名称映射到实现加密算法的类。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="cd7e1-104">元素</span><span class="sxs-lookup"><span data-stu-id="cd7e1-104">Element</span></span>|<span data-ttu-id="cd7e1-105">描述</span><span class="sxs-lookup"><span data-stu-id="cd7e1-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="cd7e1-106">包含加密类的列表，这些类具有到元素中的友好名称的映射 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="cd7e1-107">包含一个加密类，该类具有到元素中的友好名称的映射 **\<nameEntry>** 。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="cd7e1-108">包含加密设置。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="cd7e1-109">包含类到友好名称的映射。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="cd7e1-110">**\<mscorlib>** 用于加密设置的元素</span><span class="sxs-lookup"><span data-stu-id="cd7e1-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="cd7e1-111">包含 **\<cryptographySettings>** 元素。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="cd7e1-112">将类名称映射到友好算法名称，允许一个类具有多个友好名称。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="cd7e1-113">将 ASN.1 对象标识符 (OID) 映射到友好名称。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="cd7e1-114">包含映射到类的 ASN.1 OID。</span><span class="sxs-lookup"><span data-stu-id="cd7e1-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd7e1-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd7e1-115">See also</span></span>

- [<span data-ttu-id="cd7e1-116">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="cd7e1-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cd7e1-117">加密服务</span><span class="sxs-lookup"><span data-stu-id="cd7e1-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
