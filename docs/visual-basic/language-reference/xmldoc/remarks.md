---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400016"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="25c17-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25c17-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="25c17-102">为成员指定备注部分。</span><span class="sxs-lookup"><span data-stu-id="25c17-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25c17-103">语法</span><span class="sxs-lookup"><span data-stu-id="25c17-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="25c17-104">参数</span><span class="sxs-lookup"><span data-stu-id="25c17-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="25c17-105">对成员的说明。</span><span class="sxs-lookup"><span data-stu-id="25c17-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25c17-106">备注</span><span class="sxs-lookup"><span data-stu-id="25c17-106">Remarks</span></span>  
 <span data-ttu-id="25c17-107">使用 `<remarks>` 标记添加有关类型的信息，从而补充使用指定的信息 [\<summary>](summary.md) 。</span><span class="sxs-lookup"><span data-stu-id="25c17-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="25c17-108">此信息显示在对象浏览器中。</span><span class="sxs-lookup"><span data-stu-id="25c17-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="25c17-109">有关对象浏览器的信息，请参阅[查看代码的结构](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="25c17-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="25c17-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="25c17-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25c17-111">示例</span><span class="sxs-lookup"><span data-stu-id="25c17-111">Example</span></span>  
 <span data-ttu-id="25c17-112">此示例使用 `<remarks>` 标记解释该方法的作用 `UpdateRecord` 。</span><span class="sxs-lookup"><span data-stu-id="25c17-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="25c17-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25c17-113">See also</span></span>

- [<span data-ttu-id="25c17-114">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="25c17-114">XML Comment Tags</span></span>](index.md)
