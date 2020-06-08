---
title: 复制现有节点
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289208"
---
# <a name="copy-existing-nodes"></a>复制现有节点
XML 文档对象模型 (DOM) 包含许多可用于选择节点的方法和属性，如 SelectSingleNode  、ChildNodes[int i]  、Attributes[int i]  。 选择节点后，可以使用适用于特定节点类型的插入方法之一将该节点插入到树中。 将节点插入到树中的唯一限制是在插入节点后文档的格式仍必须是正确的。 将现有节点插入到 DOM 树中时，该节点从其原始位置移除并添加到它的目标位置。  
  
## <a name="see-also"></a>请参阅

- [XML 文档对象模型 (DOM)](xml-document-object-model-dom.md)
