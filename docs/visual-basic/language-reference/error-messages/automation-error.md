---
title: 自动错误
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: d62ba57db8bffefb2cfebed705251d87fe285602
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409889"
---
# <a name="automation-error"></a><span data-ttu-id="25372-102">自动错误</span><span class="sxs-lookup"><span data-stu-id="25372-102">Automation error</span></span>

<span data-ttu-id="25372-103">执行方法或者获取或设置对象变量的属性时发生错误。</span><span class="sxs-lookup"><span data-stu-id="25372-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="25372-104">错误由创建该对象的应用程序报告。</span><span class="sxs-lookup"><span data-stu-id="25372-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25372-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="25372-105">To correct this error</span></span>  
  
1. <span data-ttu-id="25372-106">检查 `Err` 对象的属性，以确定错误来源和错误性质。</span><span class="sxs-lookup"><span data-stu-id="25372-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="25372-107">在紧邻访问语句之前使用 `On Error Resume Next` 语句，然后检查紧邻访问语句之后是否存在错误。</span><span class="sxs-lookup"><span data-stu-id="25372-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25372-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25372-108">See also</span></span>

- [<span data-ttu-id="25372-109">错误类型</span><span class="sxs-lookup"><span data-stu-id="25372-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="25372-110">与我们交流</span><span class="sxs-lookup"><span data-stu-id="25372-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
