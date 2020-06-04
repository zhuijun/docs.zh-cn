---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400106"
---
# <a name="include-visual-basic"></a><span data-ttu-id="1c425-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c425-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="1c425-102">引用另一个文件，该文件描述源代码中的类型和成员。</span><span class="sxs-lookup"><span data-stu-id="1c425-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c425-103">语法</span><span class="sxs-lookup"><span data-stu-id="1c425-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c425-104">参数</span><span class="sxs-lookup"><span data-stu-id="1c425-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="1c425-105">必需。</span><span class="sxs-lookup"><span data-stu-id="1c425-105">Required.</span></span> <span data-ttu-id="1c425-106">包含文档的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="1c425-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="1c425-107">可使用路径来限定文件名。</span><span class="sxs-lookup"><span data-stu-id="1c425-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="1c425-108">用 `filename` 双引号（""）引起来。</span><span class="sxs-lookup"><span data-stu-id="1c425-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="1c425-109">必需。</span><span class="sxs-lookup"><span data-stu-id="1c425-109">Required.</span></span> <span data-ttu-id="1c425-110">`filename` 中标记的路径，它指向标记 `name`。</span><span class="sxs-lookup"><span data-stu-id="1c425-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="1c425-111">将路径用双引号（""）引起来。</span><span class="sxs-lookup"><span data-stu-id="1c425-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="1c425-112">必需。</span><span class="sxs-lookup"><span data-stu-id="1c425-112">Required.</span></span> <span data-ttu-id="1c425-113">注释前面的标记中的名称说明符。</span><span class="sxs-lookup"><span data-stu-id="1c425-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="1c425-114">`Name`将有一个 `id` 。</span><span class="sxs-lookup"><span data-stu-id="1c425-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="1c425-115">必需。</span><span class="sxs-lookup"><span data-stu-id="1c425-115">Required.</span></span> <span data-ttu-id="1c425-116">标记的 ID（位于注释之前）。</span><span class="sxs-lookup"><span data-stu-id="1c425-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="1c425-117">将 ID 括在单引号（' '）内。</span><span class="sxs-lookup"><span data-stu-id="1c425-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c425-118">备注</span><span class="sxs-lookup"><span data-stu-id="1c425-118">Remarks</span></span>  
 <span data-ttu-id="1c425-119">使用 `<include>` 标记来引用另一个文件中描述源代码中的类型和成员的注释。</span><span class="sxs-lookup"><span data-stu-id="1c425-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="1c425-120">这是对直接在源代码文件中放入文档注释的替代方法。</span><span class="sxs-lookup"><span data-stu-id="1c425-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="1c425-121">`<include>`标记使用 W3C XML 路径语言（XPath）版本1.0 建议。</span><span class="sxs-lookup"><span data-stu-id="1c425-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="1c425-122">有关自定义使用方式的详细信息 `<include>` ，请参阅 <https://www.w3.org/TR/xpath> 。</span><span class="sxs-lookup"><span data-stu-id="1c425-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c425-123">示例</span><span class="sxs-lookup"><span data-stu-id="1c425-123">Example</span></span>  
 <span data-ttu-id="1c425-124">此示例使用 `<include>` 标记从名为的文件导入成员文档注释 `commentFile.xml` 。</span><span class="sxs-lookup"><span data-stu-id="1c425-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1c425-125">的格式如下所示 `commentFile.xml` 。</span><span class="sxs-lookup"><span data-stu-id="1c425-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c425-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c425-126">See also</span></span>

- [<span data-ttu-id="1c425-127">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="1c425-127">XML Comment Tags</span></span>](index.md)
