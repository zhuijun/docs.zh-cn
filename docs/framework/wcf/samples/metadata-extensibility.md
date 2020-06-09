---
title: 元数据可扩展性
ms.date: 03/30/2017
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
ms.openlocfilehash: 1e8e7f511b38cf3326b9abbca57df769317a26a4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584618"
---
# <a name="metadata-extensibility"></a>元数据可扩展性
本节包含演示自定义元数据的示例。  
  
## <a name="in-this-section"></a>本节内容  
 [自定义安全元数据终结点](custom-secure-metadata-endpoint.md)  
 演示如何实现一个具有安全元数据终结点（该终结点使用非元数据交换绑定）的服务，以及如何配置使用的元[数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)或客户端从这类元数据终结点获取元数据。  
  
 [自定义 WSDL 发布](custom-wsdl-publication.md)  
 演示如何在自定义 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 特性上实现 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>，以便在其他功能中将该特性的属性导出为 WSDL 批注。
