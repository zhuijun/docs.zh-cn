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
# <a name="configuring-cryptography-classes"></a>配置加密类
Windows SDK 允许计算机管理员配置 .NET Framework 和适当编写的应用程序使用的默认加密算法和算法实现。  例如，具有自己的加密算法实现的企业可以使该实现成为默认实现，而不是在 Windows SDK 中提供的实现。 尽管使用加密的托管应用程序始终可以选择显式绑定到特定的实现，但建议使用加密配置系统来创建加密对象。  
  
## <a name="in-this-section"></a>本节内容  
 [将算法名称映射到加密类](map-algorithm-names-to-cryptography-classes.md)  
 介绍如何将算法名称映射到加密类。  
  
 [将对象标识符映射到加密算法](map-object-identifiers-to-cryptography-algorithms.md)  
 介绍如何将对象标识符映射到加密算法。  
  
## <a name="related-sections"></a>相关章节  
 [加密服务](../../standard/security/cryptographic-services.md)  
 概述 Windows SDK 提供的加密服务。  
  
 [密码设置架构](./file-schema/cryptography/index.md)  
 描述将友好算法名映射到实现密码算法的类的元素。
