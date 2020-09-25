---
title: 可以为 null 的结构化类型 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: fc2230401ef98c005ab52a845de37482c0dcf698
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202258"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="5f500-102">可以为 null 的结构化类型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5f500-102">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="5f500-103">结构化类型的 `null` 实例是不存在的实例。</span><span class="sxs-lookup"><span data-stu-id="5f500-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="5f500-104">这不同于其中所有属性都具有 `null` 值的现有实例。</span><span class="sxs-lookup"><span data-stu-id="5f500-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="5f500-105">本主题介绍可以为 Null 的结构化类型，包括哪些类型可以为 null 以及哪些代码模式会产生可以为 Null 的结构化类型的 `null` 实例。</span><span class="sxs-lookup"><span data-stu-id="5f500-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="5f500-106">可以为 Null 的结构化类型的种类</span><span class="sxs-lookup"><span data-stu-id="5f500-106">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="5f500-107">有三种可以为 Null 的结构化类型：</span><span class="sxs-lookup"><span data-stu-id="5f500-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="5f500-108">行类型。</span><span class="sxs-lookup"><span data-stu-id="5f500-108">Row types.</span></span>  
  
- <span data-ttu-id="5f500-109">复杂类型。</span><span class="sxs-lookup"><span data-stu-id="5f500-109">Complex types.</span></span>  
  
- <span data-ttu-id="5f500-110">实体类型。</span><span class="sxs-lookup"><span data-stu-id="5f500-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="5f500-111">能够产生结构化类型的 null 实例的代码模式</span><span class="sxs-lookup"><span data-stu-id="5f500-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="5f500-112">以下方案会产生 `null` 实例：</span><span class="sxs-lookup"><span data-stu-id="5f500-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="5f500-113">将 `null` 说明为结构化类型：</span><span class="sxs-lookup"><span data-stu-id="5f500-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="5f500-114">将基类型向上转换为派生类型：</span><span class="sxs-lookup"><span data-stu-id="5f500-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="5f500-115">对 false 条件进行外部联接：</span><span class="sxs-lookup"><span data-stu-id="5f500-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="5f500-116">--或</span><span class="sxs-lookup"><span data-stu-id="5f500-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="5f500-117">--或</span><span class="sxs-lookup"><span data-stu-id="5f500-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="5f500-118">取消 `null` 引用的引用：</span><span class="sxs-lookup"><span data-stu-id="5f500-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="5f500-119">从空集合获取 ANYELEMENT：</span><span class="sxs-lookup"><span data-stu-id="5f500-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="5f500-120">检查结构化类型实例是否为 `null`：</span><span class="sxs-lookup"><span data-stu-id="5f500-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5f500-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f500-121">See also</span></span>

- [<span data-ttu-id="5f500-122">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="5f500-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
