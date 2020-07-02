---
title: 如何：创建用户定义异常
description: 了解如何创建用户定义的异常，这是从 .NET 中异常基类派生的异常类层次结构的替代项。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: 14eb6246ba4347f33766f7dff36463f2bf996330
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662792"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="edcff-103">如何创建用户定义的异常</span><span class="sxs-lookup"><span data-stu-id="edcff-103">How to create user-defined exceptions</span></span>

<span data-ttu-id="edcff-104">.NET 可提供由基类 <xref:System.Exception> 最终派生的异常类层次结构。</span><span class="sxs-lookup"><span data-stu-id="edcff-104">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="edcff-105">然而，如果预定义的异常都不符合需求，可通过从 <xref:System.Exception> 类派生来创建自己的异常类。</span><span class="sxs-lookup"><span data-stu-id="edcff-105">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="edcff-106">创建自己的异常时，用户定义的异常类的名称需要以“Exception”一词结尾，并实现三个常见的构造函数，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="edcff-106">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="edcff-107">该示例定义名为 `EmployeeListNotFoundException` 的新异常类。</span><span class="sxs-lookup"><span data-stu-id="edcff-107">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="edcff-108">该类从 <xref:System.Exception> 派生，且包含三个构造函数。</span><span class="sxs-lookup"><span data-stu-id="edcff-108">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="edcff-109">使用远程处理时，必须确保所有用户定义的异常的元数据在服务器（被调用方）可用，在客户端（代理对象或调用方）也可用。</span><span class="sxs-lookup"><span data-stu-id="edcff-109">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="edcff-110">有关详细信息，请参阅[异常的最佳做法](best-practices-for-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="edcff-110">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edcff-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="edcff-111">See also</span></span>

- [<span data-ttu-id="edcff-112">异常</span><span class="sxs-lookup"><span data-stu-id="edcff-112">Exceptions</span></span>](index.md)
