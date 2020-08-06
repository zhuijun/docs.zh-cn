---
title: 在序列化3时保留空格
description: 了解如何在使用 XElement 和 XDocument 类中的方法序列化 XML 树时控制空白。
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303408"
---
# <a name="preserving-white-space-while-serializing"></a>在序列化时保留空白
本主题描述在序列化 XML 树时如何控制空白。  
  
 一种常见方案是，读取缩进式 XML，创建不含任何空白符文本节点（即不保留空白符）的内存中 XML 树，对 XML 执行一些操作，再保存带缩进的 XML。 在序列化带格式的 XML 时，只保留 XML 树中有意义的空白。 这是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的默认行为。  
  
 另一个常见的情况是读取和修改已经有意缩进的 XML。 您可能不想以任何方式更改这种缩进。 若要在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中执行此操作，您要在加载或解析 XML 时保留空白，并在序列化 XML 时禁用格式设置。  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>用于序列化 XML 树的方法的空白符行为  
 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 类中的以下方法用于序列化 XML 树。 可以将 XML 树序列化为文件、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader>。 `ToString` 方法序列化为字符串。  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 如果方法不接受 <xref:System.Xml.Linq.SaveOptions> 作为参数，那么该方法将格式化（缩进）序列化的 XML。 在这种情况下，将丢弃 XML 树中所有无意义的空白。  
  
 如果方法接受 <xref:System.Xml.Linq.SaveOptions> 作为参数，那么您可以指定不格式化（缩进）序列化的 XML。 在这种情况下，将保留 XML 树中的所有空白。  
