---
title: <message>此错误也可能是由于将程序集“<assemblyname>”的文件引用与项目引用混合使用所造成的
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397254"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="93bdf-102">\<message>此错误也可能是由于将程序集“\<assemblyname>”的文件引用与项目引用混合使用所造成的</span><span class="sxs-lookup"><span data-stu-id="93bdf-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>
<span data-ttu-id="93bdf-103">\<message>此错误还可能是由于将文件引用与程序集 "的项目引用混合而造成的 \<assemblyname> 。</span><span class="sxs-lookup"><span data-stu-id="93bdf-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="93bdf-104">在这种情况下，尝试将项目 "" 中对 "" 的文件引用替换为 \<assemblyfilename> \<projectname1> 对 "" 的项目引用 \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="93bdf-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="93bdf-105">项目中的代码访问另一个项目的成员，但你的解决方案配置不允许 Visual Basic 编译器解析引用。</span><span class="sxs-lookup"><span data-stu-id="93bdf-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="93bdf-106">若要访问另一个程序集中定义的类型，Visual Basic 编译器必须具有对该程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="93bdf-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="93bdf-107">此引用必须单一、明确，不会导致项目之间循环引用。</span><span class="sxs-lookup"><span data-stu-id="93bdf-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="93bdf-108">**错误 ID：** BC30971</span><span class="sxs-lookup"><span data-stu-id="93bdf-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93bdf-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="93bdf-109">To correct this error</span></span>  
  
1. <span data-ttu-id="93bdf-110">确定产生最佳程序集引用的项目。</span><span class="sxs-lookup"><span data-stu-id="93bdf-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="93bdf-111">为便于确定，你可以使用文件访问轻松程度和更新频率等条件。</span><span class="sxs-lookup"><span data-stu-id="93bdf-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="93bdf-112">在项目属性中，添加对包含某程序集的项目的引用，该程序集定义正在使用的类型。</span><span class="sxs-lookup"><span data-stu-id="93bdf-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bdf-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93bdf-113">See also</span></span>

- [<span data-ttu-id="93bdf-114">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="93bdf-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="93bdf-115">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="93bdf-115">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="93bdf-116">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="93bdf-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="93bdf-117">Troubleshooting Broken References</span><span class="sxs-lookup"><span data-stu-id="93bdf-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
