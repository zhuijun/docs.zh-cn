---
description: -nowin32manifest（C# 编译器选项）
title: -nowin32manifest（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 13bbee66901149d54632d9b164431f8898cdf52e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193993"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="219e0-103">-nowin32manifest（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="219e0-103">-nowin32manifest (C# Compiler Options)</span></span>

<span data-ttu-id="219e0-104">使用 -nowin32manifest 选项可指示编译器不将任何应用程序清单嵌入到可执行文件中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="219e0-104">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219e0-105">语法</span><span class="sxs-lookup"><span data-stu-id="219e0-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="219e0-106">备注</span><span class="sxs-lookup"><span data-stu-id="219e0-106">Remarks</span></span>  

 <span data-ttu-id="219e0-107">使用此选项时，除非在 Win32 资源文件或以后的生成步骤中提供应用程序清单，否则应用程序会受到 Windows Vista 上虚拟化的影响。</span><span class="sxs-lookup"><span data-stu-id="219e0-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="219e0-108">在 Visual Studio 的“应用程序属性”\*\*\*\* 页中，通过在“清单”下拉列表中选择“创建不带清单的应用程序”选项来设置此选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="219e0-108">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="219e0-109">有关详细信息，请参阅[“项目设计器”->“应用程序”页 (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="219e0-109">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="219e0-110">有关创建清单的详细信息，请参阅 [-win32manifest（C# 编译器选项）](./win32manifest-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="219e0-110">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219e0-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="219e0-111">See also</span></span>

- [<span data-ttu-id="219e0-112">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="219e0-112">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="219e0-113">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="219e0-113">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
