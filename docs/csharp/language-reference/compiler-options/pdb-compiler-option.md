---
description: -pdb（C# 编译器选项）
title: -pdb（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: ced1ee1f4f079830a032a628da96a389ba27da90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193850"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="0cb39-103">-pdb（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="0cb39-103">-pdb (C# Compiler Options)</span></span>

<span data-ttu-id="0cb39-104">-pdb 编译器选项指定调试符号文件的名称和位置\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0cb39-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb39-105">语法</span><span class="sxs-lookup"><span data-stu-id="0cb39-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0cb39-106">自变量</span><span class="sxs-lookup"><span data-stu-id="0cb39-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="0cb39-107">调试符号文件的名称和位置。</span><span class="sxs-lookup"><span data-stu-id="0cb39-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cb39-108">备注</span><span class="sxs-lookup"><span data-stu-id="0cb39-108">Remarks</span></span>  

 <span data-ttu-id="0cb39-109">指定 [-debug（C# 编译器选项）](./debug-compiler-option.md)后，编译器将在创建输出文件（.exe 或 .dll）的目录中创建 .pdb 文件，且名称与输出文件的名称相同。</span><span class="sxs-lookup"><span data-stu-id="0cb39-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="0cb39-110">-pdb 允许为 .pdb 文件指定非默认的文件名和位置\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0cb39-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="0cb39-111">不能在 Visual Studio 开发环境中设置此编译器选项，也不能以编程方式对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="0cb39-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cb39-112">示例</span><span class="sxs-lookup"><span data-stu-id="0cb39-112">Example</span></span>  

 <span data-ttu-id="0cb39-113">编译 `t.cs` 并创建名为 tt.pdb 的 .pdb 文件：</span><span class="sxs-lookup"><span data-stu-id="0cb39-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cb39-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0cb39-114">See also</span></span>

- [<span data-ttu-id="0cb39-115">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="0cb39-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0cb39-116">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="0cb39-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
