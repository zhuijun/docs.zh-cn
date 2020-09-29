---
description: -preferreduilang（C# 编译器选项）
title: -preferreduilang（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 490f5926fb50cfdae740b7749d72ea6c9a1f8cc9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193811"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="9808b-103">-preferreduilang（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="9808b-103">-preferreduilang (C# Compiler Options)</span></span>

<span data-ttu-id="9808b-104">通过使用 `-preferreduilang` 编译器选项，可指定 C# 编译器显示输出的语言，如错误消息。</span><span class="sxs-lookup"><span data-stu-id="9808b-104">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9808b-105">语法</span><span class="sxs-lookup"><span data-stu-id="9808b-105">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="9808b-106">自变量</span><span class="sxs-lookup"><span data-stu-id="9808b-106">Arguments</span></span>  

 `language`  
 <span data-ttu-id="9808b-107">用于编译器输出的语言的[语言名称](/windows/desktop/Intl/language-names)。</span><span class="sxs-lookup"><span data-stu-id="9808b-107">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9808b-108">备注</span><span class="sxs-lookup"><span data-stu-id="9808b-108">Remarks</span></span>  

 <span data-ttu-id="9808b-109">可以使用 `-preferreduilang` 编译器选项指定 C# 编译器用于错误消息和其他命令行输出的语言。</span><span class="sxs-lookup"><span data-stu-id="9808b-109">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="9808b-110">如果未安装针对该语言的语言包，将改用操作系统的语言设置，而不会报告错误。</span><span class="sxs-lookup"><span data-stu-id="9808b-110">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="9808b-111">要求</span><span class="sxs-lookup"><span data-stu-id="9808b-111">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9808b-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9808b-112">See also</span></span>

- [<span data-ttu-id="9808b-113">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="9808b-113">C# Compiler Options</span></span>](./index.md)
