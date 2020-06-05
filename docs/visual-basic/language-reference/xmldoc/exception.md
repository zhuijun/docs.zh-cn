---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 3a2452ec60a2182adfee365777d9824001ff006a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400119"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="edb1e-101">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edb1e-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="edb1e-102">指定可以引发的异常。</span><span class="sxs-lookup"><span data-stu-id="edb1e-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb1e-103">语法</span><span class="sxs-lookup"><span data-stu-id="edb1e-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="edb1e-104">参数</span><span class="sxs-lookup"><span data-stu-id="edb1e-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="edb1e-105">对当前编译环境中出现的一个异常的引用。</span><span class="sxs-lookup"><span data-stu-id="edb1e-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="edb1e-106">编译器检查是否存在给定的异常，并将 `member` 转换为输出 XML 中的规范的元素名称。</span><span class="sxs-lookup"><span data-stu-id="edb1e-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="edb1e-107">`member` 必须出现在双引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="edb1e-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="edb1e-108">说明。</span><span class="sxs-lookup"><span data-stu-id="edb1e-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edb1e-109">备注</span><span class="sxs-lookup"><span data-stu-id="edb1e-109">Remarks</span></span>  
 <span data-ttu-id="edb1e-110">使用 `<exception>` 标记指定可以引发的异常。</span><span class="sxs-lookup"><span data-stu-id="edb1e-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="edb1e-111">这是适用于方法定义的标记。</span><span class="sxs-lookup"><span data-stu-id="edb1e-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="edb1e-112">使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。</span><span class="sxs-lookup"><span data-stu-id="edb1e-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb1e-113">示例</span><span class="sxs-lookup"><span data-stu-id="edb1e-113">Example</span></span>  
 <span data-ttu-id="edb1e-114">此示例使用 `<exception>` 标记来描述 `IntDivide` 函数可以引发的异常。</span><span class="sxs-lookup"><span data-stu-id="edb1e-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="edb1e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edb1e-115">See also</span></span>

- [<span data-ttu-id="edb1e-116">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="edb1e-116">XML Comment Tags</span></span>](index.md)
