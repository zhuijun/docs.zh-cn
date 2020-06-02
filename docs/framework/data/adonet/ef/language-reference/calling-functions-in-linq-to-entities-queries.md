---
title: 在 LINQ to Entities 查询中调用函数
description: 使用这些文章可以查看 EntityFunctions 和 SqlFunctions 类如何作为实体框架的一部分，提供对规范和数据库函数的访问权限。
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286852"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>在 LINQ to Entities 查询中调用函数
本节中的主题说明如何调用 LINQ to Entities 查询中的函数。  
  
 <xref:System.Data.Objects.EntityFunctions> 和 <xref:System.Data.Objects.SqlClient.SqlFunctions> 类提供了对作为实体框架的一部分的规范函数和数据库函数的访问功能。 有关详细信息，请参阅[如何：调用规范函数](how-to-call-canonical-functions.md)和[如何：调用数据库函数](how-to-call-database-functions.md)。  
  
 调用自定义函数的过程需要三个基本步骤：  
  
1. 在概念模型中定义函数或在存储模型中声明函数。  
  
2. 将方法添加到应用程序并将其映射到具有 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 的模型中的函数。  
  
3. 在 LINQ to Entities 查询中调用该函数。  
  
 有关更多信息，请参见本节中的各主题。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：调用规范函数](how-to-call-canonical-functions.md)  
  
 [如何：调用数据库函数](how-to-call-database-functions.md)  
  
 [如何：调用自定义数据库函数](how-to-call-custom-database-functions.md)  
  
 [如何：在查询中调用模型定义的函数](how-to-call-model-defined-functions-in-queries.md)  
  
 [如何：调用模型定义的函数作为对象方法](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>另请参阅

- [LINQ to Entities 中的查询](queries-in-linq-to-entities.md)
- [规范函数](canonical-functions.md)
- [.edmx 文件概述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [如何：在概念模型中定义自定义函数](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
