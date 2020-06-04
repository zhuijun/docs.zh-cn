---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411481"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="64f81-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64f81-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="64f81-102">定义类型参数名称和说明。</span><span class="sxs-lookup"><span data-stu-id="64f81-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f81-103">语法</span><span class="sxs-lookup"><span data-stu-id="64f81-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="64f81-104">参数</span><span class="sxs-lookup"><span data-stu-id="64f81-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="64f81-105">类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="64f81-105">The name of the type parameter.</span></span> <span data-ttu-id="64f81-106">用双引号 (" ") 将名称引起来。</span><span class="sxs-lookup"><span data-stu-id="64f81-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="64f81-107">类型参数的说明。</span><span class="sxs-lookup"><span data-stu-id="64f81-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64f81-108">备注</span><span class="sxs-lookup"><span data-stu-id="64f81-108">Remarks</span></span>  
 <span data-ttu-id="64f81-109">在 `<typeparam>` 泛型类型或泛型成员声明的注释中使用标记来描述一个类型参数。</span><span class="sxs-lookup"><span data-stu-id="64f81-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="64f81-110">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="64f81-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64f81-111">示例</span><span class="sxs-lookup"><span data-stu-id="64f81-111">Example</span></span>  
 <span data-ttu-id="64f81-112">此示例使用 `<typeparam>` 标记来描述 `id` 参数。</span><span class="sxs-lookup"><span data-stu-id="64f81-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="64f81-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64f81-113">See also</span></span>

- [<span data-ttu-id="64f81-114">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="64f81-114">XML Comment Tags</span></span>](index.md)
