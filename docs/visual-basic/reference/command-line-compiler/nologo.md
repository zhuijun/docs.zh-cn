---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360457"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="7fb44-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fb44-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="7fb44-103">在编译期间禁止显示版权标志和信息性消息。</span><span class="sxs-lookup"><span data-stu-id="7fb44-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb44-104">语法</span><span class="sxs-lookup"><span data-stu-id="7fb44-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="7fb44-105">备注</span><span class="sxs-lookup"><span data-stu-id="7fb44-105">Remarks</span></span>  
 <span data-ttu-id="7fb44-106">如果指定 `-nologo`，编译器不会显示版权标志。</span><span class="sxs-lookup"><span data-stu-id="7fb44-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="7fb44-107">默认情况，`-nologo` 是无效的。</span><span class="sxs-lookup"><span data-stu-id="7fb44-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fb44-108">`-nologo` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="7fb44-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fb44-109">示例</span><span class="sxs-lookup"><span data-stu-id="7fb44-109">Example</span></span>  
 <span data-ttu-id="7fb44-110">以下代码编译 `T2.vb` 并且不显示任何版权标志。</span><span class="sxs-lookup"><span data-stu-id="7fb44-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fb44-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="7fb44-111">See also</span></span>

- [<span data-ttu-id="7fb44-112">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="7fb44-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7fb44-113">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="7fb44-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
