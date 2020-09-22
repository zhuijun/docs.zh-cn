---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0846efbaf2afacd3d0783a2d2d8e4dae3fc8b715
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872710"
---
# <a name="para-visual-basic"></a><span data-ttu-id="a3f08-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3f08-101">\<para> (Visual Basic)</span></span>

<span data-ttu-id="a3f08-102">指定将内容的格式设置为段落。</span><span class="sxs-lookup"><span data-stu-id="a3f08-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f08-103">语法</span><span class="sxs-lookup"><span data-stu-id="a3f08-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3f08-104">参数</span><span class="sxs-lookup"><span data-stu-id="a3f08-104">Parameters</span></span>  

 `content`  
 <span data-ttu-id="a3f08-105">段落文本。</span><span class="sxs-lookup"><span data-stu-id="a3f08-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3f08-106">备注</span><span class="sxs-lookup"><span data-stu-id="a3f08-106">Remarks</span></span>  

 <span data-ttu-id="a3f08-107">`<para>` 标记用于标记内，例如 [\<summary>](summary.md)、[\<remarks>](remarks.md) 或 [\<returns>](returns.md)，允许向文本添加结构。</span><span class="sxs-lookup"><span data-stu-id="a3f08-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="a3f08-108">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="a3f08-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3f08-109">示例</span><span class="sxs-lookup"><span data-stu-id="a3f08-109">Example</span></span>  

 <span data-ttu-id="a3f08-110">此示例使用 `<para>` 标记将方法的 "备注" 部分拆分为 `UpdateRecord` 两个段落。</span><span class="sxs-lookup"><span data-stu-id="a3f08-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a3f08-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3f08-111">See also</span></span>

- [<span data-ttu-id="a3f08-112">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="a3f08-112">XML Comment Tags</span></span>](index.md)
