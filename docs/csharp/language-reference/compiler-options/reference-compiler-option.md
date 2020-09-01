---
description: -reference（C# 编译器选项）
title: -reference（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 7b84953f85545c0400c7136c258849f259e8b48a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124794"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="78b11-103">-reference（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="78b11-103">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="78b11-104">-reference 选项使编译器将指定文件中的[公共](../keywords/public.md)类型信息导入当前项目，从而使你可从指定的程序集文件中引用元数据。</span><span class="sxs-lookup"><span data-stu-id="78b11-104">The **-reference** option causes the compiler to import [public](../keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b11-105">语法</span><span class="sxs-lookup"><span data-stu-id="78b11-105">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="78b11-106">自变量</span><span class="sxs-lookup"><span data-stu-id="78b11-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="78b11-107">包含程序集清单的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="78b11-107">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="78b11-108">若要导入多个文件，请为每个文件包括一个单独的 -reference 选项。</span><span class="sxs-lookup"><span data-stu-id="78b11-108">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="78b11-109">一个有效的 C# 标识符，表示将包含程序集中所有命名空间的根命名空间。</span><span class="sxs-lookup"><span data-stu-id="78b11-109">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78b11-110">备注</span><span class="sxs-lookup"><span data-stu-id="78b11-110">Remarks</span></span>  
 <span data-ttu-id="78b11-111">若要从多个文件导入，请为每个文件包括一个 -reference 选项。</span><span class="sxs-lookup"><span data-stu-id="78b11-111">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="78b11-112">导入的文件必须包含一个清单；输出文件必须已使用[-target:module](./target-module-compiler-option.md) 以外的一个 [-target](./target-compiler-option.md) 选项进行了编译。</span><span class="sxs-lookup"><span data-stu-id="78b11-112">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](./target-compiler-option.md) options other than [-target:module](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="78b11-113">-r 是 -reference 的缩写形式 。</span><span class="sxs-lookup"><span data-stu-id="78b11-113">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="78b11-114">使用 [-addmodule](./addmodule-compiler-option.md) 从不包含程序集清单的输出文件中导入元数据。</span><span class="sxs-lookup"><span data-stu-id="78b11-114">Use [-addmodule](./addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="78b11-115">如果引用的程序集（程序集 A）引用了另一个程序集（程序集 B），那么在下列情况下需要引用程序集 B：</span><span class="sxs-lookup"><span data-stu-id="78b11-115">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="78b11-116">使用程序集 A 中的类型，该类型继承自程序集 B 中的类型或实现程序集 B 中的接口。</span><span class="sxs-lookup"><span data-stu-id="78b11-116">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="78b11-117">调用具有程序集 B 中的返回类型或参数类型的字段、属性、事件或方法。</span><span class="sxs-lookup"><span data-stu-id="78b11-117">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="78b11-118">使用 [-lib](./lib-compiler-option.md) 指定一个或多个程序集引用所在的目录。</span><span class="sxs-lookup"><span data-stu-id="78b11-118">Use [-lib](./lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="78b11-119">-Lib 主题还讨论了编译器在哪些目录中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="78b11-119">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="78b11-120">为使编译器可以识别程序集（而不是模块）中的某个类型，需要强制解析此类型，这可以通过定义此类型的实例来完成。</span><span class="sxs-lookup"><span data-stu-id="78b11-120">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="78b11-121">还可通过其他方法为编译器解析程序集中的类型名称：例如，如果从程序集中继承类型，编译器就能识别类型名称。</span><span class="sxs-lookup"><span data-stu-id="78b11-121">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="78b11-122">有时，需要在一个程序集内引用同一组件的两个不同版本。</span><span class="sxs-lookup"><span data-stu-id="78b11-122">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="78b11-123">为此，请在每个文件的 -reference 开关上使用别名子选项，以区分两个文件。</span><span class="sxs-lookup"><span data-stu-id="78b11-123">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="78b11-124">此别名将用作组件名的限定符，并解析为其中一个文件中的组件。</span><span class="sxs-lookup"><span data-stu-id="78b11-124">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="78b11-125">默认情况下使用 csc 响应 (.rsp) 文件，该文件引用常用的 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="78b11-125">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="78b11-126">如果希望编译器不要使用 csc.rsp，请使用 [-noconfig](./noconfig-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="78b11-126">Use [-noconfig](./noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78b11-127">在 Visual Studio 中，请使用“添加引用”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="78b11-127">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="78b11-128">有关详细信息，请参阅 [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。</span><span class="sxs-lookup"><span data-stu-id="78b11-128">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="78b11-129">若要确保通过使用 `-reference` 添加引用与通过使用“添加引用”\*\*\*\* 对话框添加引用之间的行为等效，请将要添加的程序集的“嵌入互操作类型”\*\*\*\* 属性设置为“False”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78b11-129">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="78b11-130">“True”\*\*\*\* 是该属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="78b11-130">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78b11-131">示例</span><span class="sxs-lookup"><span data-stu-id="78b11-131">Example</span></span>  
 <span data-ttu-id="78b11-132">本示例演示如何使用[外部别名](../keywords/extern-alias.md)功能。</span><span class="sxs-lookup"><span data-stu-id="78b11-132">This example shows how to use the [extern alias](../keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="78b11-133">编译源文件，并从先前已编译的 `grid.dll` 和 `grid20.dll` 中导入元数据。</span><span class="sxs-lookup"><span data-stu-id="78b11-133">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="78b11-134">这两个 DLL 包含同一组件的不同版本，将使用两个带有别名选项的 -reference 编译源文件。</span><span class="sxs-lookup"><span data-stu-id="78b11-134">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="78b11-135">这两个选项如下所示：</span><span class="sxs-lookup"><span data-stu-id="78b11-135">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="78b11-136">这将设置外部别名 `GridV1` 和 `GridV2`，将通过 `extern` 语句在程序中使用它们：</span><span class="sxs-lookup"><span data-stu-id="78b11-136">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="78b11-137">完成此操作后，可以通过在控件名称前添加 `GridV1` 前缀来引用 `grid.dll` 中的网格控件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="78b11-137">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="78b11-138">此外，可以通过在控件名称前添加 `GridV2` 前缀来引用 `grid20.dll` 中的网格控件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="78b11-138">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a><span data-ttu-id="78b11-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78b11-139">See also</span></span>

- [<span data-ttu-id="78b11-140">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="78b11-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="78b11-141">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="78b11-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
