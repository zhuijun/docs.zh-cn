---
title: 理解使用用于 .NET 的 Azure 库进行身份验证
description: 介绍使用用于 .NET 的 Azure SDK 进行身份验证的不同方法。
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 727842b34faa37558220a3035ac5228fae196201
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301614"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="51bc9-103">使用用于 .NET 的 Azure SDK 进行身份验证</span><span class="sxs-lookup"><span data-stu-id="51bc9-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="51bc9-104">建议：Azure.Identity</span><span class="sxs-lookup"><span data-stu-id="51bc9-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="51bc9-105">用于 .NET 的 Azure SDK 中最新的包使用常用的身份验证包进行身份验证，即 `Azure.Identity`。</span><span class="sxs-lookup"><span data-stu-id="51bc9-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="51bc9-106">建议使用 `Azure.Identity`，而不是本文档稍后将介绍的其他身份验证机制。</span><span class="sxs-lookup"><span data-stu-id="51bc9-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="51bc9-107">支持 `Azure.Identity` 提供的凭据的包具有开头为 Azure 的包标识符。</span><span class="sxs-lookup"><span data-stu-id="51bc9-107">Packages supporting the credentials provided by `Azure.Identity` have package identifiers starting with *Azure.*</span></span> <span data-ttu-id="51bc9-108">[有关详细信息，请参阅用于 .NET 的 Azure SDK 的最新版本](https://azure.github.io/azure-sdk/releases/latest/index.html#net)。</span><span class="sxs-lookup"><span data-stu-id="51bc9-108">[For more information, see the latest releases in the Azure SDK for .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span></span>

<span data-ttu-id="51bc9-109">若要查看有关在项目中使用 `Azure.Identity` 的完整说明，请参阅[用于 .NET 的 Azure 标识客户端](/dotnet/api/overview/azure/identity-readme)的文档。</span><span class="sxs-lookup"><span data-stu-id="51bc9-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="51bc9-110">若要了解有关使用 Azure 标识管理和访问 Azure 资源的示例，请参阅 [Azure 标识、资源管理和存储示例](/samples/dotnet/samples/azure-identity-resource-management-storage/)。</span><span class="sxs-lookup"><span data-stu-id="51bc9-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="51bc9-111">若要使用不支持 Azure.Identity 的库进行身份验证，请参阅本主题的其余部分。</span><span class="sxs-lookup"><span data-stu-id="51bc9-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="51bc9-112">访问 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="51bc9-112">Access Azure resources</span></span>

<span data-ttu-id="51bc9-113">若要与 Azure 资源进行交互（例如从 Key Vault 检索机密，或在 Azure 存储中存储 Blob），许多 Azure 服务库需要使用连接字符串或密钥进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="51bc9-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="51bc9-114">例如，SQL 数据库使用[标准 SQL 连接字符串](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="51bc9-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="51bc9-115">服务连接字符串用于 [CosmosDB](/azure/cosmos-db/)、[Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache) 和[服务总线](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues)等其他 Azure 服务。</span><span class="sxs-lookup"><span data-stu-id="51bc9-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="51bc9-116">可以使用 Azure 门户、CLI 或 PowerShell 获取这些字符串。</span><span class="sxs-lookup"><span data-stu-id="51bc9-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="51bc9-117">还可以使用用于 .NET 的 Azure 管理库来查询资源，以便在代码中生成连接字符串。</span><span class="sxs-lookup"><span data-stu-id="51bc9-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="51bc9-118">使用连接字符串的方法因产品而异。</span><span class="sxs-lookup"><span data-stu-id="51bc9-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="51bc9-119">[请参阅 Azure 产品的文档](/azure/?product=featured)。</span><span class="sxs-lookup"><span data-stu-id="51bc9-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="51bc9-120">管理 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="51bc9-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="51bc9-121">创建服务主体后，可以使用两个选项对服务主体进行身份验证，以创建和管理资源。</span><span class="sxs-lookup"><span data-stu-id="51bc9-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="51bc9-122">若要使用这两个选项，需将以下 NuGet 包添加到项目。</span><span class="sxs-lookup"><span data-stu-id="51bc9-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="51bc9-123">使用令牌凭据进行身份验证</span><span class="sxs-lookup"><span data-stu-id="51bc9-123">Authenticate with token credentials</span></span>

<span data-ttu-id="51bc9-124">第一种方法是在代码中生成令牌凭据对象。</span><span class="sxs-lookup"><span data-stu-id="51bc9-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="51bc9-125">应将凭据安全存储在配置文件、注册表或 Azure KeyVault 中。</span><span class="sxs-lookup"><span data-stu-id="51bc9-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="51bc9-126">使用在创建服务主体时获得的 JSON 输出中的 *clientId*、*clientSecret* 和 *tenantId* 值。</span><span class="sxs-lookup"><span data-stu-id="51bc9-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="51bc9-127">然后，创建入口点 `Azure` 对象以开始使用 API：</span><span class="sxs-lookup"><span data-stu-id="51bc9-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

<span data-ttu-id="51bc9-128">建议向 `Azure` 对象显式提供 JSON 输出中的 subscriptionId：</span><span class="sxs-lookup"><span data-stu-id="51bc9-128">It is recommended that you explicitly provide the *subscriptionId* from the JSON output to the `Azure` object:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="51bc9-129">基于文件的身份验证</span><span class="sxs-lookup"><span data-stu-id="51bc9-129">File-based authentication</span></span>

<span data-ttu-id="51bc9-130">使用基于文件的身份验证可将服务主体凭据放入纯文本文件，并在文件系统中对其进行保护。</span><span class="sxs-lookup"><span data-stu-id="51bc9-130">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="51bc9-131">读取该文件的内容，并创建入口点 `Azure` 对象以开始使用 API：</span><span class="sxs-lookup"><span data-stu-id="51bc9-131">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
