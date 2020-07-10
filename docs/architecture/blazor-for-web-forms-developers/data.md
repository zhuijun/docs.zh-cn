---
title: 数据访问和管理
description: 了解如何访问和处理 ASP.NET Web 窗体和中的数据 Blazor 。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/26/2020
ms.openlocfilehash: 4bf9bee21ce1db828dbe0aeb156d5e15cae4f703
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173299"
---
# <a name="work-with-data"></a><span data-ttu-id="77dd9-103">处理数据</span><span class="sxs-lookup"><span data-stu-id="77dd9-103">Work with data</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="77dd9-104">数据访问是 ASP.NET Web 窗体应用的主干。</span><span class="sxs-lookup"><span data-stu-id="77dd9-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="77dd9-105">如果要为 web 构建窗体，该数据会发生什么情况呢？</span><span class="sxs-lookup"><span data-stu-id="77dd9-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="77dd9-106">使用 Web 窗体，可以使用多个数据访问技术来与数据库进行交互：</span><span class="sxs-lookup"><span data-stu-id="77dd9-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="77dd9-107">Data Sources</span><span class="sxs-lookup"><span data-stu-id="77dd9-107">Data Sources</span></span>
- <span data-ttu-id="77dd9-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="77dd9-108">ADO.NET</span></span>
- <span data-ttu-id="77dd9-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="77dd9-109">Entity Framework</span></span>

<span data-ttu-id="77dd9-110">数据源是您可以放置在 Web 窗体页上的控件，并配置为与其他控件一样。</span><span class="sxs-lookup"><span data-stu-id="77dd9-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="77dd9-111">Visual Studio 提供了一组友好对话框，可用于配置控件并将控件绑定到 Web 窗体页。</span><span class="sxs-lookup"><span data-stu-id="77dd9-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="77dd9-112">在首次发布 Web 窗体时，喜欢 "低代码" 或 "无代码" 方法首选此方法的开发人员。</span><span class="sxs-lookup"><span data-stu-id="77dd9-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![Data Sources](media/data/datasources.png)

<span data-ttu-id="77dd9-114">ADO.NET 是与数据库交互的低级别方法。</span><span class="sxs-lookup"><span data-stu-id="77dd9-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="77dd9-115">您的应用程序可以使用命令、记录集和用于交互的数据集创建与数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="77dd9-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="77dd9-116">然后，可以将结果绑定到屏幕上的字段，而无需太多代码。</span><span class="sxs-lookup"><span data-stu-id="77dd9-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="77dd9-117">此方法的缺点是， (、和) 的每一组 ADO.NET 对象都 `Connection` `Command` `Recordset` 绑定到数据库供应商提供的库。</span><span class="sxs-lookup"><span data-stu-id="77dd9-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="77dd9-118">使用这些组件将使代码变得非常复杂且难以迁移到其他数据库。</span><span class="sxs-lookup"><span data-stu-id="77dd9-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="77dd9-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="77dd9-119">Entity Framework</span></span>

<span data-ttu-id="77dd9-120">实体框架 (EF) 是由 .NET Foundation 维护的开源对象关系映射框架。</span><span class="sxs-lookup"><span data-stu-id="77dd9-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="77dd9-121">最初通过 .NET Framework 发布，EF 允许为数据库连接、存储架构和交互生成代码。</span><span class="sxs-lookup"><span data-stu-id="77dd9-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="77dd9-122">通过此抽象，你可以专注于应用的业务规则，并允许受信任的数据库管理员管理数据库。</span><span class="sxs-lookup"><span data-stu-id="77dd9-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="77dd9-123">在 .NET Core 中，可以使用名为 EF Core 的 EF 的更新版本。</span><span class="sxs-lookup"><span data-stu-id="77dd9-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="77dd9-124">EF Core 有助于使用可供你使用命令行工具的一系列命令，生成和维护你的代码和数据库之间的交互 `dotnet ef` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="77dd9-125">让我们看几个示例来帮助你使用数据库。</span><span class="sxs-lookup"><span data-stu-id="77dd9-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="77dd9-126">EF Code First</span><span class="sxs-lookup"><span data-stu-id="77dd9-126">EF Code First</span></span>

<span data-ttu-id="77dd9-127">开始构建数据库交互的快速方法是从要使用的类对象开始。</span><span class="sxs-lookup"><span data-stu-id="77dd9-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="77dd9-128">EF 提供了一个工具，可帮助为你的类生成相应的数据库代码。</span><span class="sxs-lookup"><span data-stu-id="77dd9-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="77dd9-129">此方法称为 "Code First" 开发。</span><span class="sxs-lookup"><span data-stu-id="77dd9-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="77dd9-130">`Product`对于要存储在关系数据库（如 Microsoft SQL Server）中的示例店面应用，请考虑以下类。</span><span class="sxs-lookup"><span data-stu-id="77dd9-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="77dd9-131">Product 有一个主键，另外还会在数据库中创建三个字段：</span><span class="sxs-lookup"><span data-stu-id="77dd9-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="77dd9-132">EF `Id` 按约定将属性标识为主键。</span><span class="sxs-lookup"><span data-stu-id="77dd9-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="77dd9-133">`Name`将存储在为文本存储配置的列中。</span><span class="sxs-lookup"><span data-stu-id="77dd9-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="77dd9-134">`[Required]`修饰此属性的属性将添加 `not null` 约束，以帮助强制实施该属性的声明行为。</span><span class="sxs-lookup"><span data-stu-id="77dd9-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="77dd9-135">`Description`将存储在为文本存储配置的列中，并且最大长度为4000个字符，由属性所指示 `[MaxLength]` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="77dd9-136">将使用数据类型为的列配置数据库架构 `MaxLength` `varchar(4000)` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="77dd9-137">`Price`属性将存储为货币。</span><span class="sxs-lookup"><span data-stu-id="77dd9-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="77dd9-138">`[Range]`属性将生成相应的约束，以防止在声明的最小值和最大值之外进行数据存储。</span><span class="sxs-lookup"><span data-stu-id="77dd9-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="77dd9-139">需要将此类添加 `Product` 到定义了数据库的连接和转换操作的数据库上下文类中。</span><span class="sxs-lookup"><span data-stu-id="77dd9-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="77dd9-140">`MyDbContext`类提供了一个属性，该属性定义类的访问和转换 `Product` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="77dd9-141">应用程序使用类的方法中的以下项，将此类配置为与数据库进行交互 `Startup` `ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="77dd9-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="77dd9-142">前面的代码将使用指定的连接字符串连接到 SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="77dd9-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="77dd9-143">可以将连接字符串放置在*appsettings.js*文件、环境变量或其他配置存储位置，并适当地替换此嵌入字符串。</span><span class="sxs-lookup"><span data-stu-id="77dd9-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="77dd9-144">然后，可以使用以下命令生成适用于此类的数据库表：</span><span class="sxs-lookup"><span data-stu-id="77dd9-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="77dd9-145">第一个命令定义要对数据库架构进行的更改，作为名为的新 EF 迁移 `Create Product table` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="77dd9-146">迁移定义了如何应用和删除新的数据库更改。</span><span class="sxs-lookup"><span data-stu-id="77dd9-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="77dd9-147">应用后，你可以在数据库中创建一个简单的 `Product` 表，并在项目中添加了一些新类，以帮助管理数据库架构。</span><span class="sxs-lookup"><span data-stu-id="77dd9-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="77dd9-148">默认情况下，你可以在名为 "*迁移*" 的新文件夹中找到这些生成的类。</span><span class="sxs-lookup"><span data-stu-id="77dd9-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="77dd9-149">当你对类进行更改 `Product` 或添加更多相关的类来与数据库进行交互时，需要使用迁移的新名称再次运行命令行命令。</span><span class="sxs-lookup"><span data-stu-id="77dd9-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="77dd9-150">此命令将生成另一组迁移类以更新数据库架构。</span><span class="sxs-lookup"><span data-stu-id="77dd9-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="77dd9-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="77dd9-151">EF Database First</span></span>

<span data-ttu-id="77dd9-152">对于现有数据库，可以使用 .NET 命令行工具生成 EF Core 的类。</span><span class="sxs-lookup"><span data-stu-id="77dd9-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="77dd9-153">若要基架类，请使用以下命令的变体：</span><span class="sxs-lookup"><span data-stu-id="77dd9-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="77dd9-154">上述命令使用指定的连接字符串和提供程序连接到数据库 `Microsoft.EntityFrameworkCore.SqlServer` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="77dd9-155">连接后，将创建一个名为的数据库上下文类 `MyDbContext` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="77dd9-156">此外，还会为 `Product` `Customer` 与选项一起指定的和表创建支持类 `-t` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="77dd9-157">此命令有很多配置选项，可生成适用于数据库的类层次结构。</span><span class="sxs-lookup"><span data-stu-id="77dd9-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="77dd9-158">有关完整参考，请参阅[命令的文档](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)。</span><span class="sxs-lookup"><span data-stu-id="77dd9-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="77dd9-159">有关[EF Core](/ef/core/)的详细信息可在 Microsoft Docs 站点上找到。</span><span class="sxs-lookup"><span data-stu-id="77dd9-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="77dd9-160">与 web 服务进行交互</span><span class="sxs-lookup"><span data-stu-id="77dd9-160">Interact with web services</span></span>

<span data-ttu-id="77dd9-161">首次发布 ASP.NET 时，SOAP 服务是 web 服务器和客户端交换数据的首选方式。</span><span class="sxs-lookup"><span data-stu-id="77dd9-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="77dd9-162">自那时起，这种情况已发生变化，而与服务的首选交互已移动到直接 HTTP 客户端交互。</span><span class="sxs-lookup"><span data-stu-id="77dd9-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="77dd9-163">通过 ASP.NET Core 和 Blazor ，你可以 `HttpClient` 在 `Startup` 类的方法中注册的配置 `ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="77dd9-164">需要与 HTTP 终结点交互时，请使用该配置。</span><span class="sxs-lookup"><span data-stu-id="77dd9-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="77dd9-165">请考虑以下配置代码：</span><span class="sxs-lookup"><span data-stu-id="77dd9-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="77dd9-166">每当需要访问 GitHub 中的数据时，请创建名称为的客户端 `github` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="77dd9-167">为客户端配置了基址，并正确设置了请求标头。</span><span class="sxs-lookup"><span data-stu-id="77dd9-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="77dd9-168">将 `IHttpClientFactory` Blazor `@inject` 指令或属性上的属性注入到组件 `[Inject]` 。</span><span class="sxs-lookup"><span data-stu-id="77dd9-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="77dd9-169">使用以下语法创建命名客户端并与服务交互：</span><span class="sxs-lookup"><span data-stu-id="77dd9-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="77dd9-170">此方法返回描述*dotnet/文档*GitHub 存储库中的问题集合的字符串。</span><span class="sxs-lookup"><span data-stu-id="77dd9-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="77dd9-171">它将返回 JSON 格式的内容，并将其反序列化为适当的 GitHub 问题对象。</span><span class="sxs-lookup"><span data-stu-id="77dd9-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="77dd9-172">可以通过多种方式配置 `HttpClientFactory` 来提供预先配置的 `HttpClient` 对象。</span><span class="sxs-lookup"><span data-stu-id="77dd9-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="77dd9-173">尝试使用 `HttpClient` 不同的名称和终结点为你使用的各种 web 服务配置多个实例。</span><span class="sxs-lookup"><span data-stu-id="77dd9-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="77dd9-174">此方法将使你与这些服务的交互更易于在每个页面上使用。</span><span class="sxs-lookup"><span data-stu-id="77dd9-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="77dd9-175">有关更多详细信息，请参阅[IHttpClientFactory 的文档](/aspnet/core/fundamentals/http-requests)。</span><span class="sxs-lookup"><span data-stu-id="77dd9-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="77dd9-176">[上一页](forms-validation.md)
>[下一页](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="77dd9-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
