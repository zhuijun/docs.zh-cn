---
title: F# 入门
description: 了解如何开始使用 F# 编程语言。
ms.date: 09/12/2020
ms.openlocfilehash: aeaa655e2af52a134dc70298375903c24d251079
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738783"
---
# <a name="get-started-with-f"></a><span data-ttu-id="ab0c6-103">F\# 入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-103">Get Started with F\#</span></span>

<span data-ttu-id="ab0c6-104">可以在计算机上或联机开始使用 F#。</span><span class="sxs-lookup"><span data-stu-id="ab0c6-104">You can get started with F# on your machine or online.</span></span>

## <a name="get-started-on-your-machine"></a><span data-ttu-id="ab0c6-105">计算机上的入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-105">Get started on your machine</span></span>

<span data-ttu-id="ab0c6-106">有很多关于在计算机上首次安装和使用 F# 的指南。</span><span class="sxs-lookup"><span data-stu-id="ab0c6-106">There are multiple guides on how to install and use F# for the first time on your machine.</span></span>  <span data-ttu-id="ab0c6-107">可以使用下表，它有助于做出决策：</span><span class="sxs-lookup"><span data-stu-id="ab0c6-107">You can use the following table to help in making a decision:</span></span>

| <span data-ttu-id="ab0c6-108">(OS)</span><span class="sxs-lookup"><span data-stu-id="ab0c6-108">OS</span></span> | <span data-ttu-id="ab0c6-109">首选 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ab0c6-109">Prefer Visual Studio</span></span> | <span data-ttu-id="ab0c6-110">首选 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ab0c6-110">Prefer Visual Studio Code</span></span> | <span data-ttu-id="ab0c6-111">首选命令行</span><span class="sxs-lookup"><span data-stu-id="ab0c6-111">Prefer command line</span></span> |
| -- |------------------------|--------------------------|-----------------------------|-------------------------|
| <span data-ttu-id="ab0c6-112">Windows</span><span class="sxs-lookup"><span data-stu-id="ab0c6-112">Windows</span></span> | [<span data-ttu-id="ab0c6-113">Visual Studio 入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-113">Get started with Visual Studio</span></span>](get-started-visual-studio.md) | [<span data-ttu-id="ab0c6-114">Visual Studio Code 入门</span><span class="sxs-lookup"><span data-stu-id="ab0c6-114">Get started with Visual Studio Code</span></span>](get-started-vscode.md) | [<span data-ttu-id="ab0c6-115">.NET Core CLI 入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-115">Get started with the .NET Core CLI</span></span>](get-started-command-line.md) |
| <span data-ttu-id="ab0c6-116">macOS</span><span class="sxs-lookup"><span data-stu-id="ab0c6-116">macOS</span></span> | [<span data-ttu-id="ab0c6-117">VS for Mac 入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-117">Get started with VS for Mac</span></span>](get-started-with-visual-studio-for-mac.md) | [<span data-ttu-id="ab0c6-118">Visual Studio Code 入门</span><span class="sxs-lookup"><span data-stu-id="ab0c6-118">Get started with Visual Studio Code</span></span>](get-started-vscode.md) | [<span data-ttu-id="ab0c6-119">.NET Core CLI 入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-119">Get started with the .NET Core CLI</span></span>](get-started-command-line.md) |
| <span data-ttu-id="ab0c6-120">Linux</span><span class="sxs-lookup"><span data-stu-id="ab0c6-120">Linux</span></span> | <span data-ttu-id="ab0c6-121">空值</span><span class="sxs-lookup"><span data-stu-id="ab0c6-121">N/A</span></span> | [<span data-ttu-id="ab0c6-122">Visual Studio Code 入门</span><span class="sxs-lookup"><span data-stu-id="ab0c6-122">Get started with Visual Studio Code</span></span>](get-started-vscode.md) | [<span data-ttu-id="ab0c6-123">.NET Core CLI 入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-123">Get started with the .NET Core CLI</span></span>](get-started-command-line.md) |

<span data-ttu-id="ab0c6-124">一般来说，没有哪一种比其他的更好。</span><span class="sxs-lookup"><span data-stu-id="ab0c6-124">In general, there is no specific that is better than the rest.</span></span> <span data-ttu-id="ab0c6-125">建议尝试所有在计算机上使用 F# 的方法，看看你最喜欢哪种方法！</span><span class="sxs-lookup"><span data-stu-id="ab0c6-125">We recommend trying all ways to use F# on your machine to see what you like the best!</span></span>

## <a name="get-started-online"></a><span data-ttu-id="ab0c6-126">联机入门指南</span><span class="sxs-lookup"><span data-stu-id="ab0c6-126">Get started online</span></span>

<span data-ttu-id="ab0c6-127">如果不想在计算机上安装 F# 和 .NET，也可以在浏览器中开始使用 F#：</span><span class="sxs-lookup"><span data-stu-id="ab0c6-127">If you'd rather not install F# and .NET on your machine, you can also get started with F# in the browser:</span></span>

* <span data-ttu-id="ab0c6-128">[绑定器上的 F# 简介](https://mybinder.org/v2/gh/dotnet/interactive/main?urlpath=lab)是通过免费的[绑定器](https://mybinder.org/)服务托管的 [Jupyter Notebook](https://jupyter.org/)。</span><span class="sxs-lookup"><span data-stu-id="ab0c6-128">[Introduction to F# on Binder](https://mybinder.org/v2/gh/dotnet/interactive/main?urlpath=lab) is a [Jupyter notebook](https://jupyter.org/) on hosted via the free [Binder](https://mybinder.org/) service.</span></span> <span data-ttu-id="ab0c6-129">不需要注册！</span><span class="sxs-lookup"><span data-stu-id="ab0c6-129">No sign-up needed!</span></span>
* <span data-ttu-id="ab0c6-130">[Fable REPL](https://fable.io/repl/) 是一种交互式的浏览器内 REPL，它使用 [Fable](https://fable.io/) 将 F# 代码转换为 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="ab0c6-130">[The Fable REPL](https://fable.io/repl/) is an interactive, in-browser REPL that uses [Fable](https://fable.io/) to translate F# code into JavaScript.</span></span> <span data-ttu-id="ab0c6-131">从 F# 基础知识到完全成熟的视频游戏，你都可以在浏览器中查看大量示例！</span><span class="sxs-lookup"><span data-stu-id="ab0c6-131">Check out the numerous samples that range from F# basics to a fully fledged video game all executing in your browser!</span></span>
