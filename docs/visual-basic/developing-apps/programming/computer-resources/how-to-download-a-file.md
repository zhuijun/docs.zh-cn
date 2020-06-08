---
title: 如何：下载文件
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: a5b379da00656f65476e4d9504457bf8b464beac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411650"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="2f0b1-102">如何：在 Visual Basic 中下载文件</span><span class="sxs-lookup"><span data-stu-id="2f0b1-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="2f0b1-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> 方法可用来下载远程文件并将其存储到特定位置。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="2f0b1-104">如果 `ShowUI` 参数设置为 `True`，则显示一个对话框，该对话框显示下载进度并允许用户取消该操作。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="2f0b1-105">默认情况下，不会覆盖同名的现有文件；如果希望覆盖现有文件，则将 `overwrite` 参数设为 `True`。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="2f0b1-106">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="2f0b1-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="2f0b1-107">驱动器名称无效 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="2f0b1-108">尚未提供必要的身份验证（<xref:System.UnauthorizedAccessException> 或 <xref:System.Security.SecurityException>）。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="2f0b1-109">服务器未在指定的 `connectionTimeout` (<xref:System.TimeoutException>) 内响应。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="2f0b1-110">请求被网站 (<xref:System.Net.WebException>) 拒绝。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="2f0b1-111">不要根据文件的名称来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="2f0b1-112">例如，文件 Form1.vb 可能不是 Visual Basic 源文件。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="2f0b1-113">在应用程序中使用输入的数据之前，需验证所有的输入内容。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="2f0b1-114">文件的内容可能不是预期内容，并且用来读取该文件的方法可能失败。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="2f0b1-115">下载文件</span><span class="sxs-lookup"><span data-stu-id="2f0b1-115">To download a file</span></span>

- <span data-ttu-id="2f0b1-116">使用 `DownloadFile` 方法下载文件，同时将目标文件的位置指定为字符串或 URI 并指定要存储该文件的位置。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="2f0b1-117">此示例从 `http://www.cohowinery.com/downloads` 下载 `WineList.txt` 文件，并将其保存到 `C:\Documents and Settings\All Users\Documents` 中：</span><span class="sxs-lookup"><span data-stu-id="2f0b1-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="2f0b1-118">下载文件，并指定超时间隔</span><span class="sxs-lookup"><span data-stu-id="2f0b1-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="2f0b1-119">使用 `DownloadFile` 方法下载文件，同时将目标文件的位置指定为字符串或 URI，指定要存储该文件的位置，并以毫秒为单位指定超时间隔（默认值为 1000 毫秒）。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="2f0b1-120">此示例从 `http://www.cohowinery.com/downloads` 下载 `WineList.txt` 文件，然后将该文件保存到 `C:\Documents and Settings\All Users\Documents`，同时将超时间隔指定为 500 毫秒：</span><span class="sxs-lookup"><span data-stu-id="2f0b1-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="2f0b1-121">提供用户名和密码下载文件</span><span class="sxs-lookup"><span data-stu-id="2f0b1-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="2f0b1-122">使用 `DownLoadFile` 方法下载文件，同时将目标文件的位置指定为字符串或 URI，并指定要存储该文件的位置、用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="2f0b1-123">此示例使用用户名 `anonymous` 和空密码从 `http://www.cohowinery.com/downloads` 下载 `WineList.txt` 文件，然后将该文件保存到 `C:\Documents and Settings\All Users\Documents`。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="2f0b1-124">`DownLoadFile` 方法使用的 FTP 协议以纯文本方式发送信息（包括密码），因此不应用于传送敏感信息。</span><span class="sxs-lookup"><span data-stu-id="2f0b1-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f0b1-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f0b1-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="2f0b1-126">如何：上载文件</span><span class="sxs-lookup"><span data-stu-id="2f0b1-126">How to: Upload a File</span></span>](how-to-upload-a-file.md)
- [<span data-ttu-id="2f0b1-127">如何：分析文件路径</span><span class="sxs-lookup"><span data-stu-id="2f0b1-127">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
