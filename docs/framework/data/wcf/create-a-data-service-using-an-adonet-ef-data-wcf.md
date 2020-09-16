---
title: 如何：使用 ADO.NET 实体框架数据源创建数据服务（WCF 数据服务）
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 1e559488a3260fafe6c211ff47226a258fc1289a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557692"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="184d4-102">如何：使用 ADO.NET 实体框架数据源创建数据服务（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="184d4-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="184d4-103">WCF 数据服务将实体数据作为数据服务公开。</span><span class="sxs-lookup"><span data-stu-id="184d4-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="184d4-104">当数据源为关系数据库时，NETEntity 框架将提供此实体数据。</span><span class="sxs-lookup"><span data-stu-id="184d4-104">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="184d4-105">本主题介绍如何在基于现有数据库的 Visual Studio Web 应用程序中创建基于实体框架的数据模型，以及如何使用此数据模型创建新的数据服务。</span><span class="sxs-lookup"><span data-stu-id="184d4-105">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="184d4-106">实体框架还提供可以在 Visual Studio 项目外生成实体框架模型的命令行工具。</span><span class="sxs-lookup"><span data-stu-id="184d4-106">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="184d4-107">有关详细信息，请参阅 [如何：使用 EdmGen.exe 生成模型和映射文件](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="184d4-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="184d4-108">将基于现有数据库的实体框架模型添加到现有 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="184d4-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="184d4-109">在 "**项目**" 菜单上，单击 "**添加**  >  **新项**"。</span><span class="sxs-lookup"><span data-stu-id="184d4-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="184d4-110">在 " **模板** " 窗格中，单击 " **数据** " 类别，然后选择 " **ADO.NET 实体数据模型**"。</span><span class="sxs-lookup"><span data-stu-id="184d4-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="184d4-111">输入模型名称，然后单击 " **添加**"。</span><span class="sxs-lookup"><span data-stu-id="184d4-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="184d4-112">将显示“实体数据模型向导”的第一页。</span><span class="sxs-lookup"><span data-stu-id="184d4-112">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="184d4-113">在 " **选择模型内容** " 对话框中，选择 " **从数据库生成**"。</span><span class="sxs-lookup"><span data-stu-id="184d4-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="184d4-114">然后单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="184d4-114">Then click **Next**.</span></span>

5. <span data-ttu-id="184d4-115">单击 " **新建连接** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="184d4-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="184d4-116">在 " **连接属性** " 对话框中，键入服务器名称，选择身份验证方法，键入数据库名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="184d4-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="184d4-117">" **选择您的数据连接** " 对话框将通过数据库连接设置进行更新。</span><span class="sxs-lookup"><span data-stu-id="184d4-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="184d4-118">确保选中 " **将实体连接设置保存 App.Config 为：** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="184d4-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="184d4-119">然后单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="184d4-119">Then click **Next**.</span></span>

8. <span data-ttu-id="184d4-120">在 " **选择数据库对象** " 对话框中，选择计划在数据服务中公开的所有数据库对象。</span><span class="sxs-lookup"><span data-stu-id="184d4-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="184d4-121">数据服务不自动公开数据模型中包含的对象。</span><span class="sxs-lookup"><span data-stu-id="184d4-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="184d4-122">它们必须由服务本身显式公开。</span><span class="sxs-lookup"><span data-stu-id="184d4-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="184d4-123">有关详细信息，请参阅 [配置数据服务](configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="184d4-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="184d4-124">单击 **“完成”** 以完成向导。</span><span class="sxs-lookup"><span data-stu-id="184d4-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="184d4-125">这将基于特定数据库创建默认数据模型。</span><span class="sxs-lookup"><span data-stu-id="184d4-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="184d4-126">实体框架允许对数据模型进行自定义。</span><span class="sxs-lookup"><span data-stu-id="184d4-126">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="184d4-127">有关详细信息，请参阅 [实体数据模型工具任务](/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="184d4-127">For more information, see [Entity Data Model Tools Tasks](/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="184d4-128">使用新数据模型创建数据服务</span><span class="sxs-lookup"><span data-stu-id="184d4-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="184d4-129">在 Visual Studio 中，打开代表数据模型的 .edmx 文件。</span><span class="sxs-lookup"><span data-stu-id="184d4-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="184d4-130">在 **模型浏览器**中，右键单击模型，单击 " **属性**"，然后记下实体容器的名称。</span><span class="sxs-lookup"><span data-stu-id="184d4-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="184d4-131">在**解决方案资源管理器**中，右键单击 ASP.NET 项目的名称，然后单击 "**添加**  >  **新项**"。</span><span class="sxs-lookup"><span data-stu-id="184d4-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="184d4-132">在 "**添加新项**" 对话框中，选择 " **Web** " 类别中的 " **WCF 数据服务**" 模板。</span><span class="sxs-lookup"><span data-stu-id="184d4-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Visual Studio 2015 中的 WCF 数据服务项模板](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="184d4-134">**WCF 数据服务**模板在 visual studio 2015 中提供，但在 visual studio 2017 或更高版本中不可用。</span><span class="sxs-lookup"><span data-stu-id="184d4-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

5. <span data-ttu-id="184d4-135">提供服务的名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="184d4-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="184d4-136">Visual Studio 将为新服务创建 XML 标记和代码文件。</span><span class="sxs-lookup"><span data-stu-id="184d4-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="184d4-137">默认情况下，代码编辑器窗口将打开。</span><span class="sxs-lookup"><span data-stu-id="184d4-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="184d4-138">在数据服务代码中，将用于定义数据服务的类定义中的注释 `/* TODO: put your data source class name here */` 替换为从 <xref:System.Data.Objects.ObjectContext> 类继承且作为数据模型的实体容器的类型，如步骤 2 中所述。</span><span class="sxs-lookup"><span data-stu-id="184d4-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="184d4-139">在数据服务代码中，启用经过授权的客户端来访问数据服务公开的实体集。</span><span class="sxs-lookup"><span data-stu-id="184d4-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="184d4-140">有关详细信息，请参阅 [创建数据服务](creating-the-data-service.md)。</span><span class="sxs-lookup"><span data-stu-id="184d4-140">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="184d4-141">若要使用 Web 浏览器测试 Northwind 数据服务，请按照主题 [从 Web 浏览器访问该服务](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="184d4-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="184d4-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="184d4-142">See also</span></span>

- [<span data-ttu-id="184d4-143">定义 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="184d4-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="184d4-144">数据服务提供程序</span><span class="sxs-lookup"><span data-stu-id="184d4-144">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="184d4-145">如何：使用反射提供程序创建数据服务</span><span class="sxs-lookup"><span data-stu-id="184d4-145">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="184d4-146">如何：使用 LINQ to SQL 数据源创建数据服务</span><span class="sxs-lookup"><span data-stu-id="184d4-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
