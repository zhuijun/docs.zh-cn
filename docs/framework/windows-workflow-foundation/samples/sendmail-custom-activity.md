---
title: SendMail 自定义活动
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 4dca15bfd3798b9282960663bea827f9323a1266
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547722"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="3faca-102">SendMail 自定义活动</span><span class="sxs-lookup"><span data-stu-id="3faca-102">SendMail Custom Activity</span></span>
<span data-ttu-id="3faca-103">本示例演示如何创建派生自 <xref:System.Activities.AsyncCodeActivity> 的自定义活动，以使用 SMTP 发送邮件供在工作流应用程序内使用。</span><span class="sxs-lookup"><span data-stu-id="3faca-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="3faca-104">自定义活动使用的功能 <xref:System.Net.Mail.SmtpClient> 以异步方式发送电子邮件，并通过身份验证发送邮件。</span><span class="sxs-lookup"><span data-stu-id="3faca-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="3faca-105">它还提供一些最终用户功能，例如测试模式、标记替换、文件模板和测试放置路径。</span><span class="sxs-lookup"><span data-stu-id="3faca-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="3faca-106">下表详细描述了 `SendMail` 活动的自变量。</span><span class="sxs-lookup"><span data-stu-id="3faca-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="3faca-107">名称</span><span class="sxs-lookup"><span data-stu-id="3faca-107">Name</span></span>|<span data-ttu-id="3faca-108">类型</span><span class="sxs-lookup"><span data-stu-id="3faca-108">Type</span></span>|<span data-ttu-id="3faca-109">描述</span><span class="sxs-lookup"><span data-stu-id="3faca-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3faca-110">主机</span><span class="sxs-lookup"><span data-stu-id="3faca-110">Host</span></span>|<span data-ttu-id="3faca-111">String</span><span class="sxs-lookup"><span data-stu-id="3faca-111">String</span></span>|<span data-ttu-id="3faca-112">SMTP 服务器主机的地址。</span><span class="sxs-lookup"><span data-stu-id="3faca-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="3faca-113">Port</span><span class="sxs-lookup"><span data-stu-id="3faca-113">Port</span></span>|<span data-ttu-id="3faca-114">String</span><span class="sxs-lookup"><span data-stu-id="3faca-114">String</span></span>|<span data-ttu-id="3faca-115">主机中 SMTP 服务的端口。</span><span class="sxs-lookup"><span data-stu-id="3faca-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="3faca-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="3faca-116">EnableSsl</span></span>|<span data-ttu-id="3faca-117">bool</span><span class="sxs-lookup"><span data-stu-id="3faca-117">bool</span></span>|<span data-ttu-id="3faca-118">指定 <xref:System.Net.Mail.SmtpClient> 是否使用安全套接字层 (SSL) 来对连接进行加密。</span><span class="sxs-lookup"><span data-stu-id="3faca-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="3faca-119">UserName</span><span class="sxs-lookup"><span data-stu-id="3faca-119">UserName</span></span>|<span data-ttu-id="3faca-120">String</span><span class="sxs-lookup"><span data-stu-id="3faca-120">String</span></span>|<span data-ttu-id="3faca-121">设置用于验证发件人 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 属性的凭据的用户名。</span><span class="sxs-lookup"><span data-stu-id="3faca-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="3faca-122">密码</span><span class="sxs-lookup"><span data-stu-id="3faca-122">Password</span></span>|<span data-ttu-id="3faca-123">String</span><span class="sxs-lookup"><span data-stu-id="3faca-123">String</span></span>|<span data-ttu-id="3faca-124">设置用于验证发件人 <xref:System.Net.Mail.SmtpClient.Credentials%2A> 属性的凭据的密码。</span><span class="sxs-lookup"><span data-stu-id="3faca-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="3faca-125">主题</span><span class="sxs-lookup"><span data-stu-id="3faca-125">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="3faca-126">邮件主题。</span><span class="sxs-lookup"><span data-stu-id="3faca-126">Subject of the message.</span></span>|  
|<span data-ttu-id="3faca-127">正文</span><span class="sxs-lookup"><span data-stu-id="3faca-127">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="3faca-128">邮件正文。</span><span class="sxs-lookup"><span data-stu-id="3faca-128">Body of the message.</span></span>|  
|<span data-ttu-id="3faca-129">Attachments</span><span class="sxs-lookup"><span data-stu-id="3faca-129">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="3faca-130">用于存储附加到此电子邮件的数据的附件集合。</span><span class="sxs-lookup"><span data-stu-id="3faca-130">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="3faca-131">从</span><span class="sxs-lookup"><span data-stu-id="3faca-131">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="3faca-132">此电子邮件的发件人地址。</span><span class="sxs-lookup"><span data-stu-id="3faca-132">From address for this email message.</span></span>|  
|<span data-ttu-id="3faca-133">功能</span><span class="sxs-lookup"><span data-stu-id="3faca-133">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="3faca-134">包含此电子邮件的收件人的地址集合。</span><span class="sxs-lookup"><span data-stu-id="3faca-134">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="3faca-135">CC</span><span class="sxs-lookup"><span data-stu-id="3faca-135">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="3faca-136">包含此电子邮件 (CC) 收件人的抄送副本的地址集合。</span><span class="sxs-lookup"><span data-stu-id="3faca-136">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="3faca-137">BCC</span><span class="sxs-lookup"><span data-stu-id="3faca-137">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="3faca-138">包含此电子邮件的密件抄送 (BCC) 收件人的地址集合。</span><span class="sxs-lookup"><span data-stu-id="3faca-138">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="3faca-139">令牌</span><span class="sxs-lookup"><span data-stu-id="3faca-139">Tokens</span></span>|<span data-ttu-id="3faca-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span><span class="sxs-lookup"><span data-stu-id="3faca-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="3faca-141">会在正文中进行替换的标记。</span><span class="sxs-lookup"><span data-stu-id="3faca-141">Tokens to replace in the body.</span></span> <span data-ttu-id="3faca-142">此功能允许用户在正文中指定一些值，这些值稍后可由使用此属性提供的标记进行替换。</span><span class="sxs-lookup"><span data-stu-id="3faca-142">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="3faca-143">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="3faca-143">BodyTemplateFilePath</span></span>|<span data-ttu-id="3faca-144">String</span><span class="sxs-lookup"><span data-stu-id="3faca-144">String</span></span>|<span data-ttu-id="3faca-145">正文模板的路径。</span><span class="sxs-lookup"><span data-stu-id="3faca-145">Path of a template for the body.</span></span> <span data-ttu-id="3faca-146">`SendMail` 活动将此文件的内容复制到其 body 属性中。</span><span class="sxs-lookup"><span data-stu-id="3faca-146">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="3faca-147">此模板可包含由 tokens 属性的内容替换的标记。</span><span class="sxs-lookup"><span data-stu-id="3faca-147">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="3faca-148">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="3faca-148">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="3faca-149">如果设置此属性，则会将所有电子邮件发送到其中指定的地址。</span><span class="sxs-lookup"><span data-stu-id="3faca-149">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="3faca-150">此属性应在测试工作流时使用。</span><span class="sxs-lookup"><span data-stu-id="3faca-150">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="3faca-151">例如，当你想要确保发送所有电子邮件，而不将其发送到实际的收件人。</span><span class="sxs-lookup"><span data-stu-id="3faca-151">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="3faca-152">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="3faca-152">TestDropPath</span></span>|<span data-ttu-id="3faca-153">String</span><span class="sxs-lookup"><span data-stu-id="3faca-153">String</span></span>|<span data-ttu-id="3faca-154">设置此属性后，还会将所有电子邮件保存在指定的文件中。</span><span class="sxs-lookup"><span data-stu-id="3faca-154">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="3faca-155">此属性应在测试或调试工作流时使用，以确保传出电子邮件的格式和内容正确。</span><span class="sxs-lookup"><span data-stu-id="3faca-155">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="3faca-156">解决方案内容</span><span class="sxs-lookup"><span data-stu-id="3faca-156">Solution Contents</span></span>  
 <span data-ttu-id="3faca-157">解决方案包含两个项目。</span><span class="sxs-lookup"><span data-stu-id="3faca-157">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="3faca-158">项目</span><span class="sxs-lookup"><span data-stu-id="3faca-158">Project</span></span>|<span data-ttu-id="3faca-159">说明</span><span class="sxs-lookup"><span data-stu-id="3faca-159">Description</span></span>|<span data-ttu-id="3faca-160">重要文件</span><span class="sxs-lookup"><span data-stu-id="3faca-160">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="3faca-161">SendMail</span><span class="sxs-lookup"><span data-stu-id="3faca-161">SendMail</span></span>|<span data-ttu-id="3faca-162">SendMail 活动</span><span class="sxs-lookup"><span data-stu-id="3faca-162">The SendMail activity</span></span>|<span data-ttu-id="3faca-163">1. SendMail.cs：主活动的实现</span><span class="sxs-lookup"><span data-stu-id="3faca-163">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="3faca-164">SendMailDesigner 和 SendMailDesigner.xaml.cs： SendMail 活动的设计器</span><span class="sxs-lookup"><span data-stu-id="3faca-164">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="3faca-165">3. MailTemplateBody.htm：要发送的电子邮件的模板。</span><span class="sxs-lookup"><span data-stu-id="3faca-165">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="3faca-166">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="3faca-166">SendMailTestClient</span></span>|<span data-ttu-id="3faca-167">测试 SendMail 活动的客户端。</span><span class="sxs-lookup"><span data-stu-id="3faca-167">Client to test the SendMail activity.</span></span>  <span data-ttu-id="3faca-168">此项目演示两种调用 SendMail 活动的方式：声明方式和编程方式。</span><span class="sxs-lookup"><span data-stu-id="3faca-168">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="3faca-169">1. sequence1.xaml：调用 SendMail 活动的工作流。</span><span class="sxs-lookup"><span data-stu-id="3faca-169">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="3faca-170">Program.cs：调用 Sequence1.xaml，并使用 SendMail 以编程方式创建工作流。</span><span class="sxs-lookup"><span data-stu-id="3faca-170">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="3faca-171">SendMail 活动的进一步配置</span><span class="sxs-lookup"><span data-stu-id="3faca-171">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="3faca-172">虽然在此示例中未显示，但用户可以执行 SendMail 活动的其他配置。</span><span class="sxs-lookup"><span data-stu-id="3faca-172">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="3faca-173">以下三部分演示如何完成此操作。</span><span class="sxs-lookup"><span data-stu-id="3faca-173">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="3faca-174">使用正文中指定的标记发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3faca-174">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="3faca-175">此代码段演示如何使用正文中的标记发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3faca-175">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="3faca-176">注意在 body 属性中提供标记的方式。</span><span class="sxs-lookup"><span data-stu-id="3faca-176">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="3faca-177">将以下标记的值提供给 tokens 属性。</span><span class="sxs-lookup"><span data-stu-id="3faca-177">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="3faca-178">使用模板发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="3faca-178">Sending an email using a template</span></span>  
 <span data-ttu-id="3faca-179">此代码段演示如何使用正文中的模板标记发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3faca-179">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="3faca-180">请注意，设置 `BodyTemplateFilePath` 属性时，不需要提供 Body 属性的值（模板文件的内容将复制到正文）。</span><span class="sxs-lookup"><span data-stu-id="3faca-180">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="3faca-181">在测试模式下发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="3faca-181">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="3faca-182">此代码段演示如何设置两个测试属性：通过将设置 `TestMailTo` 为 "所有消息" 将发送到 `john.doe@contoso.con` (，而不考虑 "收件人"、"抄送"、"密件抄送") 的值。</span><span class="sxs-lookup"><span data-stu-id="3faca-182">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="3faca-183">通过设置 TestDropPath，所有传出电子邮件还将记录在提供的路径中。</span><span class="sxs-lookup"><span data-stu-id="3faca-183">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="3faca-184">可单独设置这些属性（它们不相关）。</span><span class="sxs-lookup"><span data-stu-id="3faca-184">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="3faca-185">设置说明</span><span class="sxs-lookup"><span data-stu-id="3faca-185">Set-Up Instructions</span></span>  
 <span data-ttu-id="3faca-186">此示例要求具有对 SMTP 服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="3faca-186">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="3faca-187">有关设置 SMTP 服务器的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="3faca-187">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="3faca-188">[配置 SMTP 服务 (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="3faca-188">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="3faca-189">[IIS 7.0：配置 SMTP 电子邮件](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="3faca-189">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="3faca-190">[如何安装 SMTP 服务](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="3faca-190">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="3faca-191">可下载第三方提供的 SMTP 模拟器。</span><span class="sxs-lookup"><span data-stu-id="3faca-191">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="3faca-192">运行本示例的步骤</span><span class="sxs-lookup"><span data-stu-id="3faca-192">To run this sample</span></span>  
  
1. <span data-ttu-id="3faca-193">使用 Visual Studio 2010，打开 SendMail 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="3faca-193">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="3faca-194">确保您具有对有效 SMTP 服务器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="3faca-194">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="3faca-195">查看设置说明。</span><span class="sxs-lookup"><span data-stu-id="3faca-195">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="3faca-196">将程序配置为你的服务器地址，以及从和到电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="3faca-196">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="3faca-197">若要正确运行此示例，可能需要在 Program.cs 和 xaml 中将的值设置为电子邮件地址和 SMTP 服务器的地址。</span><span class="sxs-lookup"><span data-stu-id="3faca-197">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="3faca-198">您将需要更改这两个位置中的地址，因为程序用两种不同的方式发送邮件。</span><span class="sxs-lookup"><span data-stu-id="3faca-198">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="3faca-199">要生成解决方案，按 Ctrl+Shift+B。</span><span class="sxs-lookup"><span data-stu-id="3faca-199">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="3faca-200">若要运行解决方案，请按 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="3faca-200">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3faca-201">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="3faca-201">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3faca-202">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="3faca-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3faca-203">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3faca-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3faca-204">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="3faca-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
