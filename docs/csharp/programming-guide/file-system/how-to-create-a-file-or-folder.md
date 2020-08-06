---
title: 如何创建文件或文件夹 - C# 编程指南
description: 了解如何通过编程方式创建文件或文件夹。 可以创建文件夹、子文件夹和子文件夹中的文件，并将数据写入该文件。
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: f5641dc765b1a2d62adb76babe3f111730d4550b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302680"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="baf47-104">如何创建文件或文件夹（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="baf47-104">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="baf47-105">可通过编程方式在计算机上创建文件夹、子文件夹和子文件夹中的文件，并将数据写入文件。</span><span class="sxs-lookup"><span data-stu-id="baf47-105">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf47-106">示例</span><span class="sxs-lookup"><span data-stu-id="baf47-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="baf47-107">如果文件夹已存在，<xref:System.IO.Directory.CreateDirectory%2A> 不执行任何操作，未引发任何异常。</span><span class="sxs-lookup"><span data-stu-id="baf47-107">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="baf47-108">但 <xref:System.IO.File.Create%2A?displayProperty=nameWithType> 用新文件替换现有文件。</span><span class="sxs-lookup"><span data-stu-id="baf47-108">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="baf47-109">本示例使用 `if`-`else` 语句阻止替换现有文件。</span><span class="sxs-lookup"><span data-stu-id="baf47-109">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="baf47-110">通过在示例中作出以下更改，可根据具有特定名称的文件是否存在来指定不同的结果。</span><span class="sxs-lookup"><span data-stu-id="baf47-110">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="baf47-111">如果该文件不存在，代码就会创建一个文件。</span><span class="sxs-lookup"><span data-stu-id="baf47-111">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="baf47-112">如果该文件存在，代码就会将数据追加到该文件中。</span><span class="sxs-lookup"><span data-stu-id="baf47-112">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="baf47-113">指定一个非随机文件名。</span><span class="sxs-lookup"><span data-stu-id="baf47-113">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="baf47-114">用以下代码中的 `using` 语句替换 `if`-`else` 语句。</span><span class="sxs-lookup"><span data-stu-id="baf47-114">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="baf47-115">多次运行此示例，验证数据是否每次都添加到了文件中。</span><span class="sxs-lookup"><span data-stu-id="baf47-115">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="baf47-116">有关可尝试的 `FileMode` 值，请参阅 <xref:System.IO.FileMode>。</span><span class="sxs-lookup"><span data-stu-id="baf47-116">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="baf47-117">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="baf47-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="baf47-118">文件夹名称格式不正确。</span><span class="sxs-lookup"><span data-stu-id="baf47-118">The folder name is malformed.</span></span> <span data-ttu-id="baf47-119">例如，它包含非法字符或它仅为空格（<xref:System.ArgumentException> 类）。</span><span class="sxs-lookup"><span data-stu-id="baf47-119">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="baf47-120">使用 <xref:System.IO.Path> 类创建有效的路径名。</span><span class="sxs-lookup"><span data-stu-id="baf47-120">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="baf47-121">要创建的文件夹的父文件夹为只读（<xref:System.IO.IOException> 类）。</span><span class="sxs-lookup"><span data-stu-id="baf47-121">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="baf47-122">文件夹名为 `null`<xref:System.ArgumentNullException> 类）。</span><span class="sxs-lookup"><span data-stu-id="baf47-122">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="baf47-123">文件夹名过长（<xref:System.IO.PathTooLongException> 类）。</span><span class="sxs-lookup"><span data-stu-id="baf47-123">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="baf47-124">文件夹仅为冒号“:”（<xref:System.IO.PathTooLongException> 类）。</span><span class="sxs-lookup"><span data-stu-id="baf47-124">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="baf47-125">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="baf47-125">.NET Security</span></span>  
 <span data-ttu-id="baf47-126">可能在部分信任场景中引发 <xref:System.Security.SecurityException> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="baf47-126">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="baf47-127">如果没有创建文件夹的权限，则本示例引发 <xref:System.UnauthorizedAccessException> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="baf47-127">If you don't have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf47-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="baf47-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="baf47-129">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="baf47-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="baf47-130">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="baf47-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
