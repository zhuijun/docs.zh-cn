---
title: 如何：在 Web 窗体应用程序中使用事件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
ms.openlocfilehash: 3490b6fb89bfe6d7ac778078f58381bb5172e2fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288480"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="7084a-102">如何：在 Web 窗体应用程序中使用事件</span><span class="sxs-lookup"><span data-stu-id="7084a-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="7084a-103">ASP.NET Web 窗体应用程序中的一种常见情况是使用控件填充网页，然后根据用户单击的控件执行特定操作。</span><span class="sxs-lookup"><span data-stu-id="7084a-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="7084a-104">例如，当用户在网页中单击 <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> 控件时，该控件会引发一个事件。</span><span class="sxs-lookup"><span data-stu-id="7084a-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="7084a-105">通过处理事件，应用可以对按钮单击执行相应的应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="7084a-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="7084a-106">处理网页中的按钮单击事件</span><span class="sxs-lookup"><span data-stu-id="7084a-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="7084a-107">创建一个具有 <xref:System.Web.UI.WebControls.Button> 控件的 ASP.NET Web 窗体页，并将控件的 `OnClick` 值设置为下一步中定义的方法名称。</span><span class="sxs-lookup"><span data-stu-id="7084a-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="7084a-108">定义一个事件处理程序，使之与 <xref:System.Web.UI.WebControls.Button.Click> 事件委托签名匹配，并且具有为 `OnClick` 值定义的名称。</span><span class="sxs-lookup"><span data-stu-id="7084a-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <span data-ttu-id="7084a-109"><xref:System.Web.UI.WebControls.Button.Click> 事件将 <xref:System.EventHandler> 类用于委托类型，并将 <xref:System.EventArgs> 类用于事件数据。</span><span class="sxs-lookup"><span data-stu-id="7084a-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="7084a-110">ASP.NET 页框架会自动生成代码来创建 <xref:System.EventHandler> 的实例，并将此委托实例添加到 <xref:System.Web.UI.WebControls.Button.Click> 实例的 <xref:System.Web.UI.WebControls.Button> 事件。</span><span class="sxs-lookup"><span data-stu-id="7084a-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="7084a-111">在步骤 2 中定义的事件处理程序方法会添加代码以执行事件发生时所需的各种操作。</span><span class="sxs-lookup"><span data-stu-id="7084a-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7084a-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7084a-112">See also</span></span>

- [<span data-ttu-id="7084a-113">事件</span><span class="sxs-lookup"><span data-stu-id="7084a-113">Events</span></span>](index.md)
