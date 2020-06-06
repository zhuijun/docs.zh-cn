---
title: 配置加密类
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927773"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="67972-102">配置加密类</span><span class="sxs-lookup"><span data-stu-id="67972-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="67972-103">Windows SDK 允许计算机管理员配置 .NET Framework 和适当编写的应用程序使用的默认加密算法和算法实现。</span><span class="sxs-lookup"><span data-stu-id="67972-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="67972-104">例如，具有自己的加密算法实现的企业可以使该实现成为默认实现，而不是在 Windows SDK 中提供的实现。</span><span class="sxs-lookup"><span data-stu-id="67972-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="67972-105">尽管使用加密的托管应用程序始终可以选择显式绑定到特定的实现，但建议使用加密配置系统来创建加密对象。</span><span class="sxs-lookup"><span data-stu-id="67972-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67972-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="67972-106">In This Section</span></span>  
 [<span data-ttu-id="67972-107">将算法名称映射到加密类</span><span class="sxs-lookup"><span data-stu-id="67972-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="67972-108">介绍如何将算法名称映射到加密类。</span><span class="sxs-lookup"><span data-stu-id="67972-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="67972-109">将对象标识符映射到加密算法</span><span class="sxs-lookup"><span data-stu-id="67972-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="67972-110">介绍如何将对象标识符映射到加密算法。</span><span class="sxs-lookup"><span data-stu-id="67972-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67972-111">相关章节</span><span class="sxs-lookup"><span data-stu-id="67972-111">Related Sections</span></span>  
 [<span data-ttu-id="67972-112">加密服务</span><span class="sxs-lookup"><span data-stu-id="67972-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="67972-113">概述 Windows SDK 提供的加密服务。</span><span class="sxs-lookup"><span data-stu-id="67972-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="67972-114">密码设置架构</span><span class="sxs-lookup"><span data-stu-id="67972-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="67972-115">描述将友好算法名映射到实现密码算法的类的元素。</span><span class="sxs-lookup"><span data-stu-id="67972-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
