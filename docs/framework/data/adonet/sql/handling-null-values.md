---
title: 处理 Null 值
description: 了解 SQL Server 的 .NET Framework 数据提供程序如何处理 null，并了解 null 和 SqlBoolean、三值逻辑，并分配 null 值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: a4d086d81f1c2c959780366cfeb59f2d265bc40c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286450"
---
# <a name="handling-null-values"></a><span data-ttu-id="f000c-103">处理 Null 值</span><span class="sxs-lookup"><span data-stu-id="f000c-103">Handling Null Values</span></span>
<span data-ttu-id="f000c-104">如果列中的值未知或缺失，则使用关系数据库中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-104">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="f000c-105">null 既不是空字符串（对于字符或日期/时间数据类型），也不是零值（对于数值数据类型）。</span><span class="sxs-lookup"><span data-stu-id="f000c-105">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="f000c-106">ANSI SQL-92 规范规定，所有数据类型的 null 值必须相同，以便一致地处理所有 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-106">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="f000c-107"><xref:System.Data.SqlTypes> 命名空间通过实现 <xref:System.Data.SqlTypes.INullable> 接口提供 null 语义。</span><span class="sxs-lookup"><span data-stu-id="f000c-107">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="f000c-108"><xref:System.Data.SqlTypes> 中的每个数据类型都有其自己的 `IsNull` 属性和可分配给该数据类型的实例的 `Null` 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-108">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f000c-109">.NET Framework 版本2.0 引入了对可以为 null 的值类型的支持，这些类型使程序员能够扩展值类型来表示基础类型的所有值。</span><span class="sxs-lookup"><span data-stu-id="f000c-109">The .NET Framework version 2.0 introduced support for nullable value types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="f000c-110">这些 CLR 可以为 null 的值类型表示结构的实例 <xref:System.Nullable> 。</span><span class="sxs-lookup"><span data-stu-id="f000c-110">These CLR nullable value types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="f000c-111">当对值类型进行装箱和取消装箱时，此功能特别有用，从而增强了与对象类型的兼容性。</span><span class="sxs-lookup"><span data-stu-id="f000c-111">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="f000c-112">CLR 可以为 null 的值类型不用于存储数据库 null 值，因为 ANSI SQL null 的行为与 `null` 引用（或 `Nothing` 在 Visual Basic 中）的行为方式不同。</span><span class="sxs-lookup"><span data-stu-id="f000c-112">CLR nullable value types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="f000c-113">若要使用数据库 ANSI SQL null 值，请使用 <xref:System.Data.SqlTypes> null 值，而不是 <xref:System.Nullable>。</span><span class="sxs-lookup"><span data-stu-id="f000c-113">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="f000c-114">若要详细了解如何在 Visual Basic 中使用 CLR 值可以为 null 的类型，请参阅[可以为 null 的值类型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)，对于 c #，请参阅[可以为 null](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="f000c-114">For more information on working with CLR value nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="f000c-115">空和三值逻辑</span><span class="sxs-lookup"><span data-stu-id="f000c-115">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="f000c-116">允许列定义中的 null 值在应用程序中引入了三值逻辑。</span><span class="sxs-lookup"><span data-stu-id="f000c-116">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="f000c-117">比较的计算结果可以为以下三种情况之一：</span><span class="sxs-lookup"><span data-stu-id="f000c-117">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="f000c-118">True</span><span class="sxs-lookup"><span data-stu-id="f000c-118">True</span></span>  
  
- <span data-ttu-id="f000c-119">False</span><span class="sxs-lookup"><span data-stu-id="f000c-119">False</span></span>  
  
- <span data-ttu-id="f000c-120">Unknown</span><span class="sxs-lookup"><span data-stu-id="f000c-120">Unknown</span></span>  
  
 <span data-ttu-id="f000c-121">由于 null 被视为未知，因此两个 null 值之间的比较不被视为相等。</span><span class="sxs-lookup"><span data-stu-id="f000c-121">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="f000c-122">在使用算术运算符的表达式中，如果有任何操作数为 null，则结果也为 null。</span><span class="sxs-lookup"><span data-stu-id="f000c-122">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="f000c-123">null 和 SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="f000c-123">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="f000c-124">任何 <xref:System.Data.SqlTypes> 之间的比较将返回一个 <xref:System.Data.SqlTypes.SqlBoolean>。</span><span class="sxs-lookup"><span data-stu-id="f000c-124">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="f000c-125">每个 `SqlType` 的 `IsNull` 函数都返回 <xref:System.Data.SqlTypes.SqlBoolean>，并可用于检查 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-125">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="f000c-126">以下真值表显示了 AND、OR 和 NOT 运算符在存在 null 值的情况下的工作方式。</span><span class="sxs-lookup"><span data-stu-id="f000c-126">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="f000c-127">（T=true、F=false 以及 U=未知或 null。）</span><span class="sxs-lookup"><span data-stu-id="f000c-127">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="f000c-128">![真值表](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="f000c-128">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="f000c-129">理解 ANSI_NULLS 选项</span><span class="sxs-lookup"><span data-stu-id="f000c-129">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="f000c-130"><xref:System.Data.SqlTypes> 提供与在 SQL Server 中设置 ANSI_NULLS 选项相同的语义。</span><span class="sxs-lookup"><span data-stu-id="f000c-130"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="f000c-131">如果任何操作数或参数为 null （属性除外），则所有算术运算符（+、-、 \* 、/、%）、位运算符（~、&、 \| ）和大多数函数都返回 null `IsNull` 。</span><span class="sxs-lookup"><span data-stu-id="f000c-131">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="f000c-132">ANSI SQL-92 标准不支持 WHERE 子句中的 columnName = NULL\*\*。</span><span class="sxs-lookup"><span data-stu-id="f000c-132">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="f000c-133">在 SQL Server 中，ANSI_NULLS 选项既控制数据库中的默认为 Null 性，又控制对 null 值的比较的求值。</span><span class="sxs-lookup"><span data-stu-id="f000c-133">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="f000c-134">如果打开 ANSI_NULLS（默认值），则在测试 null 值时，必须在表达式中使用 IS NULL 运算符。</span><span class="sxs-lookup"><span data-stu-id="f000c-134">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="f000c-135">例如，当 ANSI_NULLS 为开启状态时，以下比较总是生成未知：</span><span class="sxs-lookup"><span data-stu-id="f000c-135">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="f000c-136">比较包含 null 值的变量也会生成未知：</span><span class="sxs-lookup"><span data-stu-id="f000c-136">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="f000c-137">使用 IS NULL 或 IS NOT NULL 谓词测试 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-137">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="f000c-138">这将增加 WHERE 子句的复杂性。</span><span class="sxs-lookup"><span data-stu-id="f000c-138">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="f000c-139">例如，AdventureWorks Customer 表中的 TerritoryID 列允许 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-139">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="f000c-140">如果 SELECT 语句不仅用于测试其他值，还用于测试 NULL 值，则该语句必须包括 IS NULL 谓词：</span><span class="sxs-lookup"><span data-stu-id="f000c-140">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="f000c-141">如果在 SQL Server 将 ANSI_NULLS 设置为关闭，则可以创建使用相等运算符与 null 进行比较的表达式。</span><span class="sxs-lookup"><span data-stu-id="f000c-141">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="f000c-142">但是，不能阻止不同的连接为该连接设置 null 选项。</span><span class="sxs-lookup"><span data-stu-id="f000c-142">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="f000c-143">使用 IS NULL 测试 null 值始终有效，而不考虑连接的 ANSI_NULLS 设置。</span><span class="sxs-lookup"><span data-stu-id="f000c-143">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="f000c-144">不支持在 `DataSet` 中将 ANSI_NULLS 设置为关闭，这始终遵循 ANSI SQL-92 标准来处理 <xref:System.Data.SqlTypes> 中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-144">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="f000c-145">赋予 Null 值</span><span class="sxs-lookup"><span data-stu-id="f000c-145">Assigning Null Values</span></span>  
 <span data-ttu-id="f000c-146">null 值为特殊值，其存储和赋值语义在不同类型系统和存储系统之间是不同的。</span><span class="sxs-lookup"><span data-stu-id="f000c-146">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="f000c-147">`Dataset` 旨在与不同的类型和存储系统一起使用。</span><span class="sxs-lookup"><span data-stu-id="f000c-147">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="f000c-148">本部分介绍 null 语义，该语义用于将 null 值分配给不同类型系统中 <xref:System.Data.DataRow> 的 <xref:System.Data.DataColumn>。</span><span class="sxs-lookup"><span data-stu-id="f000c-148">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="f000c-149">该赋值对于任何类型的 `DataColumn` 都有效。</span><span class="sxs-lookup"><span data-stu-id="f000c-149">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="f000c-150">如果类型实现 `INullable`，则会将 `DBNull.Value` 强制转换为相应的强类型 Null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-150">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="f000c-151">所有 <xref:System.Data.SqlTypes> 数据类型都实现 `INullable`。</span><span class="sxs-lookup"><span data-stu-id="f000c-151">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="f000c-152">如果可使用隐式强制转换运算符将强类型的 null 值转换为列的数据类型，则应执行赋值。</span><span class="sxs-lookup"><span data-stu-id="f000c-152">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="f000c-153">否则，将引发无效强制转换异常。</span><span class="sxs-lookup"><span data-stu-id="f000c-153">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="f000c-154">如果“null”是给定 `DataColumn` 数据类型的合法值，则会将其强制转换为与 `INullable` 类型 (`SqlType.Null`) 关联的相应 `DbNull.Value` 或 `Null`</span><span class="sxs-lookup"><span data-stu-id="f000c-154">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="f000c-155">对于 UDT 列，将始终基于与 `DataColumn` 关联的类型存储 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-155">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="f000c-156">请考虑与 `DataColumn` 关联的 UDT 的情况，它不实现 `INullable`，但其子类会实现。</span><span class="sxs-lookup"><span data-stu-id="f000c-156">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="f000c-157">在这种情况下，如果分配了与派生类关联的强类型 null 值，则会将其存储为非类型化的 `DbNull.Value`，因为 null 存储始终与 DataColumn 的数据类型一致。</span><span class="sxs-lookup"><span data-stu-id="f000c-157">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f000c-158">`DataSet` 当前不支持 `Nullable<T>` 或 <xref:System.Nullable> 结构。</span><span class="sxs-lookup"><span data-stu-id="f000c-158">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="f000c-159">多列（行）赋值</span><span class="sxs-lookup"><span data-stu-id="f000c-159">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="f000c-160">`DataTable.Add`、`DataTable.LoadDataRow` 或接受映射到行的 <xref:System.Data.DataRow.ItemArray%2A> 的其他 API，请将“null”映射到 DataColumn 的默认值。</span><span class="sxs-lookup"><span data-stu-id="f000c-160">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="f000c-161">如果数组中的对象包含 `DbNull.Value` 或其强类型对应项，则将应用上述规则。</span><span class="sxs-lookup"><span data-stu-id="f000c-161">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="f000c-162">此外，以下规则适用于 `DataRow.["columnName"]` null 赋值的实例：</span><span class="sxs-lookup"><span data-stu-id="f000c-162">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="f000c-163">对于所有列，默认值为 `DbNull.Value`，但强类型 NULL 列除外，强类型 NULL 列的默认值是相应的强类型 NULL 值\*\*。</span><span class="sxs-lookup"><span data-stu-id="f000c-163">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="f000c-164">在序列化为 XML 文件时，不会写出 null 值（如在“xsi:nil”中）。</span><span class="sxs-lookup"><span data-stu-id="f000c-164">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="f000c-165">在序列化为 XML 时，始终写出所有非 null 值（包括默认值）。</span><span class="sxs-lookup"><span data-stu-id="f000c-165">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="f000c-166">这不同于 XSD/XML 语义，其中 null 值 (xsi:nil) 是显式的，而默认值是隐式的（如果在 XML 中不存在，验证分析器可以从关联的 XSD 架构中获取它）。</span><span class="sxs-lookup"><span data-stu-id="f000c-166">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="f000c-167">`DataTable` 则是相反：null 值是隐式的，而默认值是显式的。</span><span class="sxs-lookup"><span data-stu-id="f000c-167">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="f000c-168">从 XML 输入读取的行的所有缺少列值都将分配为 NULL。</span><span class="sxs-lookup"><span data-stu-id="f000c-168">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="f000c-169">将向使用 <xref:System.Data.DataTable.NewRow%2A> 或类似方法创建的行分配 DataColumn 的默认值。</span><span class="sxs-lookup"><span data-stu-id="f000c-169">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="f000c-170"><xref:System.Data.DataRow.IsNull%2A> 方法为 `DbNull.Value` 和 `INullable.Null` 返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="f000c-170">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="f000c-171">赋予 Null 值</span><span class="sxs-lookup"><span data-stu-id="f000c-171">Assigning Null Values</span></span>  
 <span data-ttu-id="f000c-172">任何 <xref:System.Data.SqlTypes> 实例的默认值为 null。</span><span class="sxs-lookup"><span data-stu-id="f000c-172">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="f000c-173"><xref:System.Data.SqlTypes> 中的 null 值为特定类型，不能由单个值表示，如 `DbNull`。</span><span class="sxs-lookup"><span data-stu-id="f000c-173">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="f000c-174">使用 `IsNull` 属性检查 null 值。</span><span class="sxs-lookup"><span data-stu-id="f000c-174">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="f000c-175">null 值可以分配给 <xref:System.Data.DataColumn>，如下面的代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f000c-175">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="f000c-176">可以直接将 null 值分配给 `SqlTypes` 变量，而不会触发异常。</span><span class="sxs-lookup"><span data-stu-id="f000c-176">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f000c-177">示例</span><span class="sxs-lookup"><span data-stu-id="f000c-177">Example</span></span>  
 <span data-ttu-id="f000c-178">下面的代码示例创建一个 <xref:System.Data.DataTable>，其中两列定义为 <xref:System.Data.SqlTypes.SqlInt32> 和 <xref:System.Data.SqlTypes.SqlString>。</span><span class="sxs-lookup"><span data-stu-id="f000c-178">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="f000c-179">该代码将添加一行已知值、一行 null 值，然后循环访问 <xref:System.Data.DataTable>，进而将值分配给变量并在控制台窗口中显示输出。</span><span class="sxs-lookup"><span data-stu-id="f000c-179">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="f000c-180">此示例显示以下结果：</span><span class="sxs-lookup"><span data-stu-id="f000c-180">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="f000c-181">将空值与 SqlTypes 和 CLR 类型进行比较</span><span class="sxs-lookup"><span data-stu-id="f000c-181">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="f000c-182">比较 null 值时，务必要了解 `Equals` 方法计算 <xref:System.Data.SqlTypes> 中 null 值的方式与它在 CLR 类型中的工作方式相比之间的差异。</span><span class="sxs-lookup"><span data-stu-id="f000c-182">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="f000c-183">所有 <xref:System.Data.SqlTypes>`Equals` 方法都使用数据库语义计算 null 值：如果两个值中的一个或两个都为 null，则比较结果为 null。</span><span class="sxs-lookup"><span data-stu-id="f000c-183">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="f000c-184">另一方面，如果两个 <xref:System.Data.SqlTypes> 都为 null，则对两者使用 CLR `Equals` 方法将生成 true。</span><span class="sxs-lookup"><span data-stu-id="f000c-184">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="f000c-185">这反映了使用实例方法（如 CLR `String.Equals` 方法）和使用静态/共享方法 (`SqlString.Equals`) 的差异。</span><span class="sxs-lookup"><span data-stu-id="f000c-185">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="f000c-186">下面的示例演示了 `SqlString.Equals` 方法与 `String.Equals` 方法在分别传递一对 null 值和一对空字符串时的结果差异。</span><span class="sxs-lookup"><span data-stu-id="f000c-186">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="f000c-187">此代码将产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="f000c-187">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a><span data-ttu-id="f000c-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f000c-188">See also</span></span>

- [<span data-ttu-id="f000c-189">SQL Server 数据类型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f000c-189">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="f000c-190">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="f000c-190">ADO.NET Overview</span></span>](../ado-net-overview.md)
