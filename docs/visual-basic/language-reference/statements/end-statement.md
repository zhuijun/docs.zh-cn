---
title: End 语句
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 0c99b919b50701e93fab7caf5fb5d8b6b976d44b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865857"
---
# <a name="end-statement"></a><span data-ttu-id="388fe-102">End 语句</span><span class="sxs-lookup"><span data-stu-id="388fe-102">End Statement</span></span>

<span data-ttu-id="388fe-103">立即终止执行。</span><span class="sxs-lookup"><span data-stu-id="388fe-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388fe-104">语法</span><span class="sxs-lookup"><span data-stu-id="388fe-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="388fe-105">备注</span><span class="sxs-lookup"><span data-stu-id="388fe-105">Remarks</span></span>  

 <span data-ttu-id="388fe-106">可以将语句放 `End` 在过程中的任意位置，以强制整个应用程序停止运行。</span><span class="sxs-lookup"><span data-stu-id="388fe-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="388fe-107">`End` 关闭使用语句打开的所有文件 `Open` ，并清除应用程序的所有变量。</span><span class="sxs-lookup"><span data-stu-id="388fe-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="388fe-108">应用程序将立即关闭，因为没有任何其他程序保留对其对象的引用，并且没有任何代码正在运行。</span><span class="sxs-lookup"><span data-stu-id="388fe-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="388fe-109">`End`语句会突然停止代码执行，并且不会调用 `Dispose` 或 `Finalize` 方法或任何其他 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="388fe-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="388fe-110">其他程序持有的对象引用已失效。</span><span class="sxs-lookup"><span data-stu-id="388fe-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="388fe-111">如果 `End` 在或块中遇到语句 `Try` `Catch` ，控件不会传递给相应的 `Finally` 块。</span><span class="sxs-lookup"><span data-stu-id="388fe-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="388fe-112">`Stop`语句暂停执行，但与 `End` 此不同，它不会关闭任何文件或清除任何变量，除非在已编译的可执行文件 ( .exe) 文件中出现。</span><span class="sxs-lookup"><span data-stu-id="388fe-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="388fe-113">由于 `End` 终止了你的应用程序而不参与任何可能已打开的资源，因此，在使用该应用程序之前，你应尝试完全关闭。</span><span class="sxs-lookup"><span data-stu-id="388fe-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="388fe-114">例如，如果应用程序打开了任何窗体，则在控制到达语句之前应关闭它们 `End` 。</span><span class="sxs-lookup"><span data-stu-id="388fe-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="388fe-115">应 `End` 慎用，只需在需要立即停止时使用。</span><span class="sxs-lookup"><span data-stu-id="388fe-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="388fe-116">终止过程 ([返回语句](return-statement.md) 和 [退出语句](exit-statement.md) 的常规方法) 不仅完全关闭过程，而且还向调用代码授予完全关闭的机会。</span><span class="sxs-lookup"><span data-stu-id="388fe-116">The normal ways to terminate a procedure ([Return Statement](return-statement.md) and [Exit Statement](exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="388fe-117">例如，控制台应用程序可以直接 `Return` 从 `Main` 过程开始。</span><span class="sxs-lookup"><span data-stu-id="388fe-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="388fe-118">`End`语句 <xref:System.Environment.Exit%2A> <xref:System.Environment> 在命名空间中调用类的方法 <xref:System> 。</span><span class="sxs-lookup"><span data-stu-id="388fe-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="388fe-119"><xref:System.Environment.Exit%2A> 要求您具有 `UnmanagedCode` 权限。</span><span class="sxs-lookup"><span data-stu-id="388fe-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="388fe-120">否则， <xref:System.Security.SecurityException> 会发生错误。</span><span class="sxs-lookup"><span data-stu-id="388fe-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="388fe-121">后跟一个附加的关键字时， [end \<keyword> 语句](end-keyword-statement.md) 指定相应过程或块定义的末尾。</span><span class="sxs-lookup"><span data-stu-id="388fe-121">When followed by an additional keyword, [End \<keyword> Statement](end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="388fe-122">例如， `End Function` 终止过程的定义 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="388fe-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="388fe-123">示例</span><span class="sxs-lookup"><span data-stu-id="388fe-123">Example</span></span>  

 <span data-ttu-id="388fe-124">下面的示例使用 `End` 语句在用户请求代码的情况下终止代码执行。</span><span class="sxs-lookup"><span data-stu-id="388fe-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="388fe-125">智能设备开发人员说明</span><span class="sxs-lookup"><span data-stu-id="388fe-125">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="388fe-126">不支持此语句。</span><span class="sxs-lookup"><span data-stu-id="388fe-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388fe-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="388fe-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="388fe-128">Stop 语句</span><span class="sxs-lookup"><span data-stu-id="388fe-128">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="388fe-129">End \<keyword> 语句</span><span class="sxs-lookup"><span data-stu-id="388fe-129">End \<keyword> Statement</span></span>](end-keyword-statement.md)
