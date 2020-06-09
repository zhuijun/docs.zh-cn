---
title: 扩展保护身份验证示例自述文件
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601096"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="2edad-102">扩展保护身份验证示例自述文件</span><span class="sxs-lookup"><span data-stu-id="2edad-102">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="2edad-103">扩展保护是一项安全措施，可防止中间人（MITM）攻击，在这种攻击中，攻击者（"中间人"）截获客户端的凭据并使用这些凭据访问客户端目标服务器上的安全资源。</span><span class="sxs-lookup"><span data-stu-id="2edad-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="2edad-104">有关详细信息，请参阅[针对验证的扩展保护概述](extended-protection-for-authentication-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2edad-104">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2edad-105">仅当承载于 IIS 上时，此示例才有效。</span><span class="sxs-lookup"><span data-stu-id="2edad-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="2edad-106">它不适用于 Visual Studio 开发服务器，原因是此服务器不支持 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="2edad-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2edad-107">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="2edad-107">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="2edad-108">从 "添加/删除程序-> Windows 功能" 在计算机上安装 IIS。</span><span class="sxs-lookup"><span data-stu-id="2edad-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="2edad-109">在 Windows 功能中打开 Windows 身份验证： Internet Information Services > World Wide Web 服务-> Security-> Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="2edad-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="2edad-110">在 Windows 功能中启用 HTTP 激活： Microsoft .NET Framework 3.5.1-> Windows Communication Foundation HTTP 激活。</span><span class="sxs-lookup"><span data-stu-id="2edad-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="2edad-111">此示例要求客户端与服务器建立一个安全通道，因此它要求存在服务器证书，此证书可从 Internet 信息服务 (IIS) 管理器进行安装。</span><span class="sxs-lookup"><span data-stu-id="2edad-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="2edad-112">从 "功能视图" 选项卡中打开 IIS 管理器 > 服务器证书。</span><span class="sxs-lookup"><span data-stu-id="2edad-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="2edad-113">为了测试此示例，你可以创建一个自签名证书。</span><span class="sxs-lookup"><span data-stu-id="2edad-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="2edad-114">（如果不希望 Internet Explorer 提示证书不安全，可将证书安装到受信任的证书根颁发机构存储区中）。</span><span class="sxs-lookup"><span data-stu-id="2edad-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="2edad-115">转至默认网站的“操作”窗格。</span><span class="sxs-lookup"><span data-stu-id="2edad-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="2edad-116">单击 "编辑站点-> 绑定"。</span><span class="sxs-lookup"><span data-stu-id="2edad-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="2edad-117">如果 HTTPS 不存在，则将其作为一种类型添加，端口号为 443，并分配在上一步中创建的 SSL 证书。</span><span class="sxs-lookup"><span data-stu-id="2edad-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="2edad-118">生成服务。</span><span class="sxs-lookup"><span data-stu-id="2edad-118">Build the service.</span></span> <span data-ttu-id="2edad-119">这会在 IIS 中为你创建一个虚拟目录（从在项目属性中指定的生成后操作），并根据需要为要进行 Web 承载的服务复制 dll、.svc 和配置文件。</span><span class="sxs-lookup"><span data-stu-id="2edad-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="2edad-120">打开 IIS 管理器。</span><span class="sxs-lookup"><span data-stu-id="2edad-120">Open the IIS Manager.</span></span> <span data-ttu-id="2edad-121">右击在上一步中创建的虚拟目录 (ExtendedProtection)，然后选择“转换为应用程序”。</span><span class="sxs-lookup"><span data-stu-id="2edad-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="2edad-122">在 IIS 管理器中为此虚拟目录打开“身份验证”模块，并启用“Windows 身份验证”。</span><span class="sxs-lookup"><span data-stu-id="2edad-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="2edad-123">为此虚拟目录打开“Windows 身份验证”的“高级设置”，然后将其设置为“必选”，因为在此示例中，相应的 ExtendedProtection 设置已设置为“始终”。</span><span class="sxs-lookup"><span data-stu-id="2edad-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="2edad-124">通过从浏览器窗口访问 URL 可测试此服务。</span><span class="sxs-lookup"><span data-stu-id="2edad-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="2edad-125">如果想要跨计算机访问此 URL，请确保为所有传入 HTTP 和 HTTPS 连接打开了防火墙。</span><span class="sxs-lookup"><span data-stu-id="2edad-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="2edad-126">打开客户端配置文件，并为 \<client>  -  \<endpoint> -address 属性提供完整的计算机名称，并将替换 \<full_machine_name> 。</span><span class="sxs-lookup"><span data-stu-id="2edad-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="2edad-127">运行客户端。</span><span class="sxs-lookup"><span data-stu-id="2edad-127">Run the client.</span></span> <span data-ttu-id="2edad-128">客户端通过建立安全通道并使用扩展保护与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="2edad-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
