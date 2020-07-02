---
title: FTP - .NET
description: 了解 .NET Framework 通过使用 FtpWebRequest 和 FtpWebResponse 类提供的对 FTP 协议的全面支持。
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d21ca43cd1041df358dc5e2add9560fb33e85d83
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502582"
---
# <a name="ftp"></a><span data-ttu-id="63e35-103">FTP</span><span class="sxs-lookup"><span data-stu-id="63e35-103">FTP</span></span>

<span data-ttu-id="63e35-104">.NET Framework 通过 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 类为 FTP 协议提供全面支持。</span><span class="sxs-lookup"><span data-stu-id="63e35-104">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="63e35-105">这些类派生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>。</span><span class="sxs-lookup"><span data-stu-id="63e35-105">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="63e35-106">大多数情况下，<xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 类提供发出请求所需的所有事项，但如果需要访问作为属性公开的 FTP 特定功能，可以将这两个类转换为 <xref:System.Net.FtpWebRequest> 或 <xref:System.Net.FtpWebResponse>。</span><span class="sxs-lookup"><span data-stu-id="63e35-106">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="63e35-107">示例</span><span class="sxs-lookup"><span data-stu-id="63e35-107">Examples</span></span>

<span data-ttu-id="63e35-108">有关详细信息，请参阅下列主题：[如何：使用 FTP 下载文件](how-to-download-files-with-ftp.md)，[如何：使用 FTP 上传文件](how-to-upload-files-with-ftp.md)和[如何：使用 FTP 列出目录内容](how-to-list-directory-contents-with-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="63e35-108">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="63e35-109">FTP 和代理</span><span class="sxs-lookup"><span data-stu-id="63e35-109">FTP and proxies</span></span>

<span data-ttu-id="63e35-110">如果代理（由 <xref:System.Net.FtpWebRequest.Proxy%2A> 属性指定）为 HTTP 代理，则仅支持 <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory> 和 <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> 命令。</span><span class="sxs-lookup"><span data-stu-id="63e35-110">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="63e35-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="63e35-111">See also</span></span>

- [<span data-ttu-id="63e35-112">通过代理访问 Internet</span><span class="sxs-lookup"><span data-stu-id="63e35-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="63e35-113">网络编程示例</span><span class="sxs-lookup"><span data-stu-id="63e35-113">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="63e35-114">使用应用程序协议</span><span class="sxs-lookup"><span data-stu-id="63e35-114">Using Application Protocols</span></span>](using-application-protocols.md)
