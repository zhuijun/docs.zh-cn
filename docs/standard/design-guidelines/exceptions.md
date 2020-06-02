---
title: 异常设计准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: d7580d4d3953b279824bba76b44c4134a7293b7a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289767"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="94aca-102">异常设计准则</span><span class="sxs-lookup"><span data-stu-id="94aca-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="94aca-103">与基于返回值的错误报告相比，异常处理具有很多优点。</span><span class="sxs-lookup"><span data-stu-id="94aca-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="94aca-104">优秀的框架设计可帮助应用程序开发人员实现异常的好处。</span><span class="sxs-lookup"><span data-stu-id="94aca-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="94aca-105">本部分讨论异常的优点，并提供有效使用方法的指导原则。</span><span class="sxs-lookup"><span data-stu-id="94aca-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94aca-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="94aca-106">In This Section</span></span>  
 [<span data-ttu-id="94aca-107">异常引发</span><span class="sxs-lookup"><span data-stu-id="94aca-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="94aca-108">使用标准异常类型</span><span class="sxs-lookup"><span data-stu-id="94aca-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="94aca-109">异常和性能</span><span class="sxs-lookup"><span data-stu-id="94aca-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="94aca-110">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="94aca-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="94aca-111">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="94aca-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94aca-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94aca-112">See also</span></span>

- [<span data-ttu-id="94aca-113">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="94aca-113">Framework Design Guidelines</span></span>](index.md)
