---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 4b468b8ee4301693312e9545396f2b9f495f75d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550906"
---
# <a name="-bugreport"></a><span data-ttu-id="a6556-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="a6556-102">-bugreport</span></span>

<span data-ttu-id="a6556-103">创建一个在提交 bug 报告时可以使用的文件。</span><span class="sxs-lookup"><span data-stu-id="a6556-103">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6556-104">语法</span><span class="sxs-lookup"><span data-stu-id="a6556-104">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="a6556-105">自变量</span><span class="sxs-lookup"><span data-stu-id="a6556-105">Arguments</span></span>

|<span data-ttu-id="a6556-106">术语</span><span class="sxs-lookup"><span data-stu-id="a6556-106">Term</span></span>|<span data-ttu-id="a6556-107">定义</span><span class="sxs-lookup"><span data-stu-id="a6556-107">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="a6556-108">必需。</span><span class="sxs-lookup"><span data-stu-id="a6556-108">Required.</span></span> <span data-ttu-id="a6556-109">将包含 bug 报告的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="a6556-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="a6556-110">如果文件名包含空格，则将它括在引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="a6556-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6556-111">备注</span><span class="sxs-lookup"><span data-stu-id="a6556-111">Remarks</span></span>

<span data-ttu-id="a6556-112">将以下信息添加到 `file`：</span><span class="sxs-lookup"><span data-stu-id="a6556-112">The following information is added to `file`:</span></span>

- <span data-ttu-id="a6556-113">编译期间所有源代码文件的副本。</span><span class="sxs-lookup"><span data-stu-id="a6556-113">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="a6556-114">编译中使用的编译器选项列表。</span><span class="sxs-lookup"><span data-stu-id="a6556-114">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="a6556-115">有关编译器、公共语言运行时和操作系统的版本信息。</span><span class="sxs-lookup"><span data-stu-id="a6556-115">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="a6556-116">编译器输出（如有）。</span><span class="sxs-lookup"><span data-stu-id="a6556-116">Compiler output, if any.</span></span>

- <span data-ttu-id="a6556-117">问题的说明（系统会提示你提供此信息）。</span><span class="sxs-lookup"><span data-stu-id="a6556-117">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="a6556-118">有关你认为应如何修复问题的说明（系统会提示你提供此信息）。</span><span class="sxs-lookup"><span data-stu-id="a6556-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="a6556-119">所有源代码文件的副本将添加到 `file` 中，因此你可能需要在尽可能短小的程序中重现（可疑）代码缺陷。</span><span class="sxs-lookup"><span data-stu-id="a6556-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6556-120">`-bugreport` 选项将生成一个包含潜在敏感信息的文件。</span><span class="sxs-lookup"><span data-stu-id="a6556-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="a6556-121">其中包括当前时间、编译器版本、.NET Framework 版本、OS 版本、用户名、运行编译器时所用的命令行参数、所有源代码和任何引用程序集的二进制文件形式。</span><span class="sxs-lookup"><span data-stu-id="a6556-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="a6556-122">通过在 Web.config 文件中为 ASP.NET 应用程序的服务器端编译指定命令行选项，可以访问此选项。</span><span class="sxs-lookup"><span data-stu-id="a6556-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="a6556-123">为了防止出现这种情况，请修改 Machine.config 文件，禁止用户在服务器上进行编译。</span><span class="sxs-lookup"><span data-stu-id="a6556-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="a6556-124">如果将此选项与 `-errorreport:prompt`、`-errorreport:queue` 或 `-errorreport:send` 一起使用，并且应用程序遇到内部编译器错误，则 `file` 中的信息将被发送到 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="a6556-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="a6556-125">该信息将帮助 Microsoft 工程师确认出现错误的原因，并可能会帮助改进 Visual Basic 的下一个版本。</span><span class="sxs-lookup"><span data-stu-id="a6556-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="a6556-126">默认情况下，不会向 Microsoft 发送任何信息。</span><span class="sxs-lookup"><span data-stu-id="a6556-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="a6556-127">但是，当你使用 `-errorreport:queue`（默认情况下已启用）编译应用程序时，应用程序将收集其错误报告。</span><span class="sxs-lookup"><span data-stu-id="a6556-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="a6556-128">然后，当计算机管理员登录时，错误报告系统会显示一个弹出窗口，使管理员能够将自登录后发生的任何错误报告转发给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a6556-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="a6556-129">`-bugreport` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="a6556-129">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a6556-130">示例</span><span class="sxs-lookup"><span data-stu-id="a6556-130">Example</span></span>

<span data-ttu-id="a6556-131">下面的示例将编译 T2.vb  ，并将所有 bug 报告信息放在“Problem.txt”文件  中。</span><span class="sxs-lookup"><span data-stu-id="a6556-131">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a6556-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="a6556-132">See also</span></span>

- [<span data-ttu-id="a6556-133">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="a6556-133">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a6556-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6556-134">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="a6556-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="a6556-135">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="a6556-136">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="a6556-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="a6556-137">[securityPolicy 的 trustLevel 元素（ASP.NET 设置架构）](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a6556-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
