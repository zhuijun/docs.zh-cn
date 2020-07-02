---
title: 如何：与其他应用程序共享程序集
description: 了解如何与 .NET 中的其他应用程序共享程序集。 程序集可以专用（默认），也可以共享。 若要共享程序集，请将其放置在 GAC 中。
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 9cef25059968875f17ce5dc77b04c44a2f3945f6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104648"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="0cebb-105">如何：与其他应用程序共享程序集</span><span class="sxs-lookup"><span data-stu-id="0cebb-105">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="0cebb-106">程序集可以是私有或共享程序集：默认情况下，大多数简单程序都包含一个私有程序集，因为它们并不打算由其他应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="0cebb-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="0cebb-107">若要与其他应用程序共享程序集，则必须将它放置在[全局程序集缓存 (GAC)](gac.md) 中。</span><span class="sxs-lookup"><span data-stu-id="0cebb-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="0cebb-108">共享程序集：</span><span class="sxs-lookup"><span data-stu-id="0cebb-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="0cebb-109">创建程序集。</span><span class="sxs-lookup"><span data-stu-id="0cebb-109">Create your assembly.</span></span> <span data-ttu-id="0cebb-110">有关详细信息，请参阅[创建程序集](../../standard/assembly/create.md)。</span><span class="sxs-lookup"><span data-stu-id="0cebb-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="0cebb-111">向程序集分配强名称。</span><span class="sxs-lookup"><span data-stu-id="0cebb-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="0cebb-112">有关详细信息，请参阅[如何：使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="0cebb-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="0cebb-113">将版本信息分配给程序集。</span><span class="sxs-lookup"><span data-stu-id="0cebb-113">Assign version information to your assembly.</span></span> <span data-ttu-id="0cebb-114">有关详细信息，请参阅[程序集版本控制](../../standard/assembly/versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="0cebb-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="0cebb-115">将程序集添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="0cebb-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="0cebb-116">有关详细信息，请参阅[如何：将程序集安装到全局程序集缓存](install-assembly-into-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="0cebb-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="0cebb-117">从其他应用程序访问该程序集中包含的类型。</span><span class="sxs-lookup"><span data-stu-id="0cebb-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="0cebb-118">有关详细信息，请参阅[如何：引用具有强名称的程序集](../../standard/assembly/reference-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="0cebb-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cebb-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="0cebb-119">See also</span></span>

- [<span data-ttu-id="0cebb-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0cebb-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="0cebb-121">编程概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cebb-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="0cebb-122">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="0cebb-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
