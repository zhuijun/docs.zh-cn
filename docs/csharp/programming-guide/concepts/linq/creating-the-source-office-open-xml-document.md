---
title: 创建源 Office Open XML 文档 (C#)
description: 创建 Office Open XML WordprocessingML 文档以用于 C# 教程。 本文需要 Microsoft Office。
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103991"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="1f212-104">创建源 Office Open XML 文档 (C#)</span><span class="sxs-lookup"><span data-stu-id="1f212-104">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="1f212-105">本主题演示如何创建本教程其他示例中使用的 Office Open XML WordprocessingML 文档。</span><span class="sxs-lookup"><span data-stu-id="1f212-105">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="1f212-106">如果您按照这些说明操作，您的输出结果将与每个示例中提供的输出相匹配。</span><span class="sxs-lookup"><span data-stu-id="1f212-106">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="1f212-107">不过，本教程中的示例可以使用任何有效的 WordprocessingML 文档。</span><span class="sxs-lookup"><span data-stu-id="1f212-107">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="1f212-108">若要创建本教程使用的文档，必须安装 Microsoft Office 2007 或更高版本，或者具有 Microsoft Office Word、Excel 和 PowerPoint 2007 文件格式兼容包的 Microsoft Office 2003。</span><span class="sxs-lookup"><span data-stu-id="1f212-108">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="1f212-109">创建 WordprocessingML 文档</span><span class="sxs-lookup"><span data-stu-id="1f212-109">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="1f212-110">创建 WordprocessingML 文档</span><span class="sxs-lookup"><span data-stu-id="1f212-110">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="1f212-111">创建一个新的 Microsoft Word 文档。</span><span class="sxs-lookup"><span data-stu-id="1f212-111">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="1f212-112">将以下文本粘贴到新文档中：</span><span class="sxs-lookup"><span data-stu-id="1f212-112">Paste the following text into the new document:</span></span>

    ```text
    Parsing WordprocessingML with LINQ to XML

    The following example prints to the console.

    using System;

    class Program {
        public static void Main(string[] args) {
            Console.WriteLine("Hello World");
        }
    }

    This example produces the following output:

    Hello World
    ```

3. <span data-ttu-id="1f212-113">用“标题 1”样式格式化第一行。</span><span class="sxs-lookup"><span data-stu-id="1f212-113">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="1f212-114">选择包含 C# 代码的行。</span><span class="sxs-lookup"><span data-stu-id="1f212-114">Select the lines that contain the C# code.</span></span> <span data-ttu-id="1f212-115">第一行以 `using` 关键字开头。</span><span class="sxs-lookup"><span data-stu-id="1f212-115">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="1f212-116">最后一行是最后一个右大括号。</span><span class="sxs-lookup"><span data-stu-id="1f212-116">The last line is the last closing brace.</span></span> <span data-ttu-id="1f212-117">用 courier 字体格式化这些行。</span><span class="sxs-lookup"><span data-stu-id="1f212-117">Format the lines with the courier font.</span></span> <span data-ttu-id="1f212-118">用新样式格式化这些行并将新样式命名为“Code”。</span><span class="sxs-lookup"><span data-stu-id="1f212-118">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="1f212-119">最后，选择包含输出的整个行，并用 `Code` 样式格式化该行。</span><span class="sxs-lookup"><span data-stu-id="1f212-119">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="1f212-120">保存文档，并将其命名为 SampleDoc.docx。</span><span class="sxs-lookup"><span data-stu-id="1f212-120">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f212-121">如果使用的是 Microsoft Word 2003，请在“保存类型”下拉列表中选择“Word 2007 文档”。</span><span class="sxs-lookup"><span data-stu-id="1f212-121">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
