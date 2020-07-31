---
title: 缓解：路径规范化
description: 了解 .NET Framework 中的路径规范化自面向 .NET Framework 4.6.2 的应用起有何变化。
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 89dcc46d9f266ffd3635dc0cc02b634720356eda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475211"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="ac942-103">缓解：路径规范化</span><span class="sxs-lookup"><span data-stu-id="ac942-103">Mitigation: Path Normalization</span></span>
<span data-ttu-id="ac942-104">自面向 .NET Framework 4.6.2 的应用起，.NET Framework 中的路径规范化已更改。</span><span class="sxs-lookup"><span data-stu-id="ac942-104">Starting with apps that target .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="ac942-105">什么是路径规范化？</span><span class="sxs-lookup"><span data-stu-id="ac942-105">What is path normalization?</span></span>  
 <span data-ttu-id="ac942-106">路径规范化涉及修改用于标识路径或文件的字符串，使其与目标操作系统上的有效路径一致。</span><span class="sxs-lookup"><span data-stu-id="ac942-106">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="ac942-107">路径规范化通常涉及以下操作：</span><span class="sxs-lookup"><span data-stu-id="ac942-107">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="ac942-108">规范化处理组件和目录分隔符。</span><span class="sxs-lookup"><span data-stu-id="ac942-108">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="ac942-109">将当前目录应用到相对路径。</span><span class="sxs-lookup"><span data-stu-id="ac942-109">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="ac942-110">评估路径中的相对目录 (`.`) 或父目录 (`..`)。</span><span class="sxs-lookup"><span data-stu-id="ac942-110">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="ac942-111">删减指定字符。</span><span class="sxs-lookup"><span data-stu-id="ac942-111">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="ac942-112">更改</span><span class="sxs-lookup"><span data-stu-id="ac942-112">The changes</span></span>  
 <span data-ttu-id="ac942-113">自面向 .NET Framework 4.6.2 的应用起，路径规范化在以下几个方面进行了更改：</span><span class="sxs-lookup"><span data-stu-id="ac942-113">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="ac942-114">运行时在规范化处理路径时以操作系统的 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 函数为准。</span><span class="sxs-lookup"><span data-stu-id="ac942-114">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="ac942-115">路径规范化再也不用删减目录部分的末尾内容（如目录名称末尾的空格）。</span><span class="sxs-lookup"><span data-stu-id="ac942-115">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="ac942-116">支持完全信任形式的设备路径语法，包括 `\\.\` 和 `\\?\`（对于 mscorlib.dll 中的文件 I/O API）。</span><span class="sxs-lookup"><span data-stu-id="ac942-116">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="ac942-117">运行时不会验证设备语法路径。</span><span class="sxs-lookup"><span data-stu-id="ac942-117">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="ac942-118">支持使用设备语法来访问备用数据流。</span><span class="sxs-lookup"><span data-stu-id="ac942-118">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ac942-119">影响</span><span class="sxs-lookup"><span data-stu-id="ac942-119">Impact</span></span>  

<span data-ttu-id="ac942-120">对于面向 .NET Framework 4.6.2 或更高版本的应用，这些更改默认启用。</span><span class="sxs-lookup"><span data-stu-id="ac942-120">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="ac942-121">这些更改应该会提升性能，同时允许方法访问之前无法访问的路径。</span><span class="sxs-lookup"><span data-stu-id="ac942-121">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="ac942-122">定目标到 .NET Framework 4.6.1 及更低版本、但在 .NET Framework 4.6.2 或更高版本控制下运行的应用不受此更改影响。</span><span class="sxs-lookup"><span data-stu-id="ac942-122">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ac942-123">缓解</span><span class="sxs-lookup"><span data-stu-id="ac942-123">Mitigation</span></span>  
 <span data-ttu-id="ac942-124">对于面向 .NET Framework 4.6.2 或更高版本的应用，可通过将以下内容添加到应用程序配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分，选择弃用此更改而使用旧版规范化：</span><span class="sxs-lookup"><span data-stu-id="ac942-124">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="ac942-125">对于面向 .NET Framework 4.6.1 及更低版本，但在 .NET Framework 4.6.2 或更高版本上运行的应用，可通过将以下行添加到应用程序配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分，启用对路径规范化的更改：</span><span class="sxs-lookup"><span data-stu-id="ac942-125">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac942-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac942-126">See also</span></span>

- [<span data-ttu-id="ac942-127">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="ac942-127">Application compatibility</span></span>](application-compatibility.md)
