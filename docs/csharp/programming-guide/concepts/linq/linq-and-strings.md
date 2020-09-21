---
title: LINQ 和字符串 (C#)
description: LINQ 可以查询和转换字符串和字符串集合。 可以将 LINQ 查询与 C# 字符串函数和正则表达式结合起来。
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: 0500d821335659fa29dd4809513f38dac0a8b193
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556715"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="3fa45-104">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-104">LINQ and strings (C#)</span></span>

<span data-ttu-id="3fa45-105">LINQ 可用于查询和转换字符串和字符串集合。</span><span class="sxs-lookup"><span data-stu-id="3fa45-105">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="3fa45-106">这在处理文本文件中的半结构化数据时尤其有用。</span><span class="sxs-lookup"><span data-stu-id="3fa45-106">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="3fa45-107">LINQ 查询可以与传统的字符串函数和正则表达式合并。</span><span class="sxs-lookup"><span data-stu-id="3fa45-107">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="3fa45-108">例如，可以使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 或 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法来创建可稍后使用 LINQ 查询或修改的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="3fa45-108">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="3fa45-109">可以使用 LINQ 查询的 `where` 子句中的 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3fa45-109">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="3fa45-110">并且可以使用 LINQ 查询或修改正则表达式返回的 <xref:System.Text.RegularExpressions.MatchCollection> 结果。</span><span class="sxs-lookup"><span data-stu-id="3fa45-110">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="3fa45-111">还可以使用本节介绍的技术将半结构化的文本数据转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="3fa45-111">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="3fa45-112">有关详细信息，请参阅[如何从 CSV 文件生成 XML](../../../../standard/linq/generate-xml-csv-files.md)。</span><span class="sxs-lookup"><span data-stu-id="3fa45-112">For more information, see [How to generate XML from CSV files](../../../../standard/linq/generate-xml-csv-files.md).</span></span>

<span data-ttu-id="3fa45-113">本节中的示例分为两类：</span><span class="sxs-lookup"><span data-stu-id="3fa45-113">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="3fa45-114">查询文本块</span><span class="sxs-lookup"><span data-stu-id="3fa45-114">Querying a block of text</span></span>

<span data-ttu-id="3fa45-115">可以使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法或 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> 方法将文本块拆分为可查询的较小字符串数组，从而对其进行查询、分析和修改。</span><span class="sxs-lookup"><span data-stu-id="3fa45-115">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3fa45-116">可以先将源文本拆分为词语、句、段落、页或任何其他条件，然后根据查询的需要执行其他拆分。</span><span class="sxs-lookup"><span data-stu-id="3fa45-116">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="3fa45-117">如何对某个词在字符串中出现的次数进行计数 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-117">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="3fa45-118">演示如何使用 LINQ 进行简单文本查询。</span><span class="sxs-lookup"><span data-stu-id="3fa45-118">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="3fa45-119">如何查询包含一组指定词语的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-119">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="3fa45-120">演示如何在任意边界上拆分文本文件以及如何针对每个部分执行查询。</span><span class="sxs-lookup"><span data-stu-id="3fa45-120">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="3fa45-121">如何查询字符串中的字符 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-121">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="3fa45-122">演示字符串是可查询类型。</span><span class="sxs-lookup"><span data-stu-id="3fa45-122">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="3fa45-123">如何将 LINQ 查询与正则表达式合并 (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-123">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="3fa45-124">演示如何在 LINQ 查询中使用正则表达式，以便对筛选的查询结果进行复杂的模式匹配。</span><span class="sxs-lookup"><span data-stu-id="3fa45-124">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="3fa45-125">查询文本格式的半结构化数据</span><span class="sxs-lookup"><span data-stu-id="3fa45-125">Querying semi-structured data in text format</span></span>

<span data-ttu-id="3fa45-126">许多不同类型的文本文件都包含一系列行，通常具有类似的格式设置，例如制表符分隔或逗号分隔的文件或固定长度的行。</span><span class="sxs-lookup"><span data-stu-id="3fa45-126">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="3fa45-127">将此类文本文件读入内存后，可以使用 LINQ 来查询和/或修改其中的行。</span><span class="sxs-lookup"><span data-stu-id="3fa45-127">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="3fa45-128">LINQ 查询还简化了合并来自多个源的数据的任务。</span><span class="sxs-lookup"><span data-stu-id="3fa45-128">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="3fa45-129">如何查找两个列表之间的差集 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-129">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="3fa45-130">演示如何查找出现在一个列表中、但没有出现在另一个列表中的所有字符串。</span><span class="sxs-lookup"><span data-stu-id="3fa45-130">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="3fa45-131">如何按任意词或字段对文本数据进行排序或筛选 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-131">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="3fa45-132">演示如何基于任意词或字段对文本行进行排序。</span><span class="sxs-lookup"><span data-stu-id="3fa45-132">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="3fa45-133">如何重新排列带分隔符的文件的字段 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-133">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="3fa45-134">演示如何对 .csv 文件的某行中的字段进行重新排序。</span><span class="sxs-lookup"><span data-stu-id="3fa45-134">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="3fa45-135">如何合并和比较字符串集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-135">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="3fa45-136">演示如何通过各种方式合并字符串列表。</span><span class="sxs-lookup"><span data-stu-id="3fa45-136">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="3fa45-137">如何从多个源填充对象集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="3fa45-138">演示如何将多个文本文件作为数据源来创建对象集合。</span><span class="sxs-lookup"><span data-stu-id="3fa45-138">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="3fa45-139">如何联接不同文件的内容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-139">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="3fa45-140">演示如何使用匹配键将两个列表中的字符串合并成单个字符串。</span><span class="sxs-lookup"><span data-stu-id="3fa45-140">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="3fa45-141">如何使用组将一个文件拆分成多个文件 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-141">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="3fa45-142">演示如何通过将单个文件用作数据源来创建新文件。</span><span class="sxs-lookup"><span data-stu-id="3fa45-142">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="3fa45-143">如何在 CSV 文本文件中计算列值 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-143">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="3fa45-144">演示如何在 .csv 文件中对文本数据执行数学计算。</span><span class="sxs-lookup"><span data-stu-id="3fa45-144">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa45-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="3fa45-145">See also</span></span>

- [<span data-ttu-id="3fa45-146">语言集成查询 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa45-146">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="3fa45-147">如何从 CSV 文件生成 XML</span><span class="sxs-lookup"><span data-stu-id="3fa45-147">How to generate XML from CSV files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
