---
title: 如何生成 LINQ to XML 示例 (C#)
description: 提供编译 C# 所需的适当 using 指令以运行提供的代码段和 LINQ to XML 的示例。
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: f54944dcb68e1fd7d00f37c9c5381f345efc820e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103588"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a>如何生成 LINQ to XML 示例 (C#)
本文档中的各代码段和示例使用多个命名空间中的类和类型。 在编译 C# 代码时，您需要提供相应的 `using` 指令。  
  
## <a name="example"></a>示例  
 下面的代码包含 C# 示例需要生成和运行的 `using` 指令。 并非每个示例都需要所有 `using` 指令。  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 编程概述 (C#)](./linq-to-xml-overview.md)
