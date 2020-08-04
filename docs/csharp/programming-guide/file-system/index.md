---
title: 文件系统和注册表 - C# 编程指南
description: 查看介绍如何使用 C# 和 .NET 对文件、文件夹和注册表执行基本操作的文章。
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 9e25058f5fb8ae49196c070dd426123e61a55e46
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301627"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="4d67f-103">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4d67f-103">File system and the registry (C# Programming Guide)</span></span>

<span data-ttu-id="4d67f-104">下面各文章介绍了如何使用 C# 和 .NET 对文件、文件夹和注册表执行各种基本操作。</span><span class="sxs-lookup"><span data-stu-id="4d67f-104">The following articles show how to use C# and .NET to perform various basic operations on files, folders, and the registry.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4d67f-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="4d67f-105">In this section</span></span>

|<span data-ttu-id="4d67f-106">**标题**</span><span class="sxs-lookup"><span data-stu-id="4d67f-106">**Title**</span></span>|<span data-ttu-id="4d67f-107">**说明**</span><span class="sxs-lookup"><span data-stu-id="4d67f-107">**Description**</span></span>|
|---------------|---------------------|
|[<span data-ttu-id="4d67f-108">如何循环访问目录树</span><span class="sxs-lookup"><span data-stu-id="4d67f-108">How to iterate through a directory tree</span></span>](how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="4d67f-109">介绍了如何手动循环访问目录树。</span><span class="sxs-lookup"><span data-stu-id="4d67f-109">Shows how to manually iterate through a directory tree.</span></span>|
|[<span data-ttu-id="4d67f-110">如何获取有关文件、文件夹和驱动器的信息</span><span class="sxs-lookup"><span data-stu-id="4d67f-110">How to get information about files, folders, and drives</span></span>](how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="4d67f-111">介绍了如何检索有关文件、文件夹和驱动器的信息，如创建时间和大小。</span><span class="sxs-lookup"><span data-stu-id="4d67f-111">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|
|[<span data-ttu-id="4d67f-112">如何创建文件或文件夹</span><span class="sxs-lookup"><span data-stu-id="4d67f-112">How to create a file or folder</span></span>](how-to-create-a-file-or-folder.md)|<span data-ttu-id="4d67f-113">介绍了如何新建文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="4d67f-113">Shows how to create a new file or folder.</span></span>|
|[<span data-ttu-id="4d67f-114">如何复制、删除和移动文件和文件夹（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4d67f-114">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="4d67f-115">介绍了如何复制、删除、移动文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="4d67f-115">Shows how to copy, delete and move files and folders.</span></span>|
|[<span data-ttu-id="4d67f-116">如何提供文件操作进度对话框</span><span class="sxs-lookup"><span data-stu-id="4d67f-116">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="4d67f-117">介绍了如何显示特定文件操作的标准 Windows 进度对话框。</span><span class="sxs-lookup"><span data-stu-id="4d67f-117">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|
|[<span data-ttu-id="4d67f-118">如何写入文本文件</span><span class="sxs-lookup"><span data-stu-id="4d67f-118">How to write to a text file</span></span>](how-to-write-to-a-text-file.md)|<span data-ttu-id="4d67f-119">介绍了如何将内容写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="4d67f-119">Shows how to write to a text file.</span></span>|
|[<span data-ttu-id="4d67f-120">如何读取文本文件中的内容</span><span class="sxs-lookup"><span data-stu-id="4d67f-120">How to read from a text file</span></span>](how-to-read-from-a-text-file.md)|<span data-ttu-id="4d67f-121">介绍了如何读取文本文件中的内容。</span><span class="sxs-lookup"><span data-stu-id="4d67f-121">Shows how to read from a text file.</span></span>|
|[<span data-ttu-id="4d67f-122">如何一次一行地读取文本文件</span><span class="sxs-lookup"><span data-stu-id="4d67f-122">How to read a text file one line at a time</span></span>](how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="4d67f-123">介绍了如何一次一行地检索文件文本。</span><span class="sxs-lookup"><span data-stu-id="4d67f-123">Shows how to retrieve text from a file one line at a time.</span></span>|
|[<span data-ttu-id="4d67f-124">如何在注册表中创建注册表项</span><span class="sxs-lookup"><span data-stu-id="4d67f-124">How to create a key in the registry</span></span>](how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="4d67f-125">介绍了如何将注册表项写入系统注册表。</span><span class="sxs-lookup"><span data-stu-id="4d67f-125">Shows how to write a key to the system registry.</span></span>|

## <a name="related-sections"></a><span data-ttu-id="4d67f-126">相关章节</span><span class="sxs-lookup"><span data-stu-id="4d67f-126">Related sections</span></span>

- [<span data-ttu-id="4d67f-127">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="4d67f-127">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="4d67f-128">如何复制、删除和移动文件和文件夹（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4d67f-128">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](how-to-copy-delete-and-move-files-and-folders.md)
- [<span data-ttu-id="4d67f-129">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="4d67f-129">C# Programming Guide</span></span>](../index.md)
- <xref:System.IO?displayProperty=nameWithType>
