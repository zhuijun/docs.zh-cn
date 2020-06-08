---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: b6a1c8fce17e3e5a54366c2ff4dff4e6aa668f56
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408655"
---
# <a name="-errorreport"></a><span data-ttu-id="73d67-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="73d67-102">-errorreport</span></span>

<span data-ttu-id="73d67-103">指定 Visual Basic 编译器应报告内部编译器错误的方式。</span><span class="sxs-lookup"><span data-stu-id="73d67-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="73d67-104">语法</span><span class="sxs-lookup"><span data-stu-id="73d67-104">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="73d67-105">备注</span><span class="sxs-lookup"><span data-stu-id="73d67-105">Remarks</span></span>

<span data-ttu-id="73d67-106">此选项为将 Visual Basic 内部编译器错误 (ICE) 报告给 Microsoft 的 Visual Basic 团队提供快捷方式。</span><span class="sxs-lookup"><span data-stu-id="73d67-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="73d67-107">默认情况下，编译器不向 Microsoft 发送任何信息。</span><span class="sxs-lookup"><span data-stu-id="73d67-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="73d67-108">不过，如果你遇到了内部编译器错误，则可以通过此选项将错误报告给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="73d67-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="73d67-109">该信息将帮助 Microsoft 工程师确认原因，并可能会帮助改进 Visual Basic 的下一个版本。</span><span class="sxs-lookup"><span data-stu-id="73d67-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="73d67-110">用户能否发送报告取决于计算机和用户策略权限。</span><span class="sxs-lookup"><span data-stu-id="73d67-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="73d67-111">下表概括了 `-errorreport` 选项的效果。</span><span class="sxs-lookup"><span data-stu-id="73d67-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="73d67-112">选项</span><span class="sxs-lookup"><span data-stu-id="73d67-112">Option</span></span>|<span data-ttu-id="73d67-113">行为</span><span class="sxs-lookup"><span data-stu-id="73d67-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="73d67-114">如果出现了内部编译器错误，会出现一个对话框，以便于你查看编译器收集到的准确数据。</span><span class="sxs-lookup"><span data-stu-id="73d67-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="73d67-115">你可以确定错误报告中是否有任何敏感信息，并决定是否将它发送给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="73d67-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="73d67-116">若你决定发送它，并且计算机和用户策略设置允许此操作，编译器会将数据发送给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="73d67-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="73d67-117">将错误报告排入队列。</span><span class="sxs-lookup"><span data-stu-id="73d67-117">Queues the error report.</span></span> <span data-ttu-id="73d67-118">使用管理员权限登录时，你可以报告自上次登录后出现的任何故障（每三天内提示你发送故障报告的次数不会超过一次）。</span><span class="sxs-lookup"><span data-stu-id="73d67-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="73d67-119">未指定 `-errorreport` 选项时，这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="73d67-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="73d67-120">若出现内部编译器错误，并且计算机和用户策略设置允许此操作，编译器会将数据发送给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="73d67-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="73d67-121">若 [Windows 错误报告](/windows/desktop/wer/windows-error-reporting)系统设置启用了报告，选项 `-errorreport:send` 会尝试自动将错误信息发送给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="73d67-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="73d67-122">若出现内部编译器错误，不会收集它，也不会将其发送给 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="73d67-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="73d67-123">出现错误时，编译器会发送数据，其中包括通常会包含部分源代码的堆栈。</span><span class="sxs-lookup"><span data-stu-id="73d67-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="73d67-124">若将 `-errorreport` 与 [-bugreport](bugreport.md) 选项配合使用，将发送完整的源文件。</span><span class="sxs-lookup"><span data-stu-id="73d67-124">If `-errorreport` is used with the [-bugreport](bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="73d67-125">此选项最适合与 [-bugreport](bugreport.md) 选项配合使用，因为这样 Microsoft 工程师即可以轻松地重现错误。</span><span class="sxs-lookup"><span data-stu-id="73d67-125">This option is best used with the [-bugreport](bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="73d67-126">`-errorreport` 选项在 Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="73d67-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="73d67-127">示例</span><span class="sxs-lookup"><span data-stu-id="73d67-127">Example</span></span>

<span data-ttu-id="73d67-128">下面的代码尝试编译 `T2.vb`，若编译器遇到内部编译器错误，它会提示你向 Microsoft 发送错误报告。</span><span class="sxs-lookup"><span data-stu-id="73d67-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="73d67-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="73d67-129">See also</span></span>

- [<span data-ttu-id="73d67-130">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="73d67-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="73d67-131">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="73d67-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="73d67-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="73d67-132">-bugreport</span></span>](bugreport.md)
