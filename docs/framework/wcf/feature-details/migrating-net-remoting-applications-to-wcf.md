---
title: 将 .NET 远程处理应用程序迁移到 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: d12583904e4a025a8de1103f0fb48f4656d6855e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598770"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>将 .NET 远程处理应用程序迁移到 WCF
**本主题特定于旧技术，保留该技术是为了向后兼容现有应用程序，不建议用于新的开发。现在应使用 WCF 开发分布式应用程序。**  
  
 可以通过两种方法来利用 WCF 和现有的 .NET 远程处理应用程序：集成和迁移。 集成使你能够并行运行 .NET 远程处理2.0 和 WCF，使你可以同时在这两种技术上公开相同的业务对象，而无需修改现有的 .NET 远程处理2.0 代码。 集成要求在 .NET Framework 2.0 或更高版本上运行。 如果你想要利用 WCF 功能，并且不需要与远程处理2.0 系统之间的网络兼容性，则可以将整个服务迁移到 WCF。 从 .NET 远程处理2.0 迁移到 WCF 需要更改远程对象的接口及其配置设置。 [从远程处理到 Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80))中介绍了这两个主题。  
  
## <a name="see-also"></a>另请参阅

- [概念性概述](../conceptual-overview.md)
