---
title: 获取 ADO.NET 代码示例的示例 SQL Server 数据库
description: 下载 ADO.NET 文档的代码示例中使用的示例 SQL Server 数据库，以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156051"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="61a67-103">获取 ADO.NET 代码示例的示例数据库</span><span class="sxs-lookup"><span data-stu-id="61a67-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="61a67-104">文档中的一些示例和演练 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server 数据库和 SQL Server Express 的示例。</span><span class="sxs-lookup"><span data-stu-id="61a67-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="61a67-105">你可以从 Microsoft 免费下载这些产品。</span><span class="sxs-lookup"><span data-stu-id="61a67-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="61a67-106">获取用于 SQL Server 的 Northwind 示例数据库</span><span class="sxs-lookup"><span data-stu-id="61a67-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="61a67-107">`instnwnd.sql`从以下 GitHub 存储库下载脚本，为 SQL Server 创建和加载 Northwind 示例数据库：</span><span class="sxs-lookup"><span data-stu-id="61a67-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="61a67-108">用于 Microsoft SQL Server 的 Northwind 和 pubs 示例数据库</span><span class="sxs-lookup"><span data-stu-id="61a67-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="61a67-109">在您可以使用 Northwind 数据库之前，您必须运行下载的 `instnwnd.sql` 脚本文件以通过使用 [SQL Server Management Studio](#get_ssms) 或类似的工具在 SQL Server 的实例上重新创建数据库。</span><span class="sxs-lookup"><span data-stu-id="61a67-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="61a67-110">按照存储库中的自述文件中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="61a67-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="61a67-111">如果正在寻找用于 Microsoft Access 的 Northwind 数据库，请参阅 [安装用于 Microsoft access 的 northwind 示例数据库](#northwind_access)。</span><span class="sxs-lookup"><span data-stu-id="61a67-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> <span data-ttu-id="61a67-112">获取 Microsoft Access 的 Northwind 示例数据库</span><span class="sxs-lookup"><span data-stu-id="61a67-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="61a67-113">Microsoft 下载中心不提供用于 Microsoft Access 的 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="61a67-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="61a67-114">若要直接从 Access 中安装 Northwind，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="61a67-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="61a67-115">打开访问。</span><span class="sxs-lookup"><span data-stu-id="61a67-115">Open Access.</span></span>

1. <span data-ttu-id="61a67-116">在 "**搜索联机模板**" 框中输入**Northwind** ，然后选择**Enter**。</span><span class="sxs-lookup"><span data-stu-id="61a67-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="61a67-117">在结果屏幕上，选择 " **Northwind**"。</span><span class="sxs-lookup"><span data-stu-id="61a67-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="61a67-118">此时将打开一个新窗口，其中包含 Northwind 数据库的说明。</span><span class="sxs-lookup"><span data-stu-id="61a67-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="61a67-119">在新窗口中，在 " **文件名** " 文本框中提供 Northwind 数据库副本的文件名。</span><span class="sxs-lookup"><span data-stu-id="61a67-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="61a67-120">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="61a67-120">Select **Create**.</span></span> <span data-ttu-id="61a67-121">Access 会下载 Northwind 数据库并准备好文件。</span><span class="sxs-lookup"><span data-stu-id="61a67-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="61a67-122">此过程完成后，数据库将打开并显示欢迎屏幕。</span><span class="sxs-lookup"><span data-stu-id="61a67-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="61a67-123">获取用于 SQL Server 的 AdventureWorks 示例数据库</span><span class="sxs-lookup"><span data-stu-id="61a67-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="61a67-124">从以下 GitHub 存储库下载适用于 SQL Server 的 AdventureWorks 示例数据库：</span><span class="sxs-lookup"><span data-stu-id="61a67-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

<span data-ttu-id="61a67-125">[AdventureWorks sample databases](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)（AdventureWorks 示例数据库）</span><span class="sxs-lookup"><span data-stu-id="61a67-125">[AdventureWorks sample databases](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)</span></span>

<span data-ttu-id="61a67-126">将一个数据库备份 (\* .bak) 文件下载完成后，使用 SQL Server Management Studio (SSMS) 将备份还原到 SQL Server 的实例。</span><span class="sxs-lookup"><span data-stu-id="61a67-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="61a67-127">请参阅 [获取 SQL Server Management Studio](#get_ssms)。</span><span class="sxs-lookup"><span data-stu-id="61a67-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> <span data-ttu-id="61a67-128">获取 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61a67-128">Get SQL Server Management Studio</span></span>

<span data-ttu-id="61a67-129">若要查看或修改已下载的数据库，可以使用 SQL Server Management Studio (SSMS) 。</span><span class="sxs-lookup"><span data-stu-id="61a67-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="61a67-130">从以下页面下载 SSMS：</span><span class="sxs-lookup"><span data-stu-id="61a67-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="61a67-131">下载 SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="61a67-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="61a67-132">你还可以在 Visual Studio 集成开发环境 (IDE) 中查看和管理数据库。</span><span class="sxs-lookup"><span data-stu-id="61a67-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="61a67-133">在 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)中，从 **SQL Server 对象资源管理器**连接到数据库，或创建到 **服务器资源管理器**中的数据库的数据连接。</span><span class="sxs-lookup"><span data-stu-id="61a67-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="61a67-134">从 " **视图** " 菜单打开这些 "资源管理器" 窗格。</span><span class="sxs-lookup"><span data-stu-id="61a67-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a> <span data-ttu-id="61a67-135">获取 SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="61a67-135">Get SQL Server Express</span></span>

<span data-ttu-id="61a67-136">SQL Server Express 是免费的入门级版 SQL Server，可与应用程序一起分发。</span><span class="sxs-lookup"><span data-stu-id="61a67-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="61a67-137">从以下页面下载 SQL Server Express：</span><span class="sxs-lookup"><span data-stu-id="61a67-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="61a67-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="61a67-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="61a67-139">如果你使用的是 [Visual studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)，则 visual Studio 免费社区版以及专业版和更高版本中都包含 SQL Server Express LocalDB。</span><span class="sxs-lookup"><span data-stu-id="61a67-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="61a67-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="61a67-140">See also</span></span>

- [<span data-ttu-id="61a67-141">入门</span><span class="sxs-lookup"><span data-stu-id="61a67-141">Getting Started</span></span>](getting-started.md)
