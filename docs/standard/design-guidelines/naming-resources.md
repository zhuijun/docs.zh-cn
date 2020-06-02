---
title: 命名资源
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 762ba99c4751ba40f5f33e99455cf950af35cdf6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290144"
---
# <a name="naming-resources"></a><span data-ttu-id="565b4-102">命名资源</span><span class="sxs-lookup"><span data-stu-id="565b4-102">Naming Resources</span></span>
<span data-ttu-id="565b4-103">由于可以通过某些对象来引用可本地化的资源，就像它们是属性一样，因此资源的命名准则与属性准则类似。</span><span class="sxs-lookup"><span data-stu-id="565b4-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="565b4-104">✔️在资源键中使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="565b4-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="565b4-105">✔️提供描述性而不是短标识符。</span><span class="sxs-lookup"><span data-stu-id="565b4-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="565b4-106">❌不要使用主要 CLR 语言的特定于语言的关键字。</span><span class="sxs-lookup"><span data-stu-id="565b4-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="565b4-107">✔️在命名资源中仅使用字母数字字符和下划线。</span><span class="sxs-lookup"><span data-stu-id="565b4-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="565b4-108">✔️对异常消息资源使用以下命名约定。</span><span class="sxs-lookup"><span data-stu-id="565b4-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="565b4-109">资源标识符应为异常类型名称和异常的简短标识符：</span><span class="sxs-lookup"><span data-stu-id="565b4-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="565b4-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="565b4-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="565b4-111">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="565b4-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="565b4-112">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="565b4-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="565b4-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="565b4-113">See also</span></span>

- [<span data-ttu-id="565b4-114">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="565b4-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="565b4-115">命名准则</span><span class="sxs-lookup"><span data-stu-id="565b4-115">Naming Guidelines</span></span>](naming-guidelines.md)
