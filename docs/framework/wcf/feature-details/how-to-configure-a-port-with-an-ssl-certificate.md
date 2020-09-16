---
title: 如何：使用 SSL 证书配置端口
description: 了解如何使用 x.509 证书配置端口，该证书是使用传输安全的 WSHttpBinding 类的自承载 WCF 服务所必需的。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 619a893e0973f6691e32446d75f101201a0b6799
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556377"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="559cb-103">如何：使用 SSL 证书配置端口</span><span class="sxs-lookup"><span data-stu-id="559cb-103">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="559cb-104">当使用使用传输安全的类创建自承载 Windows Communication Foundation (WCF) 服务时 <xref:System.ServiceModel.WSHttpBinding> ，还必须使用 x.509 证书配置端口。</span><span class="sxs-lookup"><span data-stu-id="559cb-104">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="559cb-105">如果不是在创建自承载服务，可以在 Internet 信息服务 (IIS) 上承载服务。</span><span class="sxs-lookup"><span data-stu-id="559cb-105">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="559cb-106">有关详细信息，请参阅 [HTTP 传输安全](http-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="559cb-106">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="559cb-107">若要配置端口，使用的工具取决于计算机运行的操作系统。</span><span class="sxs-lookup"><span data-stu-id="559cb-107">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="559cb-108">如果运行的是 Windows Server 2003，请使用 HttpCfg.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="559cb-108">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="559cb-109">在 Windows Server 2003 上，此工具已安装。</span><span class="sxs-lookup"><span data-stu-id="559cb-109">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="559cb-110">有关详细信息，请参阅 [Httpcfg.exe 概述](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="559cb-110">For more information, see [Httpcfg Overview](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="559cb-111">[Windows 支持工具文档](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10))说明了 Httpcfg.exe 工具的语法。</span><span class="sxs-lookup"><span data-stu-id="559cb-111">The [Windows Support Tools documentation](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="559cb-112">如果运行的是 Windows Vista，请使用已安装的 Netsh.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="559cb-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="559cb-113">修改存储在计算机上的证书需要管理权限。</span><span class="sxs-lookup"><span data-stu-id="559cb-113">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="559cb-114">确定如何配置端口</span><span class="sxs-lookup"><span data-stu-id="559cb-114">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="559cb-115">在 Windows Server 2003 或 Windows XP 中，使用 HttpCfg.exe 工具来查看当前端口配置，使用 **查询** 和 **ssl** 开关，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-115">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="559cb-116">在 Windows Vista 中，使用 Netsh.exe 工具查看当前端口配置，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-116">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="559cb-117">获取证书的指纹</span><span class="sxs-lookup"><span data-stu-id="559cb-117">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="559cb-118">使用证书 MMC 管理单元查找用于客户端身份验证的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="559cb-118">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="559cb-119">有关详细信息，请参阅[如何：使用 MMC 管理单元查看证书](how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="559cb-119">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="559cb-120">访问证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="559cb-120">Access the certificate's thumbprint.</span></span> <span data-ttu-id="559cb-121">有关详细信息，请参阅[如何：检索证书的指纹](how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="559cb-121">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="559cb-122">将证书指纹复制到文本编辑器，如 Notepad。</span><span class="sxs-lookup"><span data-stu-id="559cb-122">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="559cb-123">移除十六进制字符之间的所有空格。</span><span class="sxs-lookup"><span data-stu-id="559cb-123">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="559cb-124">完成此操作的一种方法是使用文本编辑器的“查找和替换”功能，将每个空格替换为空字符。</span><span class="sxs-lookup"><span data-stu-id="559cb-124">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="559cb-125">将 SSL 证书绑定到端口号</span><span class="sxs-lookup"><span data-stu-id="559cb-125">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="559cb-126">在 Windows Server 2003 或 Windows XP 中，使用安全套接字层 (SSL) 存储上 "设置" 模式下的 HttpCfg.exe 工具将证书绑定到端口号。</span><span class="sxs-lookup"><span data-stu-id="559cb-126">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="559cb-127">该工具使用指纹识别证书，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-127">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="559cb-128">**-I**开关的语法为 `IP` ： `port` ，指示该工具将证书设置为计算机的端口8012。</span><span class="sxs-lookup"><span data-stu-id="559cb-128">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="559cb-129">另外，也可将端口号前面的四个零替换为计算机的实际 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="559cb-129">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="559cb-130">**-H**开关指定证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="559cb-130">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="559cb-131">在 Windows Vista 中，使用 Netsh.exe 工具，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-131">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="559cb-132">**Certhash**参数指定证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="559cb-132">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="559cb-133">**Ipport**参数指定 IP 地址和端口，并且函数与所述 Httpcfg.exe 工具的 **-i**开关相同。</span><span class="sxs-lookup"><span data-stu-id="559cb-133">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="559cb-134">**Appid**参数是可用于标识所属应用程序的 GUID。</span><span class="sxs-lookup"><span data-stu-id="559cb-134">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="559cb-135">将 SSL 证书绑定到端口号并支持客户端证书</span><span class="sxs-lookup"><span data-stu-id="559cb-135">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="559cb-136">在 Windows Server 2003 或 Windows XP 中，若要支持在传输层使用 x.509 证书进行身份验证的客户端，请按照前面的过程进行操作，但将其他命令行参数传递给 HttpCfg.exe，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-136">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="559cb-137">**-F**开关的语法为 `n` ，其中 n 是1到7之间的数字。</span><span class="sxs-lookup"><span data-stu-id="559cb-137">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="559cb-138">值为 2 可在传输层启用客户端证书，如上面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-138">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="559cb-139">值为 3 可启用客户端证书并将这些证书映射至 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="559cb-139">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="559cb-140">请参见“HttpCfg.exe 帮助”以获取其他值的行为。</span><span class="sxs-lookup"><span data-stu-id="559cb-140">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="559cb-141">在 Windows Vista 中，若要支持在传输层使用 x.509 证书进行身份验证的客户端，请按照前面的过程操作，但使用其他参数，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-141">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="559cb-142">从端口号删除 SSL 证书</span><span class="sxs-lookup"><span data-stu-id="559cb-142">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="559cb-143">使用 HttpCfg.exe 或 Netsh.exe 工具查看计算机上的端口和所有绑定的指纹。</span><span class="sxs-lookup"><span data-stu-id="559cb-143">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="559cb-144">若要将信息打印到磁盘，请使用重定向字符 ">"，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-144">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="559cb-145">在 Windows Server 2003 或 Windows XP 中，将 HttpCfg.exe 工具与 **delete** 和 **ssl** 关键字一起使用。</span><span class="sxs-lookup"><span data-stu-id="559cb-145">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="559cb-146">使用 **-i** 开关指定 `IP` ： `port` number，并使用 **-h** 开关指定指纹。</span><span class="sxs-lookup"><span data-stu-id="559cb-146">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="559cb-147">在 Windows Vista 中，使用 Netsh.exe 工具，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="559cb-147">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="559cb-148">示例</span><span class="sxs-lookup"><span data-stu-id="559cb-148">Example</span></span>  

 <span data-ttu-id="559cb-149">下面的代码演示如何使用 <xref:System.ServiceModel.WSHttpBinding> 类（设置为传输安全）创建自承载服务。</span><span class="sxs-lookup"><span data-stu-id="559cb-149">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="559cb-150">创建应用程序时，请指定地址中的端口号。</span><span class="sxs-lookup"><span data-stu-id="559cb-150">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="559cb-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="559cb-151">See also</span></span>

- [<span data-ttu-id="559cb-152">HTTP 传输安全</span><span class="sxs-lookup"><span data-stu-id="559cb-152">HTTP Transport Security</span></span>](http-transport-security.md)
