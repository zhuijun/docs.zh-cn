---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 0a68cf0a495c2809961e8ec99effa459b0647fec
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866390"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="fbfc8-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbfc8-101">\<typeparam> (Visual Basic)</span></span>

<span data-ttu-id="fbfc8-102">定义类型参数名称和说明。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfc8-103">语法</span><span class="sxs-lookup"><span data-stu-id="fbfc8-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbfc8-104">parameters</span><span class="sxs-lookup"><span data-stu-id="fbfc8-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="fbfc8-105">类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-105">The name of the type parameter.</span></span> <span data-ttu-id="fbfc8-106">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="fbfc8-107">类型参数的说明。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbfc8-108">备注</span><span class="sxs-lookup"><span data-stu-id="fbfc8-108">Remarks</span></span>  

 <span data-ttu-id="fbfc8-109">在 `<typeparam>` 泛型类型或泛型成员声明的注释中使用标记来描述一个类型参数。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="fbfc8-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbfc8-111">示例</span><span class="sxs-lookup"><span data-stu-id="fbfc8-111">Example</span></span>  

 <span data-ttu-id="fbfc8-112">此示例使用 `<typeparam>` 标记来描述 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="fbfc8-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="fbfc8-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbfc8-113">See also</span></span>

- [<span data-ttu-id="fbfc8-114">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="fbfc8-114">XML Comment Tags</span></span>](index.md)
