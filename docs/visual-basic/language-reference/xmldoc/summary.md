---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411494"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="01459-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01459-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="01459-102">指定成员的摘要。</span><span class="sxs-lookup"><span data-stu-id="01459-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01459-103">语法</span><span class="sxs-lookup"><span data-stu-id="01459-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="01459-104">参数</span><span class="sxs-lookup"><span data-stu-id="01459-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="01459-105">对象的摘要。</span><span class="sxs-lookup"><span data-stu-id="01459-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01459-106">备注</span><span class="sxs-lookup"><span data-stu-id="01459-106">Remarks</span></span>  
 <span data-ttu-id="01459-107">使用 `<summary>` 标记来描述类型或类型成员。</span><span class="sxs-lookup"><span data-stu-id="01459-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="01459-108">用于向 [\<remarks>](remarks.md) 类型说明添加补充信息。</span><span class="sxs-lookup"><span data-stu-id="01459-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="01459-109">标记的文本 `<summary>` 是有关 IntelliSense 中类型的唯一信息源，也会显示在对象浏览器中。</span><span class="sxs-lookup"><span data-stu-id="01459-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="01459-110">有关对象浏览器的信息，请参阅[查看代码的结构](/visualstudio/ide/viewing-the-structure-of-code)。</span><span class="sxs-lookup"><span data-stu-id="01459-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="01459-111">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="01459-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01459-112">示例</span><span class="sxs-lookup"><span data-stu-id="01459-112">Example</span></span>  
 <span data-ttu-id="01459-113">此示例使用 `<summary>` 标记来描述 `ResetCounter` 方法和 `Counter` 属性。</span><span class="sxs-lookup"><span data-stu-id="01459-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01459-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01459-114">See also</span></span>

- [<span data-ttu-id="01459-115">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="01459-115">XML Comment Tags</span></span>](index.md)
