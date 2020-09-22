---
title: 需要引用包含类型“<assemblyidentity>”的程序集“<typename>”，但由于项目“<projectname1>”和“<projectname2>”之间存在二义性，未能找到合适的引用
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: ffc6b3c180c86abe272d56d0ecf3042d8181da59
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870896"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="c8a9e-102">需要引用包含类型“\<assemblyidentity>”的程序集“\<typename>”，但由于项目“\<projectname1>”和“\<projectname2>”之间存在二义性，未能找到合适的引用</span><span class="sxs-lookup"><span data-stu-id="c8a9e-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>

<span data-ttu-id="c8a9e-103">表达式使用在项目外部定义的类型，如类、结构、接口、枚举或委托。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="c8a9e-104">但是，你具有对定义该类型的多个程序集的项目引用。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="c8a9e-105">引用的项目会生成名称相同的程序集。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="c8a9e-106">因此，编译器无法确定对要访问的类型使用哪一个程序集。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="c8a9e-107">若要访问另一个程序集中定义的类型，Visual Basic 编译器必须具有对该程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="c8a9e-108">此引用必须单一、明确，不会导致项目之间循环引用。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="c8a9e-109">**错误 ID：** BC30969</span><span class="sxs-lookup"><span data-stu-id="c8a9e-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8a9e-110">更正此错误</span><span class="sxs-lookup"><span data-stu-id="c8a9e-110">To correct this error</span></span>  
  
1. <span data-ttu-id="c8a9e-111">确定产生最佳程序集引用的项目。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="c8a9e-112">为便于确定，你可以使用文件访问轻松程度和更新频率等条件。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="c8a9e-113">在项目属性中，添加对包含某程序集的文件的引用，该程序集定义正在使用的类型。</span><span class="sxs-lookup"><span data-stu-id="c8a9e-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a9e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8a9e-114">See also</span></span>

- [<span data-ttu-id="c8a9e-115">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="c8a9e-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="c8a9e-116">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="c8a9e-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="c8a9e-117">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="c8a9e-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="c8a9e-118">Troubleshooting Broken References</span><span class="sxs-lookup"><span data-stu-id="c8a9e-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
