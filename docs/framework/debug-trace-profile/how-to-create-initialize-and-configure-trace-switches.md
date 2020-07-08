---
title: 如何：创建、初始化和配置跟踪开关
description: 使用 .NET 中的 BooleanSwitch 和 TraceSwitch 类创建、初始化和配置跟踪开关。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 6a43e143abba96c841f04b7be9d482c55e78aa8f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051319"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="8ec34-103">如何：创建、初始化和配置跟踪开关</span><span class="sxs-lookup"><span data-stu-id="8ec34-103">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="8ec34-104">跟踪开关用于启用、禁用和筛选跟踪输出。</span><span class="sxs-lookup"><span data-stu-id="8ec34-104">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="8ec34-105">创建和初始化跟踪开关</span><span class="sxs-lookup"><span data-stu-id="8ec34-105">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="8ec34-106">为了使用跟踪开关，必须首先创建跟踪开关并将其放置在代码中。</span><span class="sxs-lookup"><span data-stu-id="8ec34-106">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="8ec34-107">有两种预定义的类可用于创建开关对象：<xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> 类和 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> 类。</span><span class="sxs-lookup"><span data-stu-id="8ec34-107">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8ec34-108">如果您只关心跟踪消息是否出现，应使用 <xref:System.Diagnostics.BooleanSwitch>；如果您需要区别不同的跟踪级别，应使用 <xref:System.Diagnostics.TraceSwitch>。</span><span class="sxs-lookup"><span data-stu-id="8ec34-108">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="8ec34-109">如果使用 <xref:System.Diagnostics.TraceSwitch>，则可以定义您自己的调试消息并将其与不同的跟踪级别相关联。</span><span class="sxs-lookup"><span data-stu-id="8ec34-109">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="8ec34-110">您可以将这两种开关用于跟踪或调试。</span><span class="sxs-lookup"><span data-stu-id="8ec34-110">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="8ec34-111">默认情况下，将禁用 <xref:System.Diagnostics.BooleanSwitch>，并将 <xref:System.Diagnostics.TraceSwitch> 设置为 <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType> 级别。</span><span class="sxs-lookup"><span data-stu-id="8ec34-111">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ec34-112">可在任何需要使用跟踪开关的位置创建和放置跟踪开关。</span><span class="sxs-lookup"><span data-stu-id="8ec34-112">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="8ec34-113">虽然可以在代码中设置跟踪级别和其他配置选项，但最好使用配置文件来管理开关的状态。</span><span class="sxs-lookup"><span data-stu-id="8ec34-113">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="8ec34-114">这是因为，通过配置系统管理开关配置可获得较大的灵活性，您无需重新编译应用程序，就可以打开和关闭各个开关并更改级别。</span><span class="sxs-lookup"><span data-stu-id="8ec34-114">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="8ec34-115">若要创建和初始化跟踪开关</span><span class="sxs-lookup"><span data-stu-id="8ec34-115">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="8ec34-116">将开关定义为 <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> 类型或 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> 类型并设置开关的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="8ec34-116">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="8ec34-117">配置跟踪开关。</span><span class="sxs-lookup"><span data-stu-id="8ec34-117">Configure your trace switch.</span></span> <span data-ttu-id="8ec34-118">有关详细信息，请参阅[配置跟踪开关](#configure)。</span><span class="sxs-lookup"><span data-stu-id="8ec34-118">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="8ec34-119">以下代码创建两个开关，每种类型一个开关：</span><span class="sxs-lookup"><span data-stu-id="8ec34-119">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =
       new System.Diagnostics.TraceSwitch("General",
       "Entire application");  
    ```  
  
<a name="configure"></a>
## <a name="configuring-trace-switches"></a><span data-ttu-id="8ec34-120">配置跟踪开关</span><span class="sxs-lookup"><span data-stu-id="8ec34-120">Configuring trace switches</span></span>  
 <span data-ttu-id="8ec34-121">分发应用程序后，你仍可以通过在应用程序中配置跟踪开关来启用或禁用跟踪输出。</span><span class="sxs-lookup"><span data-stu-id="8ec34-121">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="8ec34-122">配置一个开关意味着在其初始化后，从外部源中更改其值。</span><span class="sxs-lookup"><span data-stu-id="8ec34-122">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="8ec34-123">可以使用配置文件更改开关对象的值。</span><span class="sxs-lookup"><span data-stu-id="8ec34-123">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="8ec34-124">配置跟踪开关，可以将其打开和关闭，或设置其级别，从而确定它传递到侦听器的消息量和消息类型。</span><span class="sxs-lookup"><span data-stu-id="8ec34-124">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="8ec34-125">使用 .config 文件配置开关。</span><span class="sxs-lookup"><span data-stu-id="8ec34-125">Your switches are configured using the .config file.</span></span> <span data-ttu-id="8ec34-126">对于 Web 应用程序，这是与项目关联的 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="8ec34-126">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="8ec34-127">在 Windows 应用程序中，此文件的名称为（应用程序名称） .exe.config。在已部署的应用程序中，此文件必须与可执行文件位于同一文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8ec34-127">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="8ec34-128">应用程序执行首次创建交换机的实例的代码时，它会检查有关命名开关跟踪级别信息的配置文件。</span><span class="sxs-lookup"><span data-stu-id="8ec34-128">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="8ec34-129">跟踪系统仅为任一特定的开关检查一次配置文件 — 即应用程序首次创建开关时。</span><span class="sxs-lookup"><span data-stu-id="8ec34-129">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="8ec34-130">在已部署的应用程序中，应用程序未运行时重新配置开关对象可启用跟踪代码。</span><span class="sxs-lookup"><span data-stu-id="8ec34-130">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="8ec34-131">通常，这涉及到打开和关闭开关对象或更改跟踪级别，然后重新启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="8ec34-131">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="8ec34-132">创建开关实例时，还可以通过指定 displayName 和 description 这两个参数来初始化此实例\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-132">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="8ec34-133">构造函数的 displayName 参数设置 <xref:System.Diagnostics.Switch> 类实例的 <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> 属性\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-133">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="8ec34-134">displayName 是用于在 .config 文件中配置开关的名称，description 参数应返回开关及其所控制的消息的简要说明 \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-134">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="8ec34-135">除了指定要配置的开关名称，还必须指定此开关的值。</span><span class="sxs-lookup"><span data-stu-id="8ec34-135">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="8ec34-136">此值是一个整数。</span><span class="sxs-lookup"><span data-stu-id="8ec34-136">This value is an Integer.</span></span> <span data-ttu-id="8ec34-137">对于 <xref:System.Diagnostics.BooleanSwitch>，0 值对应“关闭”，而任何非零值对应“打开”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-137">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="8ec34-138">对于 <xref:System.Diagnostics.TraceSwitch>，0、1、2、3 和 4 分别对应“关闭”、“错误”、“警告”、“信息”和“详细”\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-138">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="8ec34-139">任何大于 4 的数字将被视为“详细”，而任何小于零的数字将被视为“关闭”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-139">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ec34-140">在 .NET Framework 2.0 版中，你可以使用文本指定开关值。</span><span class="sxs-lookup"><span data-stu-id="8ec34-140">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="8ec34-141">例如，为 <xref:System.Diagnostics.BooleanSwitch> 指定 `true` 或表示枚举值的文本，例如为 <xref:System.Diagnostics.TraceSwitch> 指定 `Error`。</span><span class="sxs-lookup"><span data-stu-id="8ec34-141">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="8ec34-142">行 `<add name="myTraceSwitch" value="Error" />` 等于 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="8ec34-142">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="8ec34-143">为了使最终用户能够配置应用程序的跟踪开关，你必须提供关于应用程序中开关的详细文档。</span><span class="sxs-lookup"><span data-stu-id="8ec34-143">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="8ec34-144">应该详细说明哪些开关控制哪些内容以及如何将其打开和关闭。</span><span class="sxs-lookup"><span data-stu-id="8ec34-144">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="8ec34-145">应向你的最终用户提供 .config 文件，此文件在注释中具有适当的帮助。</span><span class="sxs-lookup"><span data-stu-id="8ec34-145">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="8ec34-146">配置跟踪开关</span><span class="sxs-lookup"><span data-stu-id="8ec34-146">To configure trace switches</span></span>  
  
1. <span data-ttu-id="8ec34-147">要使用跟踪开关，必须根据[创建和初始化跟踪开关](#create)中所述的内容首先创建跟踪开关，然后将它们放入代码中。</span><span class="sxs-lookup"><span data-stu-id="8ec34-147">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="8ec34-148">如果项目不包含配置文件（app.config 或 Web.config），则从“项目”菜单中选择“添加新项”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-148">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="8ec34-149">**Visual Basic：** 在“添加新项”对话框中，选择“应用程序配置文件”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-149">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="8ec34-150">创建并打开应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="8ec34-150">The application configuration file is created and opened.</span></span> <span data-ttu-id="8ec34-151">这是一个根元素为 `<configuration>.` 的 XML 文档</span><span class="sxs-lookup"><span data-stu-id="8ec34-151">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="8ec34-152">**Visual C#：** 在“添加新项”对话框中，选择“XML 文件”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-152">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="8ec34-153">将此文件命名**app.config**。在 XML 编辑器中，在 XML 声明的后面添加以下 XML：</span><span class="sxs-lookup"><span data-stu-id="8ec34-153">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="8ec34-154">编译项目后，app.config 文件会被复制到项目输出文件夹中，并重命名为 applicationname.exe.config\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-154">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="8ec34-155">在 `<configuration>` 标记之后但在 `</configuration>` 标记前面，添加适当的 XML 以配置开关。</span><span class="sxs-lookup"><span data-stu-id="8ec34-155">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="8ec34-156">以下示例演示了一个 DisplayName 属性为 `DataMessageSwitch` 的 BooleanSwitch，以及一个 DisplayName 属性为 `TraceLevelSwitch` 的 TraceSwitch\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-156">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="8ec34-157">在此配置中，两个开关均为关闭。</span><span class="sxs-lookup"><span data-stu-id="8ec34-157">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="8ec34-158">如果需要开启 BooleanSwitch，如前面示例中所示的 `DataMessagesSwitch`，请将“Value”更改为 0 以外的任何整数\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-158">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="8ec34-159">如果需要开启 TraceSwitch，如前面示例中所示的 `TraceLevelSwitch`，请将“Value”更改为适当的级别设置 (1-4)\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ec34-159">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="8ec34-160">将注释添加到 .config 文件，以便最终用户清楚地了解适当地配置开关所需更改的值。</span><span class="sxs-lookup"><span data-stu-id="8ec34-160">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="8ec34-161">以下示例显示最终代码（包括注释）：</span><span class="sxs-lookup"><span data-stu-id="8ec34-161">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8ec34-162">请参阅</span><span class="sxs-lookup"><span data-stu-id="8ec34-162">See also</span></span>

- [<span data-ttu-id="8ec34-163">跟踪应用程序和在应用程序中插入检测点</span><span class="sxs-lookup"><span data-stu-id="8ec34-163">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="8ec34-164">如何：向应用程序代码添加跟踪语句</span><span class="sxs-lookup"><span data-stu-id="8ec34-164">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="8ec34-165">跟踪开关</span><span class="sxs-lookup"><span data-stu-id="8ec34-165">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="8ec34-166">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="8ec34-166">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)
