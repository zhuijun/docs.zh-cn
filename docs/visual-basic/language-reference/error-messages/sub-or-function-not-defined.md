---
title: 未定义 Sub 或 Function
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 24e290ce1193cd6bc6a0ec8985902576332423f2
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870525"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="04839-102">未定义 Sub 或 Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04839-102">Sub or Function not defined (Visual Basic)</span></span>

<span data-ttu-id="04839-103">`Sub` `Function` 若要调用，必须定义或。</span><span class="sxs-lookup"><span data-stu-id="04839-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="04839-104">此错误的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="04839-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="04839-105">错误的过程名称。</span><span class="sxs-lookup"><span data-stu-id="04839-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="04839-106">尝试从另一个项目调用过程，而无需在 " **引用** " 对话框中显式添加对该项目的引用。</span><span class="sxs-lookup"><span data-stu-id="04839-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="04839-107">指定对调用过程不可见的过程。</span><span class="sxs-lookup"><span data-stu-id="04839-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="04839-108">声明 Windows 动态链接库 (DLL) 例程或 Macintosh 代码资源例程，该例程不在指定的库或代码资源中。</span><span class="sxs-lookup"><span data-stu-id="04839-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04839-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="04839-109">To correct this error</span></span>  
  
1. <span data-ttu-id="04839-110">请确保过程名称拼写正确。</span><span class="sxs-lookup"><span data-stu-id="04839-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="04839-111">在 " **引用** " 对话框中找到包含要调用的过程的项目的名称。</span><span class="sxs-lookup"><span data-stu-id="04839-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="04839-112">如果未显示，请单击 " **浏览** " 按钮进行搜索。</span><span class="sxs-lookup"><span data-stu-id="04839-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="04839-113">选中项目名称左侧的复选框，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="04839-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="04839-114">检查例程的名称。</span><span class="sxs-lookup"><span data-stu-id="04839-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04839-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04839-115">See also</span></span>

- [<span data-ttu-id="04839-116">错误类型</span><span class="sxs-lookup"><span data-stu-id="04839-116">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="04839-117">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="04839-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="04839-118">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="04839-118">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="04839-119">Function 语句</span><span class="sxs-lookup"><span data-stu-id="04839-119">Function Statement</span></span>](../statements/function-statement.md)
