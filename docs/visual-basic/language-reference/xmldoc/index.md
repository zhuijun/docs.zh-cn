---
title: 建议用于文档注释的 XML 标记
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400094"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="41387-102">建议的用于文档注释的 XML 标记 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41387-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="41387-103">Visual Basic 编译器可以在代码中将文档注释处理到 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="41387-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="41387-104">您可以使用其他工具将 XML 文件处理到文档中。</span><span class="sxs-lookup"><span data-stu-id="41387-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="41387-105">允许对代码构造（如类型和类型成员）使用 XML 注释。</span><span class="sxs-lookup"><span data-stu-id="41387-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="41387-106">对于分部类型，只有一个类型的部分可以有 XML 注释，尽管注释其成员没有限制。</span><span class="sxs-lookup"><span data-stu-id="41387-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41387-107">文档注释不能应用于命名空间。</span><span class="sxs-lookup"><span data-stu-id="41387-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="41387-108">原因是一个命名空间可以跨多个程序集，而不是所有程序集都必须同时加载。</span><span class="sxs-lookup"><span data-stu-id="41387-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="41387-109">编译器将处理任何为有效 XML 的标记。</span><span class="sxs-lookup"><span data-stu-id="41387-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="41387-110">以下标记提供用户文档中的常用功能。</span><span class="sxs-lookup"><span data-stu-id="41387-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="41387-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="41387-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="41387-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="41387-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="41387-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="41387-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="41387-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="41387-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="41387-118">（<sup>1</sup>编译器验证语法。）</span><span class="sxs-lookup"><span data-stu-id="41387-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41387-119">如果要在文档注释的文本中显示尖括号，请使用 `&lt;` 和 `&gt;` 。</span><span class="sxs-lookup"><span data-stu-id="41387-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="41387-120">例如，该字符串 `"&lt;text in angle brackets&gt;"` 将显示为 `<text in angle brackets>` 。</span><span class="sxs-lookup"><span data-stu-id="41387-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41387-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="41387-121">See also</span></span>

- [<span data-ttu-id="41387-122">使用 XML 记录代码</span><span class="sxs-lookup"><span data-stu-id="41387-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="41387-123">-doc</span><span class="sxs-lookup"><span data-stu-id="41387-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="41387-124">如何：创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="41387-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
