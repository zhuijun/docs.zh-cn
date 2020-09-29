---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: b489a164e56a5e3bdbf7e3cdf24ec330fadedf38
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097548"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="498c4-102">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498c4-102">-reference (Visual Basic)</span></span>

<span data-ttu-id="498c4-103">使编译器让指定程序集中的类型信息可供当前正在编译的项目使用。</span><span class="sxs-lookup"><span data-stu-id="498c4-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="498c4-104">语法</span><span class="sxs-lookup"><span data-stu-id="498c4-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="498c4-105">or</span><span class="sxs-lookup"><span data-stu-id="498c4-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="498c4-106">自变量</span><span class="sxs-lookup"><span data-stu-id="498c4-106">Arguments</span></span>  
  
|<span data-ttu-id="498c4-107">术语</span><span class="sxs-lookup"><span data-stu-id="498c4-107">Term</span></span>|<span data-ttu-id="498c4-108">定义</span><span class="sxs-lookup"><span data-stu-id="498c4-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="498c4-109">必需。</span><span class="sxs-lookup"><span data-stu-id="498c4-109">Required.</span></span> <span data-ttu-id="498c4-110">程序集文件名的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="498c4-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="498c4-111">如果文件名包含空格，则将名称括在引号内。</span><span class="sxs-lookup"><span data-stu-id="498c4-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="498c4-112">备注</span><span class="sxs-lookup"><span data-stu-id="498c4-112">Remarks</span></span>  

 <span data-ttu-id="498c4-113">导入的文件必须包含程序集元数据。</span><span class="sxs-lookup"><span data-stu-id="498c4-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="498c4-114">仅公共类型在程序集外部可见。</span><span class="sxs-lookup"><span data-stu-id="498c4-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="498c4-115">[-addmodule](addmodule.md) 选项从模块导入元数据。</span><span class="sxs-lookup"><span data-stu-id="498c4-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="498c4-116">如果引用的程序集（程序集 A）引用了另一个程序集（程序集 B），那么在下列情况下需要引用程序集 B：</span><span class="sxs-lookup"><span data-stu-id="498c4-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="498c4-117">程序集 A 中的类型继承自程序集 B 中的类型或实现程序集 B 中的接口。</span><span class="sxs-lookup"><span data-stu-id="498c4-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="498c4-118">调用具有程序集 B 中的返回类型或参数类型的字段、属性、事件或方法。</span><span class="sxs-lookup"><span data-stu-id="498c4-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="498c4-119">使用 [-libpath](libpath.md) 指定一个或多个程序集引用所在的目录。</span><span class="sxs-lookup"><span data-stu-id="498c4-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="498c4-120">为了使编译器能够识别程序集（而非模块）中的类型，必须强制其解析该类型。</span><span class="sxs-lookup"><span data-stu-id="498c4-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="498c4-121">如何执行此操作的一个示例是定义类型的实例。</span><span class="sxs-lookup"><span data-stu-id="498c4-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="498c4-122">还可以使用其他方法来为编译器解析程序集中的类型名称。</span><span class="sxs-lookup"><span data-stu-id="498c4-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="498c4-123">例如，如果从程序集中的类型继承，则编译器将知道类型名称。</span><span class="sxs-lookup"><span data-stu-id="498c4-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="498c4-124">默认情况下使用 Vbc.rsp 响应文件，该文件引用常用的 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="498c4-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="498c4-125">如果希望编译器不要使用 Vbc.rsp，请使用 `-noconfig`。</span><span class="sxs-lookup"><span data-stu-id="498c4-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="498c4-126">`-reference` 的缩写形式是 `-r`。</span><span class="sxs-lookup"><span data-stu-id="498c4-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="498c4-127">示例</span><span class="sxs-lookup"><span data-stu-id="498c4-127">Example</span></span>  

 <span data-ttu-id="498c4-128">下面的命令编译源文件 `Input.vb` 并引用来自 `Metad1.dll` 和 `Metad2.dll` 的程序集以生成 `Out.exe`。</span><span class="sxs-lookup"><span data-stu-id="498c4-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="498c4-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="498c4-129">See also</span></span>

- [<span data-ttu-id="498c4-130">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="498c4-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="498c4-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="498c4-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="498c4-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498c4-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="498c4-133">Public</span><span class="sxs-lookup"><span data-stu-id="498c4-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="498c4-134">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="498c4-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
