---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84399990"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="00acf-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00acf-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="00acf-102">指定属性或函数的返回值。</span><span class="sxs-lookup"><span data-stu-id="00acf-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00acf-103">语法</span><span class="sxs-lookup"><span data-stu-id="00acf-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="00acf-104">参数</span><span class="sxs-lookup"><span data-stu-id="00acf-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="00acf-105">返回值的说明。</span><span class="sxs-lookup"><span data-stu-id="00acf-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00acf-106">备注</span><span class="sxs-lookup"><span data-stu-id="00acf-106">Remarks</span></span>  
 <span data-ttu-id="00acf-107">`<returns>`在方法声明的注释中使用标记来描述返回值。</span><span class="sxs-lookup"><span data-stu-id="00acf-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="00acf-108">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="00acf-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00acf-109">示例</span><span class="sxs-lookup"><span data-stu-id="00acf-109">Example</span></span>  
 <span data-ttu-id="00acf-110">此示例使用 `<returns>` 标记解释函数返回的内容 `DoesRecordExist` 。</span><span class="sxs-lookup"><span data-stu-id="00acf-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="00acf-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00acf-111">See also</span></span>

- [<span data-ttu-id="00acf-112">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="00acf-112">XML Comment Tags</span></span>](index.md)
