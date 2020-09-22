---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875177"
---
# <a name="value-visual-basic"></a><span data-ttu-id="72b5f-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72b5f-101">\<value> (Visual Basic)</span></span>

<span data-ttu-id="72b5f-102">指定属性的说明。</span><span class="sxs-lookup"><span data-stu-id="72b5f-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b5f-103">语法</span><span class="sxs-lookup"><span data-stu-id="72b5f-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="72b5f-104">参数</span><span class="sxs-lookup"><span data-stu-id="72b5f-104">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="72b5f-105">属性的说明。</span><span class="sxs-lookup"><span data-stu-id="72b5f-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72b5f-106">备注</span><span class="sxs-lookup"><span data-stu-id="72b5f-106">Remarks</span></span>  

 <span data-ttu-id="72b5f-107">使用 `<value>` 标记来描述属性。</span><span class="sxs-lookup"><span data-stu-id="72b5f-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="72b5f-108">请注意，当您使用 Visual Studio 开发环境中的代码向导添加属性时，它将 [\<summary>](summary.md) 为新属性添加标记。</span><span class="sxs-lookup"><span data-stu-id="72b5f-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="72b5f-109">然后，应手动添加 `<value>` 标记，以描述属性表示的值。</span><span class="sxs-lookup"><span data-stu-id="72b5f-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="72b5f-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="72b5f-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72b5f-111">示例</span><span class="sxs-lookup"><span data-stu-id="72b5f-111">Example</span></span>  

 <span data-ttu-id="72b5f-112">此示例使用 `<value>` 标记来描述属性包含的值 `Counter` 。</span><span class="sxs-lookup"><span data-stu-id="72b5f-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="72b5f-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72b5f-113">See also</span></span>

- [<span data-ttu-id="72b5f-114">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="72b5f-114">XML Comment Tags</span></span>](index.md)
