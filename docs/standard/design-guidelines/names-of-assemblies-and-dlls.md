---
title: 程序集和 DLL 的名称
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 138ae8154b0d10fb813f0c98ceb7c58a2471b780
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291950"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="40a8e-102">程序集和 DLL 的名称</span><span class="sxs-lookup"><span data-stu-id="40a8e-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="40a8e-103">程序集是托管代码程序的部署和标识单元。</span><span class="sxs-lookup"><span data-stu-id="40a8e-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="40a8e-104">尽管程序集可跨一个或多个文件，但通常程序集与 DLL 相互映射。</span><span class="sxs-lookup"><span data-stu-id="40a8e-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="40a8e-105">因此，本节仅介绍 DLL 命名约定，然后可以将其映射到程序集命名约定。</span><span class="sxs-lookup"><span data-stu-id="40a8e-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="40a8e-106">✔️为程序集 Dll 选择名称，这些名称建议了大块功能，如 System.object。</span><span class="sxs-lookup"><span data-stu-id="40a8e-106">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="40a8e-107">程序集和 DLL 的名称不必与命名空间名称对应，但在命名程序集时遵循命名空间名称是合理的。</span><span class="sxs-lookup"><span data-stu-id="40a8e-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="40a8e-108">合理的经验法则是基于程序集中包含的命名空间的公共前缀来命名 DLL。</span><span class="sxs-lookup"><span data-stu-id="40a8e-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="40a8e-109">例如，可以调用具有两个命名空间和的程序集 `MyCompany.MyTechnology.FirstFeature` `MyCompany.MyTechnology.SecondFeature` `MyCompany.MyTechnology.dll` 。</span><span class="sxs-lookup"><span data-stu-id="40a8e-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="40a8e-110">✔️考虑根据以下模式命名 Dll：</span><span class="sxs-lookup"><span data-stu-id="40a8e-110">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="40a8e-111">其中 `<Component>` 包含一个或多个以句点分隔的子句。</span><span class="sxs-lookup"><span data-stu-id="40a8e-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="40a8e-112">例如：</span><span class="sxs-lookup"><span data-stu-id="40a8e-112">For example:</span></span>

 <span data-ttu-id="40a8e-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="40a8e-113">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="40a8e-114">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="40a8e-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="40a8e-115">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="40a8e-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="40a8e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40a8e-116">See also</span></span>

- [<span data-ttu-id="40a8e-117">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="40a8e-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="40a8e-118">命名准则</span><span class="sxs-lookup"><span data-stu-id="40a8e-118">Naming Guidelines</span></span>](naming-guidelines.md)
