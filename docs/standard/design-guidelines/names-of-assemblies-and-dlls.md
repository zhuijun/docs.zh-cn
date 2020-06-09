---
title: 程序集和 DLL 的名称
description: 了解如何命名程序集和动态链接库（Dll）。 程序集可跨一个或多个文件，但它通常与 DLL 相互映射。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: de7ce3ee774d4598521d7156d0d660c3fe30154c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594473"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="b2262-104">程序集和 DLL 的名称</span><span class="sxs-lookup"><span data-stu-id="b2262-104">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="b2262-105">程序集是托管代码程序的部署和标识单元。</span><span class="sxs-lookup"><span data-stu-id="b2262-105">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="b2262-106">尽管程序集可跨一个或多个文件，但通常程序集与 DLL 相互映射。</span><span class="sxs-lookup"><span data-stu-id="b2262-106">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="b2262-107">因此，本节仅介绍 DLL 命名约定，然后可以将其映射到程序集命名约定。</span><span class="sxs-lookup"><span data-stu-id="b2262-107">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="b2262-108">✔️为程序集 Dll 选择名称，这些名称建议了大块功能，如 System.object。</span><span class="sxs-lookup"><span data-stu-id="b2262-108">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="b2262-109">程序集和 DLL 的名称不必与命名空间名称对应，但在命名程序集时遵循命名空间名称是合理的。</span><span class="sxs-lookup"><span data-stu-id="b2262-109">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="b2262-110">合理的经验法则是基于程序集中包含的命名空间的公共前缀来命名 DLL。</span><span class="sxs-lookup"><span data-stu-id="b2262-110">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="b2262-111">例如，可以调用具有两个命名空间和的程序集 `MyCompany.MyTechnology.FirstFeature` `MyCompany.MyTechnology.SecondFeature` `MyCompany.MyTechnology.dll` 。</span><span class="sxs-lookup"><span data-stu-id="b2262-111">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="b2262-112">✔️考虑根据以下模式命名 Dll：</span><span class="sxs-lookup"><span data-stu-id="b2262-112">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="b2262-113">其中 `<Component>` 包含一个或多个以句点分隔的子句。</span><span class="sxs-lookup"><span data-stu-id="b2262-113">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="b2262-114">例如：</span><span class="sxs-lookup"><span data-stu-id="b2262-114">For example:</span></span>

 <span data-ttu-id="b2262-115">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="b2262-115">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="b2262-116">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="b2262-116">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b2262-117">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="b2262-117">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b2262-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2262-118">See also</span></span>

- [<span data-ttu-id="b2262-119">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="b2262-119">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="b2262-120">命名准则</span><span class="sxs-lookup"><span data-stu-id="b2262-120">Naming Guidelines</span></span>](naming-guidelines.md)
