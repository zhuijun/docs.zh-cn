---
title: 缓解：产品版本控制
description: 在本文中，了解 .NET Framework 4.6 和更高版本产品版本控制与早期版本相比有何变化。
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475393"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="8361c-103">缓解：产品版本控制</span><span class="sxs-lookup"><span data-stu-id="8361c-103">Mitigation: Product Versioning</span></span>

<span data-ttu-id="8361c-104">在 .NET Framework 4.6 和更高版本中，产品版本控制已更改，不再是早期版本的 .NET Framework（.NET Framework 4、4.5、4.5.1 和 4.5.2）。</span><span class="sxs-lookup"><span data-stu-id="8361c-104">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="8361c-105">产品版本控制更改</span><span class="sxs-lookup"><span data-stu-id="8361c-105">Product versioning changes</span></span>

<span data-ttu-id="8361c-106">以下是详细更改：</span><span class="sxs-lookup"><span data-stu-id="8361c-106">The following are the detailed changes:</span></span>

- <span data-ttu-id="8361c-107">`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 键的 `Version` 项的值在 .NET Framework 4.6 及其点版本中已更改为 `4.6.`*xxxxx*，在 .NET Framework 4.7 中已更改为 `4.7.`*xxxxx*。</span><span class="sxs-lookup"><span data-stu-id="8361c-107">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="8361c-108">在 .NET Framework 4.5、4.5.1 和 4.5.2 中，它的格式为 `4.5.`*xxxxx*。</span><span class="sxs-lookup"><span data-stu-id="8361c-108">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="8361c-109">.NET Framework 文件的文件和产品版本控制在 .NET Framework 4.6 及其点版本中已从 `4.0.30319.x` 的早期版本控制方案更改为 `4.6.X.0`，在 .NET Framework 4.7 及其点版本中已更改为 `4.7.X.0`。</span><span class="sxs-lookup"><span data-stu-id="8361c-109">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="8361c-110">右键单击某个文件后，查看文件的“属性”时可以看到这些新值。</span><span class="sxs-lookup"><span data-stu-id="8361c-110">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="8361c-111">对于 .NET Framework 4.6 及其点版本，托管程序集的 <xref:System.Reflection.AssemblyFileVersionAttribute> 和 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 特性具有格式为 `4.6.X.0` 的 <xref:System.Version> 值，对于 .NET Framework 4.7，则为格式 `4.7.X.0`。</span><span class="sxs-lookup"><span data-stu-id="8361c-111">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="8361c-112">从 .NET Framework 4.6 开始，<xref:System.Environment.Version%2A?displayProperty=nameWithType> 属性将返回修正后的版本字符串 `4.0.30319.42000`。</span><span class="sxs-lookup"><span data-stu-id="8361c-112">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="8361c-113">在 .NET Framework 4、4.5、4.5.1 和 4.5.2 中，它返回格式为 `4.0.30319.xxxxx`（其中 `xxxxx` 小于 42000）的版本字符串，例如“4.0.30319.18010”。</span><span class="sxs-lookup"><span data-stu-id="8361c-113">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="8361c-114">请注意，我们不建议应用程序代码对 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 属性产生任何新的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="8361c-114">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="8361c-115">处理产品版本控制更改</span><span class="sxs-lookup"><span data-stu-id="8361c-115">Handling the product versioning changes</span></span>

<span data-ttu-id="8361c-116">一般情况下，应用程序应依赖于用于检测诸如 .NET Framework 的运行时版本和安装目录等内容的推荐技术：</span><span class="sxs-lookup"><span data-stu-id="8361c-116">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="8361c-117">要检测 .NET Framework 的运行时版本，请参阅[如何：确定已安装的 .NET Framework 版本](how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="8361c-117">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="8361c-118">若要确定 .NET Framework 的安装路径，请使用 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 密钥中的 `InstallPath` 条目的值。</span><span class="sxs-lookup"><span data-stu-id="8361c-118">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="8361c-119">子项名称是 `NET Framework Setup`，而不是 `.NET Framework Setup`。</span><span class="sxs-lookup"><span data-stu-id="8361c-119">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="8361c-120">若要确定.NET Framework 公共语言运行时的目录路径，请调用 <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8361c-120">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="8361c-121">若要获取 CLR 版本，请调用 <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="8361c-121">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="8361c-122">对于 .NET Framework 4 及其子版本（.NET Framework 4.5、4.5.1、4.5.2 以及 .NET Framework 4.6、4.6.1、4.6.2 和 4.7），它将返回字符串 `v4.0.30319`。</span><span class="sxs-lookup"><span data-stu-id="8361c-122">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8361c-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="8361c-123">See also</span></span>

- [<span data-ttu-id="8361c-124">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="8361c-124">Application compatibility</span></span>](application-compatibility.md)
