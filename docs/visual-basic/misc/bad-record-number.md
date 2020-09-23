---
title: 错误的记录号
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 8cbffc7714211fb10bedc3a73729eac59d98f0bb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086980"
---
# <a name="bad-record-number"></a><span data-ttu-id="478c0-102">错误的记录号</span><span class="sxs-lookup"><span data-stu-id="478c0-102">Bad record number</span></span>

<span data-ttu-id="478c0-103">`a FileGet`、`FilePut``FileGetObject` 或 `FilePutObject` 语句中的记录号小于或等于零。</span><span class="sxs-lookup"><span data-stu-id="478c0-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="478c0-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="478c0-104">To correct this error</span></span>  
  
1. <span data-ttu-id="478c0-105">检查用于生成记录号的计算。</span><span class="sxs-lookup"><span data-stu-id="478c0-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="478c0-106">验证包含记录号或用于计算记录号的变量的拼写。</span><span class="sxs-lookup"><span data-stu-id="478c0-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="478c0-107">拼写错误的变量名称将被隐式声明并初始化为零，除非在此模块中使用 `Option Explicit On` 。</span><span class="sxs-lookup"><span data-stu-id="478c0-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="478c0-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="478c0-108">See also</span></span>

- [<span data-ttu-id="478c0-109">Option Explicit 语句</span><span class="sxs-lookup"><span data-stu-id="478c0-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
