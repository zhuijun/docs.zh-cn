---
title: 如何：释放系统资源
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403493"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="aa7f8-102">如何：释放系统资源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa7f8-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="aa7f8-103">您可以使用 `Using` 块来保证系统在代码退出块时释放资源。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="aa7f8-104">如果你使用的系统资源占用大量内存，或者其他组件也想要使用，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="aa7f8-105">使用数据库连接完成代码时释放数据库连接</span><span class="sxs-lookup"><span data-stu-id="aa7f8-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="aa7f8-106">请确保在源文件开头包含数据库连接的相应[Imports 语句（.Net 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) （在本例中为 <xref:System.Data.SqlClient> ）。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="aa7f8-107">`Using`使用和语句创建块 `Using` `End Using` 。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="aa7f8-108">在块中，放置用于处理数据库连接的代码。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="aa7f8-109">声明连接并在语句中创建其实例 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="aa7f8-110">无论退出块的方式如何（包括未经处理的异常的情况），系统都将释放资源。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="aa7f8-111">请注意，不能 `sqc` 从块外部访问 `Using` ，因为它的作用域限制为块。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="aa7f8-112">您可以对系统资源（如文件句柄或 COM 包装）使用这种方法。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="aa7f8-113">`Using`当你希望在退出块后，请使用块来确保其他组件可以使用该资源 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="aa7f8-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7f8-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa7f8-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="aa7f8-115">控制流</span><span class="sxs-lookup"><span data-stu-id="aa7f8-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="aa7f8-116">决策结构</span><span class="sxs-lookup"><span data-stu-id="aa7f8-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="aa7f8-117">循环结构</span><span class="sxs-lookup"><span data-stu-id="aa7f8-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="aa7f8-118">其他控件结构</span><span class="sxs-lookup"><span data-stu-id="aa7f8-118">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="aa7f8-119">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="aa7f8-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="aa7f8-120">Using 语句</span><span class="sxs-lookup"><span data-stu-id="aa7f8-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
