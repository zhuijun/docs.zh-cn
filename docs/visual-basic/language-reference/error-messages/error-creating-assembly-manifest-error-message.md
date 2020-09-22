---
title: 创建程序集清单时出错：<error message>
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: e90ad1905123a3c5426ada15e21179abe5c078ab
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874402"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="d131f-102">创建程序集清单时出错：\<error message></span><span class="sxs-lookup"><span data-stu-id="d131f-102">Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="d131f-103">Visual Basic 编译器调用程序集链接器 ( # A0 （也称为 Alink) ）以生成包含清单的程序集。</span><span class="sxs-lookup"><span data-stu-id="d131f-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="d131f-104">该链接器已报告在创建程序集的预发出阶段中出错。</span><span class="sxs-lookup"><span data-stu-id="d131f-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="d131f-105">如果指定的密钥文件或密钥容器有问题，就可能发生错误。</span><span class="sxs-lookup"><span data-stu-id="d131f-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="d131f-106">若要对程序集进行完全签名，必须提供包含公钥和私钥信息的有效密钥文件。</span><span class="sxs-lookup"><span data-stu-id="d131f-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="d131f-107">若要延迟对程序集的签名，必须选择“仅延迟签名”复选框，并提供包含公钥信息的有效密钥文件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d131f-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="d131f-108">当程序集为延迟签名时，不需要使用私有密钥。</span><span class="sxs-lookup"><span data-stu-id="d131f-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="d131f-109">有关详细信息，请参阅[操作说明：使用强名称为程序集签名](../../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="d131f-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="d131f-110">**错误 ID：** BC30140</span><span class="sxs-lookup"><span data-stu-id="d131f-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d131f-111">更正此错误</span><span class="sxs-lookup"><span data-stu-id="d131f-111">To correct this error</span></span>  
  
1. <span data-ttu-id="d131f-112">检查引用的错误消息并参考 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)主题。</span><span class="sxs-lookup"><span data-stu-id="d131f-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="d131f-113">对于错误 AL1019 进一步的说明和建议</span><span class="sxs-lookup"><span data-stu-id="d131f-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="d131f-114">如果仍然出现错误，则收集有关该情况的信息并通知 Microsoft 产品支持服务。</span><span class="sxs-lookup"><span data-stu-id="d131f-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d131f-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d131f-115">See also</span></span>

- [<span data-ttu-id="d131f-116">如何：使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="d131f-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="d131f-117">“项目设计器”-&gt;“签名”页</span><span class="sxs-lookup"><span data-stu-id="d131f-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="d131f-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="d131f-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="d131f-119">与我们交流</span><span class="sxs-lookup"><span data-stu-id="d131f-119">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
