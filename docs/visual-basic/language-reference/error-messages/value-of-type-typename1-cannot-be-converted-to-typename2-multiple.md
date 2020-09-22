---
title: 类型“<typename1>”的值无法转换为“<typename2>”（多个文件引用）
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 4b74fdc5584fd296d4bbe36034920d4b467dbb7a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875076"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="b055a-102">类型“\<typename1>”的值无法转换为“\<typename2>”（多个文件引用）</span><span class="sxs-lookup"><span data-stu-id="b055a-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>

<span data-ttu-id="b055a-103">类型 "" 的值 \<typename1> 无法转换为 " \<typename2> "。</span><span class="sxs-lookup"><span data-stu-id="b055a-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="b055a-104">类型不匹配可能是由于将对项目 "" 中 "" 的文件引用 \<filepath1> \<projectname1> 与项目 "" 中 "" 的文件引用混合而造成的 \<filepath2> \<projectname2> 。</span><span class="sxs-lookup"><span data-stu-id="b055a-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="b055a-105">如果两个程序集完全相同，请尝试更换这些引用，以确保两个引用都来自相同的位置。</span><span class="sxs-lookup"><span data-stu-id="b055a-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="b055a-106">在项目对一个程序集进行多个文件引用的情况下，编译器无法保证可以将一种类型转换为另一种类型。</span><span class="sxs-lookup"><span data-stu-id="b055a-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="b055a-107">每个文件引用指定项目的输出文件的文件路径和名称 (通常) 的 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="b055a-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="b055a-108">编译器无法保证输出文件来自相同的源，或它们表示同一程序集的相同版本。</span><span class="sxs-lookup"><span data-stu-id="b055a-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="b055a-109">因此，它无法保证不同引用中的类型具有相同的类型，甚至可以将其转换为另一种类型。</span><span class="sxs-lookup"><span data-stu-id="b055a-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="b055a-110">如果知道引用的程序集具有相同的程序集标识，则可以使用单个文件引用。</span><span class="sxs-lookup"><span data-stu-id="b055a-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="b055a-111">*程序集标识*包括程序集的名称、版本、公钥（如果有）和区域性。</span><span class="sxs-lookup"><span data-stu-id="b055a-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="b055a-112">此信息唯一地标识该程序集。</span><span class="sxs-lookup"><span data-stu-id="b055a-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="b055a-113">**错误 ID：** BC30961</span><span class="sxs-lookup"><span data-stu-id="b055a-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b055a-114">更正此错误</span><span class="sxs-lookup"><span data-stu-id="b055a-114">To correct this error</span></span>  
  
- <span data-ttu-id="b055a-115">如果引用的程序集具有相同的程序集标识，则删除或替换其中一个文件引用，以便只有一个文件引用。</span><span class="sxs-lookup"><span data-stu-id="b055a-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
- <span data-ttu-id="b055a-116">如果引用的程序集不具有相同的程序集标识，则更改您的代码，使其不会尝试将一种类型转换为另一种类型。</span><span class="sxs-lookup"><span data-stu-id="b055a-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b055a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b055a-117">See also</span></span>

- [<span data-ttu-id="b055a-118">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="b055a-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="b055a-119">管理项目中的引用</span><span class="sxs-lookup"><span data-stu-id="b055a-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
