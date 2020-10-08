---
title: 'Wfc.exe (工作流命令行编译器工具) '
description: 了解 wfc.exe （工作流命令行编译器工具）。
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: cf89962014584adf098118044b063b38b29160b7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844610"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a><span data-ttu-id="63dd6-103">wfc.exe (工作流命令行编译器工具) </span><span class="sxs-lookup"><span data-stu-id="63dd6-103">wfc.exe (Workflow Command-line Compiler Tool)</span></span>
> [!NOTE]
> <span data-ttu-id="63dd6-104">本材料讨论的类型和命名空间已废弃不用。</span><span class="sxs-lookup"><span data-stu-id="63dd6-104">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="63dd6-105">wfc.exe 工作流命令行编译器工具适用于文件扩展名为 *xoml* () 过时的旧工作流标记文件。</span><span class="sxs-lookup"><span data-stu-id="63dd6-105">The wfc.exe workflow command-line compiler tool works with old workflow markup files that have the file extension *.xoml* (obsoleted).</span></span>

## <a name="compilation-process"></a><span data-ttu-id="63dd6-106">编译过程</span><span class="sxs-lookup"><span data-stu-id="63dd6-106">Compilation process</span></span>

<span data-ttu-id="63dd6-107">编译工作流时，会在编译过程中执行下列过程：</span><span class="sxs-lookup"><span data-stu-id="63dd6-107">When workflows are compiled, the following procedures are performed as part of the compilation process:</span></span>

- <span data-ttu-id="63dd6-108">执行验证可以确保根据工作流活动为自己设置的规则验证这些活动。</span><span class="sxs-lookup"><span data-stu-id="63dd6-108">Validation is performed to ensure that the workflow activities validate based on the rules that the activities have set for themselves.</span></span> <span data-ttu-id="63dd6-109">如果存在验证错误，则编译器会返回错误列表。</span><span class="sxs-lookup"><span data-stu-id="63dd6-109">If there are validation errors, the compiler returns a list of the errors.</span></span>  
- <span data-ttu-id="63dd6-110">根据在编译器中输入的标记定义来生成一个分部类。</span><span class="sxs-lookup"><span data-stu-id="63dd6-110">A partial class is generated from the markup definition that is input into the compiler.</span></span>  

- <span data-ttu-id="63dd6-111">执行代码可以帮助在运行时执行活动。</span><span class="sxs-lookup"><span data-stu-id="63dd6-111">Code is generated to help with the run-time execution of the activities.</span></span> <span data-ttu-id="63dd6-112">生成事件订阅，事件订阅可帮助活动了解它们所包含的活动何时执行完毕。</span><span class="sxs-lookup"><span data-stu-id="63dd6-112">Event subscriptions are generated, which help activities know when the activities they contain are finished executing.</span></span>  
- <span data-ttu-id="63dd6-113">在 .NET Framework C# 或 Visual Basic 编译器中输入根据标记文件生成的分部类以及根据代码文件生成的分部类。</span><span class="sxs-lookup"><span data-stu-id="63dd6-113">The partial classes generated from the markup file and the partial classes from the code file are entered into the .NET Framework C# or Visual Basic compiler.</span></span> <span data-ttu-id="63dd6-114">此过程的输出为 .NET 程序集：WorkflowSample.dll。</span><span class="sxs-lookup"><span data-stu-id="63dd6-114">The output of this process is the .NET assembly, WorkflowSample.dll.</span></span> <span data-ttu-id="63dd6-115">可以部署该程序集以运行工作流。</span><span class="sxs-lookup"><span data-stu-id="63dd6-115">This can be deployed to run the workflow.</span></span>

### <a name="compiler-options"></a><span data-ttu-id="63dd6-116">编译器选项</span><span class="sxs-lookup"><span data-stu-id="63dd6-116">Compiler options</span></span>

<span data-ttu-id="63dd6-117">本部分介绍 wfc.exe 工作流命令行编译器的选项。</span><span class="sxs-lookup"><span data-stu-id="63dd6-117">This section shows the options for the wfc.exe workflow command-line compiler.</span></span>

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a><span data-ttu-id="63dd6-118">注解</span><span class="sxs-lookup"><span data-stu-id="63dd6-118">Remarks</span></span>
> [!NOTE]
> <span data-ttu-id="63dd6-119">本材料讨论的类型和命名空间已废弃不用。</span><span class="sxs-lookup"><span data-stu-id="63dd6-119">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="63dd6-120">授权类型的列表通常在 *wfc.exe.config* 文件中定义。</span><span class="sxs-lookup"><span data-stu-id="63dd6-120">A list of authorized types is usually defined in the *wfc.exe.config* file.</span></span> <span data-ttu-id="63dd6-121">在工作流编译的验证阶段，如果工作流源文档或伴随规则文件直接引用授权类型列表中不存在的任何 .NET Framework 类型，则该工作流源文档将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="63dd6-121">During the validation phase of workflow compilation, a workflow source document is rejected if it or the companion rules file directly references any .NET Framework types not present in a list of authorized types.</span></span> <span data-ttu-id="63dd6-122">授权类型列表是一个 XML 文档，其中每个条目表示一个 `Assembly` 、、 `Namespace` 一个 `TypeName` 和一个授权的 { `True`&#124;`False` } 指示器。</span><span class="sxs-lookup"><span data-stu-id="63dd6-122">The list of authorized types is an XML document where each entry indicates an `Assembly`, a `Namespace`, a `TypeName`, and an Authorized {`True`&#124;`False`} indicator.</span></span> <span data-ttu-id="63dd6-123">`AuthorizedType` 对应于列表中的条目。</span><span class="sxs-lookup"><span data-stu-id="63dd6-123">`AuthorizedType` corresponds to an entry in the list.</span></span> <span data-ttu-id="63dd6-124">允许使用通配符符号（可用于包含或排除完整的命名空间）。</span><span class="sxs-lookup"><span data-stu-id="63dd6-124">Wildcard character designations, which can be used to include or exclude complete namespaces, are allowed.</span></span> <span data-ttu-id="63dd6-125">例如， `Type="System.*"` 包括中的所有类型 <xref:System> ，包括子命名空间中包含的类型。</span><span class="sxs-lookup"><span data-stu-id="63dd6-125">For example, `Type="System.*"` includes all types in <xref:System>, including types contained in child namespaces.</span></span>
  
<span data-ttu-id="63dd6-126">使用授权类型列表的方式由 <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> 选项控制 `'/checktypes'` 。</span><span class="sxs-lookup"><span data-stu-id="63dd6-126">The use of a list of authorized types is controlled by the <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'`.</span></span>

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> <span data-ttu-id="63dd6-127">当 `Type="System.*"` 类型存在时，可以包括其他不需要的类型（如 `Type="System.Configuration"` ）进行编译。</span><span class="sxs-lookup"><span data-stu-id="63dd6-127">When `Type="System.*"` type is present, it's possible to include other unintended types, such as `Type="System.Configuration"`, for compilation.</span></span> <span data-ttu-id="63dd6-128">你应谨慎，并查看每个。</span><span class="sxs-lookup"><span data-stu-id="63dd6-128">You should be cautious and review each one.</span></span> <span data-ttu-id="63dd6-129">对于应限制的任何类型，请确保将设置 `Authorized` 为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="63dd6-129">For any type that should be restricted, be sure to set `Authorized` to `False`.</span></span>

## <a name="see-also"></a><span data-ttu-id="63dd6-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="63dd6-130">See also</span></span>

- [<span data-ttu-id="63dd6-131">AuthorizedType 类</span><span class="sxs-lookup"><span data-stu-id="63dd6-131">AuthorizedType class</span></span>](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
