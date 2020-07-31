---
title: CorFlags.exe（CorFlags 转换工具）
description: 了解 CorFlags.exe（CorFlags 转换工具）。 此工具可用于配置可移植可执行映像的标头的 CorFlags 部分。
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: da5efadd63cc03f6f6e4eecf3115865ca3643b39
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167222"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="7f320-104">CorFlags.exe（CorFlags 转换工具）</span><span class="sxs-lookup"><span data-stu-id="7f320-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="7f320-105">利用 CorFlags 转换工具，你配置可移植可执行映像标头的 CorFlags 部分。</span><span class="sxs-lookup"><span data-stu-id="7f320-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="7f320-106">此工具会自动随 Visual Studio 一起安装。</span><span class="sxs-lookup"><span data-stu-id="7f320-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="7f320-107">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="7f320-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="7f320-108">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7f320-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="7f320-109">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="7f320-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f320-110">语法</span><span class="sxs-lookup"><span data-stu-id="7f320-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f320-111">参数</span><span class="sxs-lookup"><span data-stu-id="7f320-111">Parameters</span></span>  
  
|<span data-ttu-id="7f320-112">必选参数</span><span class="sxs-lookup"><span data-stu-id="7f320-112">Required parameter</span></span>|<span data-ttu-id="7f320-113">描述</span><span class="sxs-lookup"><span data-stu-id="7f320-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="7f320-114">要为其配置 CorFlags 的程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="7f320-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="7f320-115">选项</span><span class="sxs-lookup"><span data-stu-id="7f320-115">Option</span></span>|<span data-ttu-id="7f320-116">说明</span><span class="sxs-lookup"><span data-stu-id="7f320-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="7f320-117">设置 32BITREQUIRED 标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="7f320-118">清除 32BITREQUIRED 标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="7f320-119">设置 32BITPREFERRED 标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="7f320-120">该应用程序甚至可以作为 32 位进程在 64 位平台上运行。</span><span class="sxs-lookup"><span data-stu-id="7f320-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="7f320-121">仅在 EXE 文件中设置此标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="7f320-122">如果在 DLL 上设置此标志，则 DLL 将无法在 64 位进程中加载，并引发 <xref:System.BadImageFormatException> 异常。</span><span class="sxs-lookup"><span data-stu-id="7f320-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="7f320-123">具有此标志的 EXE 文件可以加载到 64 位进程中。</span><span class="sxs-lookup"><span data-stu-id="7f320-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="7f320-124">.NET Framework 4.5 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="7f320-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="7f320-125">清除 32BITPREFERRED 标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="7f320-126">.NET Framework 4.5 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="7f320-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="7f320-127">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="7f320-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="7f320-128">强制执行更新，即使程序集具有强名称也是如此。</span><span class="sxs-lookup"><span data-stu-id="7f320-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="7f320-129">**重要提示：** 如果更新具有强名称的程序集，则必须在执行其代码之前再次对其签名。</span><span class="sxs-lookup"><span data-stu-id="7f320-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="7f320-130">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="7f320-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="7f320-131">设置 ILONLY 标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="7f320-132">清除 ILONLY 标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="7f320-133">取消显示 Microsoft 启动版权标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="7f320-134">将 CLR 标头版本还原到 2.0。</span><span class="sxs-lookup"><span data-stu-id="7f320-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="7f320-135">将 CLR 标头版本升级到 2.5。</span><span class="sxs-lookup"><span data-stu-id="7f320-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="7f320-136">**注意：** 程序集必须具有 2.5 版或更高版本的 CLR 标头才能在本机运行。</span><span class="sxs-lookup"><span data-stu-id="7f320-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f320-137">备注</span><span class="sxs-lookup"><span data-stu-id="7f320-137">Remarks</span></span>  
 <span data-ttu-id="7f320-138">如果未指定任何选项，则 CorFlags 转换工具将显示指定程序集的标志。</span><span class="sxs-lookup"><span data-stu-id="7f320-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f320-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f320-139">See also</span></span>

- [<span data-ttu-id="7f320-140">工具</span><span class="sxs-lookup"><span data-stu-id="7f320-140">Tools</span></span>](index.md)
- [<span data-ttu-id="7f320-141">64 位应用程序</span><span class="sxs-lookup"><span data-stu-id="7f320-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="7f320-142">命令提示</span><span class="sxs-lookup"><span data-stu-id="7f320-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
