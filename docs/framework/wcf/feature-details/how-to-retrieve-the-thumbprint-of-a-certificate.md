---
title: 如何：检索证书的指纹
description: 了解如何指定在 x.509 证书中找到的声明，这在开发使用证书进行身份验证的 WCF 应用程序时是必需的。
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: 0622ff9b990dd9d8fe14c4a4c1d48cc8530d5a61
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609468"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="372f4-103">如何：检索证书的指纹</span><span class="sxs-lookup"><span data-stu-id="372f4-103">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="372f4-104">编写使用 x.509 证书进行身份验证的 Windows Communication Foundation (WCF) 应用程序时，通常需要指定在证书中找到的声明。</span><span class="sxs-lookup"><span data-stu-id="372f4-104">When writing a Windows Communication Foundation (WCF) application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="372f4-105">例如，在 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 方法中使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 枚举时，必须提供指纹声明。</span><span class="sxs-lookup"><span data-stu-id="372f4-105">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="372f4-106">查找声明值有两个步骤。</span><span class="sxs-lookup"><span data-stu-id="372f4-106">Finding the claim value requires two steps.</span></span> <span data-ttu-id="372f4-107">首先，打开用于证书的 Microsoft 管理控制台 (MMC) 管理单元</span><span class="sxs-lookup"><span data-stu-id="372f4-107">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="372f4-108"> (参阅 [如何：使用 MMC 管理单元查看证书](how-to-view-certificates-with-the-mmc-snap-in.md)。 ) 秒钟，如此处所述，查找相应的证书并将其指纹 (或其他声明值) 。</span><span class="sxs-lookup"><span data-stu-id="372f4-108">(See [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="372f4-109">如果您要将证书用于服务身份验证，一定要记下 **“颁发给”** 列（控制台中的首列）的值，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="372f4-109">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="372f4-110">在将安全套接字层 (SSL) 用作传输安全时，首先需要执行的检查之一是将服务的基址统一资源标识符 (URI) 与 **“颁发给”** 值进行比较。</span><span class="sxs-lookup"><span data-stu-id="372f4-110">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="372f4-111">这些值必须匹配，否则身份验证进程会暂停。</span><span class="sxs-lookup"><span data-stu-id="372f4-111">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="372f4-112">你还可以使用 PowerShell New-selfsignedcertificate cmdlet 来创建只在开发过程中使用的临时证书。</span><span class="sxs-lookup"><span data-stu-id="372f4-112">You can also use the PowerShell New-SelfSignedCertificate cmdlet to create temporary certificates for use only during development.</span></span> <span data-ttu-id="372f4-113">但是，默认情况下，此类证书不是由证书颁发机构颁发的，并且不可用于生产目的。</span><span class="sxs-lookup"><span data-stu-id="372f4-113">By default, however, such a certificate is not issued by a certification authority and is unusable for production purposes.</span></span> <span data-ttu-id="372f4-114">有关详细信息，请参阅 [如何：创建在开发期间使用的临时证书](how-to-create-temporary-certificates-for-use-during-development.md)。</span><span class="sxs-lookup"><span data-stu-id="372f4-114">For more information, see [How to: Create Temporary Certificates for Use During Development](how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="372f4-115">检索证书的指纹</span><span class="sxs-lookup"><span data-stu-id="372f4-115">To retrieve a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="372f4-116">打开用于证书的 Microsoft 管理控制台 (MMC) 管理单元</span><span class="sxs-lookup"><span data-stu-id="372f4-116">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="372f4-117">（请参阅 [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md)。）</span><span class="sxs-lookup"><span data-stu-id="372f4-117">(See [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2. <span data-ttu-id="372f4-118">在 **“控制台根节点”** 窗口的左窗格中，单击 **“证书(本地计算机)”**。</span><span class="sxs-lookup"><span data-stu-id="372f4-118">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3. <span data-ttu-id="372f4-119">单击 **“个人”** 文件夹将其展开。</span><span class="sxs-lookup"><span data-stu-id="372f4-119">Click the **Personal** folder to expand it.</span></span>  
  
4. <span data-ttu-id="372f4-120">单击 **“证书”** 文件夹将其展开。</span><span class="sxs-lookup"><span data-stu-id="372f4-120">Click the **Certificates** folder to expand it.</span></span>  
  
5. <span data-ttu-id="372f4-121">在证书列表中，注意 **“预期目的”** 标题。</span><span class="sxs-lookup"><span data-stu-id="372f4-121">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="372f4-122">查找一个按预期目的列出 **“客户端身份验证”** 的证书。</span><span class="sxs-lookup"><span data-stu-id="372f4-122">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6. <span data-ttu-id="372f4-123">双击该证书。</span><span class="sxs-lookup"><span data-stu-id="372f4-123">Double-click the certificate.</span></span>  
  
7. <span data-ttu-id="372f4-124">在 **“证书”** 对话框中，单击 **“详细信息”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="372f4-124">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8. <span data-ttu-id="372f4-125">浏览该字段列表并单击 **“指纹”**。</span><span class="sxs-lookup"><span data-stu-id="372f4-125">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="372f4-126">复制该框中的十六进制字符。</span><span class="sxs-lookup"><span data-stu-id="372f4-126">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="372f4-127">如果此指纹在 `X509FindType`的代码中使用，请移除十六进制数字之间的空格。</span><span class="sxs-lookup"><span data-stu-id="372f4-127">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="372f4-128">例如，指纹“a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b”在代码中应指定为“a909502dd82ae41433e6f83886b00d4277a32a7b”。</span><span class="sxs-lookup"><span data-stu-id="372f4-128">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372f4-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="372f4-129">See also</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [<span data-ttu-id="372f4-130">如何：使用 SSL 证书配置端口</span><span class="sxs-lookup"><span data-stu-id="372f4-130">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="372f4-131">如何：使用 MMC 管理单元查看证书</span><span class="sxs-lookup"><span data-stu-id="372f4-131">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="372f4-132">如何：创建开发期间使用的临时证书</span><span class="sxs-lookup"><span data-stu-id="372f4-132">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
