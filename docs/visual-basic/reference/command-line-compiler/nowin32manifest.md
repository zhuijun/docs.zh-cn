---
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: d9323cd541eaf611551de90e58a181f6915fad89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397449"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="cff46-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cff46-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="cff46-103">指示编译器不在可执行文件中嵌入任何应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="cff46-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff46-104">语法</span><span class="sxs-lookup"><span data-stu-id="cff46-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="cff46-105">备注</span><span class="sxs-lookup"><span data-stu-id="cff46-105">Remarks</span></span>  
 <span data-ttu-id="cff46-106">使用此选项时，除非在 Win32 资源文件或以后的生成步骤中提供应用程序清单，否则应用程序会受到 Windows Vista 上虚拟化的影响。</span><span class="sxs-lookup"><span data-stu-id="cff46-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="cff46-107">有关虚拟化的详细信息，请参阅 [Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="cff46-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="cff46-108">有关清单创建的详细信息，请参阅 [-win32manifest (Visual Basic)](win32manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="cff46-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff46-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="cff46-109">See also</span></span>

- [<span data-ttu-id="cff46-110">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="cff46-110">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="cff46-111">“项目设计器”->“应用程序”页 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cff46-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
