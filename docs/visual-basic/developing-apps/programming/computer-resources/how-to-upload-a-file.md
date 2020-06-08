---
title: 如何：上载文件
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: cee6811d6b6d295c28eb683c5d2f7bcbb5fe94ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401805"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="dc395-102">如何：在 Visual Basic 中上传文件</span><span class="sxs-lookup"><span data-stu-id="dc395-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="dc395-103">可使用 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> 方法上传文件并将文件存储到远程位置。</span><span class="sxs-lookup"><span data-stu-id="dc395-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="dc395-104">如果 `ShowUI` 参数设置为 `True`，则显示一个对话框，该对话框显示上传进度并允许用户取消该操作。</span><span class="sxs-lookup"><span data-stu-id="dc395-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="dc395-105">上传文件</span><span class="sxs-lookup"><span data-stu-id="dc395-105">To upload a file</span></span>  
  
- <span data-ttu-id="dc395-106">可以使用 `UploadFile` 方法上传文件，同时将源文件的位置和目标目录位置指定为字符串或 URI（统一资源标识符）。此示例将文件 `Order.txt` 上传到 `http://www.cohowinery.com/uploads.aspx`。</span><span class="sxs-lookup"><span data-stu-id="dc395-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="dc395-107">上传文件并显示操作进度</span><span class="sxs-lookup"><span data-stu-id="dc395-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="dc395-108">可以使用 `UploadFile` 方法上传文件，同时将源文件的位置和目标目录位置指定为字符串或 URI。</span><span class="sxs-lookup"><span data-stu-id="dc395-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="dc395-109">此示例在不提供用户名或密码的情况下将文件 `Order.txt` 上传到 `http://www.cohowinery.com/uploads.aspx`显示了上传操作的进度，并将将超时间隔为 500 毫秒。</span><span class="sxs-lookup"><span data-stu-id="dc395-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="dc395-110">上传文件并提供用户名和密码</span><span class="sxs-lookup"><span data-stu-id="dc395-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="dc395-111">可以使用 `UploadFile` 方法上传文件，同时将源文件的位置和目标目录位置指定为字符串或 URI，并指定用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="dc395-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="dc395-112">此示例将文件 `Order.txt` 上传到 `http://www.cohowinery.com/uploads.aspx`，并提供了用户名 `anonymous` 和空白密码。</span><span class="sxs-lookup"><span data-stu-id="dc395-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dc395-113">可靠编程</span><span class="sxs-lookup"><span data-stu-id="dc395-113">Robust Programming</span></span>  

 <span data-ttu-id="dc395-114">以下情况可能会引发异常：</span><span class="sxs-lookup"><span data-stu-id="dc395-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="dc395-115">本地文件路径无效 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="dc395-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="dc395-116">身份验证失败 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="dc395-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="dc395-117">连接超时 (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="dc395-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc395-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dc395-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="dc395-119">如何：下载文件</span><span class="sxs-lookup"><span data-stu-id="dc395-119">How to: Download a File</span></span>](how-to-download-a-file.md)
- [<span data-ttu-id="dc395-120">如何：分析文件路径</span><span class="sxs-lookup"><span data-stu-id="dc395-120">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
