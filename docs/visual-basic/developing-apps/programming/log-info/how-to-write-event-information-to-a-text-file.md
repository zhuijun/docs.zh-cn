---
title: 'How to: Write Event Information to a Text File'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 6e83f8450ca7be8a2dcd5ff43eab3dd2ec0d2f1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410057"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="992bf-102">如何：将事件信息写入文本文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="992bf-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="992bf-103">可以使用 `My.Application.Log` 和 `My.Log` 对象来记录有关应用程序中所发生事件的信息。</span><span class="sxs-lookup"><span data-stu-id="992bf-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="992bf-104">本示例演示如何使用 `My.Application.Log.WriteEntry` 方法将跟踪信息记录到日志文件中。</span><span class="sxs-lookup"><span data-stu-id="992bf-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="992bf-105">添加和配置文件日志侦听器</span><span class="sxs-lookup"><span data-stu-id="992bf-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="992bf-106">在“解决方案资源管理器”  中右键单击 app.config，然后选择“打开”  。</span><span class="sxs-lookup"><span data-stu-id="992bf-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="992bf-107">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="992bf-107">\- or -</span></span>

     <span data-ttu-id="992bf-108">如果其中没有 app.config 文件：</span><span class="sxs-lookup"><span data-stu-id="992bf-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="992bf-109">在 **“项目”** 菜单上选择 **“添加新项”** 。</span><span class="sxs-lookup"><span data-stu-id="992bf-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="992bf-110">在“添加新项”  对话框中，选择“应用程序配置文件”  。</span><span class="sxs-lookup"><span data-stu-id="992bf-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="992bf-111">单击 **添加**。</span><span class="sxs-lookup"><span data-stu-id="992bf-111">Click **Add**.</span></span>

2. <span data-ttu-id="992bf-112">在应用程序配置文件中找到 `<listeners>` 部分。</span><span class="sxs-lookup"><span data-stu-id="992bf-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="992bf-113">\<listeners> 部分位于 name 属性为“DefaultSource”的 \<source> 部分当中，后者又嵌套在 \<system.diagnostics> 部分当中，位于顶级 \<configuration> 部分之下。</span><span class="sxs-lookup"><span data-stu-id="992bf-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="992bf-114">将此元素添加到该 `<listeners>` 部分：</span><span class="sxs-lookup"><span data-stu-id="992bf-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="992bf-115">找到 `<sharedListeners>` 部分，该部分位于 `<system.diagnostics>` 部分中，后者嵌套在顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="992bf-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="992bf-116">将此元素添加到该 `<sharedListeners>` 部分：</span><span class="sxs-lookup"><span data-stu-id="992bf-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="992bf-117">将 `customlocation` 属性的值更改为日志目录。</span><span class="sxs-lookup"><span data-stu-id="992bf-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="992bf-118">若要设置侦听器属性的值，请使用与该属性具有相同名称的特性，名称中的所有字母都为小写。</span><span class="sxs-lookup"><span data-stu-id="992bf-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="992bf-119">例如，`location` 和 `customlocation` 属性设置 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> 和 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="992bf-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="992bf-120">将事件信息写入文件日志</span><span class="sxs-lookup"><span data-stu-id="992bf-120">To write event information to the file log</span></span>

<span data-ttu-id="992bf-121">可以使用 `My.Application.Log.WriteEntry` 或 `My.Application.Log.WriteException` 方法将信息写入文件日志。</span><span class="sxs-lookup"><span data-stu-id="992bf-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="992bf-122">有关详细信息，请参阅[如何：编写日志消息](how-to-write-log-messages.md)和[如何：记录异常](how-to-log-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="992bf-122">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="992bf-123">为程序集配置文件日志侦听器后，它将接收该程序集写入 `My.Application.Log` 的所有消息。</span><span class="sxs-lookup"><span data-stu-id="992bf-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="992bf-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="992bf-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="992bf-125">使用应用程序日志</span><span class="sxs-lookup"><span data-stu-id="992bf-125">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="992bf-126">如何：日志异常</span><span class="sxs-lookup"><span data-stu-id="992bf-126">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
