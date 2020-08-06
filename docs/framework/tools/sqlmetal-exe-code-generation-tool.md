---
title: SqlMetal.exe（代码生成工具）
description: 了解 SqlMetal.exe（代码生成工具）。 使用此工具为 .NET 的 LINQ to SQL 组件生成代码和映射。
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517043"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="24882-104">SqlMetal.exe（代码生成工具）</span><span class="sxs-lookup"><span data-stu-id="24882-104">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="24882-105">SqlMetal 命令行工具可为 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] 的 .NET Framework 组件生成代码和映射。</span><span class="sxs-lookup"><span data-stu-id="24882-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="24882-106">通过应用本主题后面出现的选项，可以指示 SqlMetal 执行若干种不同的操作，其中包括：</span><span class="sxs-lookup"><span data-stu-id="24882-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="24882-107">从数据库生成源代码和映射特性或映射文件。</span><span class="sxs-lookup"><span data-stu-id="24882-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="24882-108">从数据库生成供自定义使用的中间数据库标记语言 (.dbml) 文件。</span><span class="sxs-lookup"><span data-stu-id="24882-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="24882-109">从 .dbml 文件生成代码和映射特性或映射文件。</span><span class="sxs-lookup"><span data-stu-id="24882-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="24882-110">此工具会自动随 Visual Studio 一起安装。</span><span class="sxs-lookup"><span data-stu-id="24882-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="24882-111">默认情况下，此文件位于 `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin 下。</span><span class="sxs-lookup"><span data-stu-id="24882-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="24882-112">如果没有安装 Visual Studio，也可以通过下载 [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)获取 SQLMetal 文件。</span><span class="sxs-lookup"><span data-stu-id="24882-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24882-113">使用 Visual Studio 的开发人员还可以使用对象关系设计器生成实体类。</span><span class="sxs-lookup"><span data-stu-id="24882-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="24882-114">对于大型数据库，这种命令行方法具有很好的扩展性。</span><span class="sxs-lookup"><span data-stu-id="24882-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="24882-115">由于 SqlMetal 是一个命令行工具，因此可以在生成过程中使用它。</span><span class="sxs-lookup"><span data-stu-id="24882-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="24882-116">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="24882-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="24882-117">有关详细信息，请参阅[命令提示符](developer-command-prompt-for-vs.md)。在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="24882-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24882-118">语法</span><span class="sxs-lookup"><span data-stu-id="24882-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="24882-119">选项</span><span class="sxs-lookup"><span data-stu-id="24882-119">Options</span></span>  
 <span data-ttu-id="24882-120">要查看最新的选项列表，请在安装位置的命令提示符处键入 `sqlmetal /?` 。</span><span class="sxs-lookup"><span data-stu-id="24882-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="24882-121">**连接选项**</span><span class="sxs-lookup"><span data-stu-id="24882-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="24882-122">选项</span><span class="sxs-lookup"><span data-stu-id="24882-122">Option</span></span>|<span data-ttu-id="24882-123">说明</span><span class="sxs-lookup"><span data-stu-id="24882-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="24882-124">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="24882-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="24882-125">指定数据库服务器名称。</span><span class="sxs-lookup"><span data-stu-id="24882-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="24882-126">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="24882-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="24882-127">指定服务器上的数据库目录。</span><span class="sxs-lookup"><span data-stu-id="24882-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="24882-128">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="24882-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="24882-129">指定登录用户 ID。默认值：使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="24882-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="24882-130">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="24882-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="24882-131">指定登录密码。</span><span class="sxs-lookup"><span data-stu-id="24882-131">Specifies logon password.</span></span> <span data-ttu-id="24882-132">默认值：使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="24882-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="24882-133">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="24882-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="24882-134">指定数据库连接字符串。</span><span class="sxs-lookup"><span data-stu-id="24882-134">Specifies database connection string.</span></span> <span data-ttu-id="24882-135">不能与 **/server**、 **/database**、 **/user**或 **/password** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="24882-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="24882-136">不要在连接字符串中包含文件名，</span><span class="sxs-lookup"><span data-stu-id="24882-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="24882-137">而应将文件名作为输入文件添加到命令行中。</span><span class="sxs-lookup"><span data-stu-id="24882-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="24882-138">例如，下一行命令将“c:\northwnd.mdf”指定为输入文件： **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** 。</span><span class="sxs-lookup"><span data-stu-id="24882-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="24882-139">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="24882-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="24882-140">指定 SqlMetal 访问数据库时的超时值。</span><span class="sxs-lookup"><span data-stu-id="24882-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="24882-141">默认值：0（即没有时间限制）。</span><span class="sxs-lookup"><span data-stu-id="24882-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="24882-142">**提取选项**</span><span class="sxs-lookup"><span data-stu-id="24882-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="24882-143">选项</span><span class="sxs-lookup"><span data-stu-id="24882-143">Option</span></span>|<span data-ttu-id="24882-144">说明</span><span class="sxs-lookup"><span data-stu-id="24882-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="24882-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="24882-145">**/views**</span></span>|<span data-ttu-id="24882-146">提取数据库视图。</span><span class="sxs-lookup"><span data-stu-id="24882-146">Extracts database views.</span></span>|  
|<span data-ttu-id="24882-147">**/functions**</span><span class="sxs-lookup"><span data-stu-id="24882-147">**/functions**</span></span>|<span data-ttu-id="24882-148">提取数据库函数。</span><span class="sxs-lookup"><span data-stu-id="24882-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="24882-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="24882-149">**/sprocs**</span></span>|<span data-ttu-id="24882-150">提取存储过程。</span><span class="sxs-lookup"><span data-stu-id="24882-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="24882-151">**输出选项**</span><span class="sxs-lookup"><span data-stu-id="24882-151">**Output options**</span></span>  
  
|<span data-ttu-id="24882-152">选项</span><span class="sxs-lookup"><span data-stu-id="24882-152">Option</span></span>|<span data-ttu-id="24882-153">说明</span><span class="sxs-lookup"><span data-stu-id="24882-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="24882-154">/dbml [:file]</span><span class="sxs-lookup"><span data-stu-id="24882-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="24882-155">采用 .dbml 格式发送输出。</span><span class="sxs-lookup"><span data-stu-id="24882-155">Sends output as .dbml.</span></span> <span data-ttu-id="24882-156">不能与 **/map** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="24882-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="24882-157">/code [:file]</span><span class="sxs-lookup"><span data-stu-id="24882-157">**/code** *[:file]*</span></span>|<span data-ttu-id="24882-158">以源代码形式发送输出。</span><span class="sxs-lookup"><span data-stu-id="24882-158">Sends output as source code.</span></span> <span data-ttu-id="24882-159">不能与 **/dbml** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="24882-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="24882-160">/map [:file]</span><span class="sxs-lookup"><span data-stu-id="24882-160">**/map** *[:file]*</span></span>|<span data-ttu-id="24882-161">生成 XML 映射文件而不是特性。</span><span class="sxs-lookup"><span data-stu-id="24882-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="24882-162">不能与 **/dbml** 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="24882-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="24882-163">**杂项**</span><span class="sxs-lookup"><span data-stu-id="24882-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="24882-164">选项</span><span class="sxs-lookup"><span data-stu-id="24882-164">Option</span></span>|<span data-ttu-id="24882-165">说明</span><span class="sxs-lookup"><span data-stu-id="24882-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="24882-166">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="24882-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="24882-167">指定源代码语言。</span><span class="sxs-lookup"><span data-stu-id="24882-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="24882-168">有效的 *\<language>* ：vb、csharp。</span><span class="sxs-lookup"><span data-stu-id="24882-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="24882-169">默认值：从代码文件的扩展名派生。</span><span class="sxs-lookup"><span data-stu-id="24882-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="24882-170">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="24882-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="24882-171">为生成的代码指定命名空间。</span><span class="sxs-lookup"><span data-stu-id="24882-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="24882-172">默认值：无命名空间。</span><span class="sxs-lookup"><span data-stu-id="24882-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="24882-173">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="24882-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="24882-174">指定数据上下文类的名称。</span><span class="sxs-lookup"><span data-stu-id="24882-174">Specifies name of data context class.</span></span> <span data-ttu-id="24882-175">默认值：从数据库名称派生。</span><span class="sxs-lookup"><span data-stu-id="24882-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="24882-176">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="24882-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="24882-177">指定生成的代码中的实体类的基类。</span><span class="sxs-lookup"><span data-stu-id="24882-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="24882-178">默认值：实体没有基类。</span><span class="sxs-lookup"><span data-stu-id="24882-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="24882-179">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="24882-179">**/pluralize**</span></span>|<span data-ttu-id="24882-180">自动为类和成员名称应用复数或单数形式。</span><span class="sxs-lookup"><span data-stu-id="24882-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="24882-181">此选项仅在美国可用。英文版。</span><span class="sxs-lookup"><span data-stu-id="24882-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="24882-182">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="24882-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="24882-183">生成可序列化类。</span><span class="sxs-lookup"><span data-stu-id="24882-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="24882-184">有效的 *\<option>* ：无，单向。</span><span class="sxs-lookup"><span data-stu-id="24882-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="24882-185">默认值：无。</span><span class="sxs-lookup"><span data-stu-id="24882-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="24882-186">有关详细信息，请参阅[序列化](../data/adonet/sql/linq/serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="24882-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="24882-187">**输入文件**</span><span class="sxs-lookup"><span data-stu-id="24882-187">**Input File**</span></span>  
  
|<span data-ttu-id="24882-188">选项</span><span class="sxs-lookup"><span data-stu-id="24882-188">Option</span></span>|<span data-ttu-id="24882-189">说明</span><span class="sxs-lookup"><span data-stu-id="24882-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="24882-190">指定 SQL Server Express .mdf 文件、SQL Server Compact 3.5 .sdf 文件或 .dbml intermediate 文件。</span><span class="sxs-lookup"><span data-stu-id="24882-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24882-191">备注</span><span class="sxs-lookup"><span data-stu-id="24882-191">Remarks</span></span>  
 <span data-ttu-id="24882-192">SqlMetal 功能实际涉及两个步骤：</span><span class="sxs-lookup"><span data-stu-id="24882-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="24882-193">将数据库的元数据提取到一个 .dbml 文件中。</span><span class="sxs-lookup"><span data-stu-id="24882-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="24882-194">生成一个代码输出文件。</span><span class="sxs-lookup"><span data-stu-id="24882-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="24882-195">通过使用适当的命令行选项，可以生成 Visual Basic 或 C# 源代码，也可以生成 XML 映射文件。</span><span class="sxs-lookup"><span data-stu-id="24882-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="24882-196">若要从 .mdf 文件中提取元数据，必须在所有其他选项后指定 .mdf 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="24882-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="24882-197">如果没有指定 **/server** ，则假定为 **localhost/sqlexpress** 。</span><span class="sxs-lookup"><span data-stu-id="24882-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="24882-198">如果下述一个或多个条件为 true，则 Microsoft SQL Server 2005 会引发异常：</span><span class="sxs-lookup"><span data-stu-id="24882-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="24882-199">SqlMetal 尝试提取进行自我调用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="24882-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="24882-200">存储过程、函数或视图的嵌套级别超过 32。</span><span class="sxs-lookup"><span data-stu-id="24882-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="24882-201">SqlMetal 将捕获此异常并将其报告为警告。</span><span class="sxs-lookup"><span data-stu-id="24882-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="24882-202">若要指定一个输入文件名，请将该名称作为输入文件添加到命令行。</span><span class="sxs-lookup"><span data-stu-id="24882-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="24882-203">不支持在连接字符串中包含文件名（使用 **/conn** 选项）。</span><span class="sxs-lookup"><span data-stu-id="24882-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="24882-204">示例</span><span class="sxs-lookup"><span data-stu-id="24882-204">Examples</span></span>  
 <span data-ttu-id="24882-205">生成一个包含提取的 SQL 元数据的 .dbml 文件：</span><span class="sxs-lookup"><span data-stu-id="24882-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="24882-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="24882-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="24882-207">使用 SQL Server Express 生成一个包含从 .mdf 文件中提取的 SQL 元数据的 .dbml 文件：</span><span class="sxs-lookup"><span data-stu-id="24882-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="24882-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="24882-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="24882-209">生成一个包含从 SQL Server Express 中提取的 SQL 元数据的 .dbml 文件：</span><span class="sxs-lookup"><span data-stu-id="24882-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="24882-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="24882-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="24882-211">从 .dbml 元数据文件生成源代码：</span><span class="sxs-lookup"><span data-stu-id="24882-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="24882-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="24882-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="24882-213">直接从 SQL 元数据生成源代码：</span><span class="sxs-lookup"><span data-stu-id="24882-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="24882-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="24882-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24882-215">如果对 Northwind 示例数据库应用 **/pluralize** 选项，请注意以下行为。</span><span class="sxs-lookup"><span data-stu-id="24882-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="24882-216">如果 SqlMetal 为表创建了行类型的名称，表名将采用单数形式。</span><span class="sxs-lookup"><span data-stu-id="24882-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="24882-217">如果它为表创建了 <xref:System.Data.Linq.DataContext> 属性，则表名将采用复数形式。</span><span class="sxs-lookup"><span data-stu-id="24882-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="24882-218">巧合的是，Northwind 示例数据库中的表名已采用复数形式。</span><span class="sxs-lookup"><span data-stu-id="24882-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="24882-219">因此，你将看不到这种效果。</span><span class="sxs-lookup"><span data-stu-id="24882-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="24882-220">尽管数据库表普遍命名为单数形式，但在 .NET 中，将集合命名为复数形式也是一种常见的做法。</span><span class="sxs-lookup"><span data-stu-id="24882-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24882-221">请参阅</span><span class="sxs-lookup"><span data-stu-id="24882-221">See also</span></span>

- [<span data-ttu-id="24882-222">如何：在 Visual Basic 或 C# 中生成对象模型</span><span class="sxs-lookup"><span data-stu-id="24882-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="24882-223">LINQ to SQL 中的代码生成</span><span class="sxs-lookup"><span data-stu-id="24882-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="24882-224">外部映射</span><span class="sxs-lookup"><span data-stu-id="24882-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
