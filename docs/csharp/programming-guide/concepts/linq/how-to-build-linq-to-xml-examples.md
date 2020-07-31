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
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="fe213-103">如何生成 LINQ to XML 示例 (C#)</span><span class="sxs-lookup"><span data-stu-id="fe213-103">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="fe213-104">本文档中的各代码段和示例使用多个命名空间中的类和类型。</span><span class="sxs-lookup"><span data-stu-id="fe213-104">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="fe213-105">在编译 C# 代码时，您需要提供相应的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="fe213-105">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe213-106">示例</span><span class="sxs-lookup"><span data-stu-id="fe213-106">Example</span></span>  
 <span data-ttu-id="fe213-107">下面的代码包含 C# 示例需要生成和运行的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="fe213-107">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="fe213-108">并非每个示例都需要所有 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="fe213-108">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe213-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="fe213-109">See also</span></span>

- [<span data-ttu-id="fe213-110">LINQ to XML 编程概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="fe213-110">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
