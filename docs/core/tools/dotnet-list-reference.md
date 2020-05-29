---
title: dotnet list reference 命令
description: dotnet list reference 命令可便于列出项目间引用。
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802754"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="f1608-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="f1608-103">dotnet list reference</span></span>

<span data-ttu-id="f1608-104">**本文适用于：** ✔️ .NET Core 2.x SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="f1608-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1608-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="f1608-105">Name</span></span>

<span data-ttu-id="f1608-106">`dotnet list reference` - 列出项目到项目引用。</span><span class="sxs-lookup"><span data-stu-id="f1608-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1608-107">摘要</span><span class="sxs-lookup"><span data-stu-id="f1608-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="f1608-108">描述</span><span class="sxs-lookup"><span data-stu-id="f1608-108">Description</span></span>

<span data-ttu-id="f1608-109">使用 `dotnet list reference` 命令可方便地列出给定项目的项目引用。</span><span class="sxs-lookup"><span data-stu-id="f1608-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f1608-110">自变量</span><span class="sxs-lookup"><span data-stu-id="f1608-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="f1608-111">要操作的项目文件。</span><span class="sxs-lookup"><span data-stu-id="f1608-111">The project file to operate on.</span></span> <span data-ttu-id="f1608-112">如果未指定文件，此命令会搜索当前目录来获取文件。</span><span class="sxs-lookup"><span data-stu-id="f1608-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="f1608-113">选项</span><span class="sxs-lookup"><span data-stu-id="f1608-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="f1608-114">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="f1608-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f1608-115">示例</span><span class="sxs-lookup"><span data-stu-id="f1608-115">Examples</span></span>

* <span data-ttu-id="f1608-116">列出指定项目的项目引用：</span><span class="sxs-lookup"><span data-stu-id="f1608-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="f1608-117">列出当前目录中的项目的项目引用：</span><span class="sxs-lookup"><span data-stu-id="f1608-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
