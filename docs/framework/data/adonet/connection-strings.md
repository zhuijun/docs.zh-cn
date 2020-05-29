---
title: 连接字符串
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 3f56a487121757706ef6b4dfd11fcd761657431a
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202282"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="0f0cc-102">在 ADO.NET 中的连接字符串</span><span class="sxs-lookup"><span data-stu-id="0f0cc-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="0f0cc-103">连接字符串包含作为参数从数据提供程序传递到数据源的初始化信息。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="0f0cc-104">数据访问接口接收连接字符串作为属性的值 <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0f0cc-105">提供程序分析连接字符串，并确保语法正确，并且支持关键字。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="0f0cc-106">然后， <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> 方法将已分析的连接参数传递到数据源。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="0f0cc-107">数据源执行进一步的验证，并建立连接。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="0f0cc-108">连接字符串语法</span><span class="sxs-lookup"><span data-stu-id="0f0cc-108">Connection string syntax</span></span>

<span data-ttu-id="0f0cc-109">连接字符串是以分号分隔的键/值参数对列表：</span><span class="sxs-lookup"><span data-stu-id="0f0cc-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```csharp
keyword1=value; keyword2=value;
```

<span data-ttu-id="0f0cc-110">关键字不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="0f0cc-111">但是，值可能区分大小写，具体取决于数据源。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="0f0cc-112">关键字和值可以包含[空格字符](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="0f0cc-113">关键字和无引号值中会忽略前导空格和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="0f0cc-114">如果值包含分号、 [Unicode 控制字符](https://en.wikipedia.org/wiki/Unicode_control_characters)或前导或尾随空格，则必须用单引号或双引号将其引起来。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="0f0cc-115">例如：</span><span class="sxs-lookup"><span data-stu-id="0f0cc-115">For example:</span></span>

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="0f0cc-116">封闭字符不能出现在它所包含的值中。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="0f0cc-117">因此，包含单引号的值只能用双引号引起来，反之亦然：</span><span class="sxs-lookup"><span data-stu-id="0f0cc-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="0f0cc-118">还可以通过将其中两个字符一起使用来转义封闭字符：</span><span class="sxs-lookup"><span data-stu-id="0f0cc-118">You can also escape the enclosing character by using two of them together:</span></span>

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="0f0cc-119">引号本身以及等号不需要进行转义，因此以下连接字符串有效：</span><span class="sxs-lookup"><span data-stu-id="0f0cc-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="0f0cc-120">由于每个值都是在下一个分号或字符串末尾之前读取的，因此后一示例中的值为 `a=b=c` ，而最后的分号是可选的。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="0f0cc-121">所有连接字符串共享上述相同的基本语法。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="0f0cc-122">但所识别的关键字集取决于提供程序，但在以前的 Api （例如*ODBC*）中已经演变。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="0f0cc-123">用于*SQL Server* （）的 *.NET Framework*数据提供程序 `SqlClient` 支持来自较低版本 api 的多个关键字，但通常更灵活，并接受多个常用连接字符串关键字的同义词。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="0f0cc-124">键入错误会导致错误。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="0f0cc-125">例如， `Integrated Security=true` 是有效的，但 `IntegratedSecurity=true` 会导致错误。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="0f0cc-126">在运行时从未经验证用户输入手动构造的连接字符串容易受到字符串注入式攻击，并危害数据源的安全性。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="0f0cc-127">为了解决这些问题， *ADO.NET* 2.0 引入了每个 *.NET Framework*数据提供程序的[连接字符串生成器](connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="0f0cc-128">这些连接字符串生成器将参数作为强类型属性公开，并在将连接字符串发送到数据源之前验证连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-128">These connection string builders expose parameters as strongly typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0f0cc-129">本节内容</span><span class="sxs-lookup"><span data-stu-id="0f0cc-129">In This Section</span></span>

<span data-ttu-id="0f0cc-130">[连接字符串生成器](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="0f0cc-130">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="0f0cc-131">演示如何使用 `ConnectionStringBuilder` 类在运行时构造有效的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="0f0cc-132">[连接字符串和配置文件](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="0f0cc-132">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="0f0cc-133">演示如何在配置文件中存储和检索连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="0f0cc-134">[连接字符串语法](connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="0f0cc-134">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="0f0cc-135">描述如何为 `SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 配置提供程序专用的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="0f0cc-136">[保护连接信息](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="0f0cc-136">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="0f0cc-137">演示保护用于连接到数据源的信息的各项技术。</span><span class="sxs-lookup"><span data-stu-id="0f0cc-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f0cc-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f0cc-138">See also</span></span>

- [<span data-ttu-id="0f0cc-139">连接到数据源</span><span class="sxs-lookup"><span data-stu-id="0f0cc-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="0f0cc-140">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0f0cc-140">ADO.NET Overview</span></span>](ado-net-overview.md)
