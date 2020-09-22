---
title: 需要对程序集“<assemblyname>”（包含基类“<classname>”）的引用
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: 07c09d0dfcb374b974fbda9099c4e85d6d054753
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870912"
---
# <a name="reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="78486-102">需要对程序集“\<assemblyname>”（包含基类“\<classname>”）的引用</span><span class="sxs-lookup"><span data-stu-id="78486-102">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="78486-103">需要对 \<assemblyname> 包含基类 "" 的程序集 "" 的引用 \<classname> 。</span><span class="sxs-lookup"><span data-stu-id="78486-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="78486-104">请向项目中添加一个。</span><span class="sxs-lookup"><span data-stu-id="78486-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="78486-105">该类是在动态链接库 (DLL) 或未在项目中直接引用的程序集中定义的。</span><span class="sxs-lookup"><span data-stu-id="78486-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="78486-106">如果类是在多个 DLL 或程序集中定义的，则 Visual Basic 编译器需要引用以避免多义性。</span><span class="sxs-lookup"><span data-stu-id="78486-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="78486-107">**错误 ID：** BC30007</span><span class="sxs-lookup"><span data-stu-id="78486-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78486-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="78486-108">To correct this error</span></span>  
  
- <span data-ttu-id="78486-109">将未引用的 DLL 或程序集名称包括在项目引用中。</span><span class="sxs-lookup"><span data-stu-id="78486-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78486-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78486-110">See also</span></span>

- [<span data-ttu-id="78486-111">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="78486-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="78486-112">Troubleshooting Broken References</span><span class="sxs-lookup"><span data-stu-id="78486-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
