---
ms.openlocfilehash: 7c4b9faf25853c1c7a546f06c329f6f153eef904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606750"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="420a3-101">路径规范化中的更改</span><span class="sxs-lookup"><span data-stu-id="420a3-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="420a3-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="420a3-102">Details</span></span>

<span data-ttu-id="420a3-103">从面向 .NET Framework 4.6.2 的应用开始，运行时规范路径的方式发生了变化。路径规范化涉及修改用于标识路径或文件的字符串，使其与目标操作系统上的有效路径一致。</span><span class="sxs-lookup"><span data-stu-id="420a3-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="420a3-104">路径规范化通常涉及以下操作：</span><span class="sxs-lookup"><span data-stu-id="420a3-104">Normalization typically involves:</span></span>

- <span data-ttu-id="420a3-105">规范化处理组件和目录分隔符。</span><span class="sxs-lookup"><span data-stu-id="420a3-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="420a3-106">将当前目录应用到相对路径。</span><span class="sxs-lookup"><span data-stu-id="420a3-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="420a3-107">评估路径中的相对目录 (.) 或父目录 (..)。</span><span class="sxs-lookup"><span data-stu-id="420a3-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="420a3-108">删减指定字符。</span><span class="sxs-lookup"><span data-stu-id="420a3-108">Trimming specified characters.</span></span>
<span data-ttu-id="420a3-109">从面向 .NET Framework 4.6.2 的应用开始，在路径规范化中默认启用以下更改：</span><span class="sxs-lookup"><span data-stu-id="420a3-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="420a3-110">运行时在规范化处理路径时以操作系统的 [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) 函数为准。</span><span class="sxs-lookup"><span data-stu-id="420a3-110">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="420a3-111">路径规范化再也不用删减目录部分的末尾内容（如目录名称末尾的空格）。</span><span class="sxs-lookup"><span data-stu-id="420a3-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="420a3-112">支持完全信任形式的设备路径语法，包括 `\\.\` 和 `\\?\`（对于 mscorlib.dll 中的文件 I/O API）。</span><span class="sxs-lookup"><span data-stu-id="420a3-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="420a3-113">运行时不会验证设备语法路径。</span><span class="sxs-lookup"><span data-stu-id="420a3-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="420a3-114">支持使用设备语法来访问备用数据流。</span><span class="sxs-lookup"><span data-stu-id="420a3-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="420a3-115">这些更改会提升性能，同时允许方法访问之前无法访问的路径。</span><span class="sxs-lookup"><span data-stu-id="420a3-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="420a3-116">定目标到 .NET Framework 4.6.1 及更低版本、但在 .NET Framework 4.6.2 或更高版本控制下运行的应用不受此更改影响。</span><span class="sxs-lookup"><span data-stu-id="420a3-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="420a3-117">建议</span><span class="sxs-lookup"><span data-stu-id="420a3-117">Suggestion</span></span>

<span data-ttu-id="420a3-118">对于面向 .NET Framework 4.6.2 或更高版本的应用，可通过将以下内容添加到应用程序配置文件的 `<runtime>` 部分，选择弃用此更改而使用旧版规范化：</span><span class="sxs-lookup"><span data-stu-id="420a3-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="420a3-119">对于面向 .NET Framework 4.6.1 及更低版本，但在 .NET Framework 4.6.2 或更高版本上运行的应用，可通过将以下行添加到应用程序配置文件的 `<runtime>` 部分，启用对路径规范化的更改：</span><span class="sxs-lookup"><span data-stu-id="420a3-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="420a3-120">“属性”</span><span class="sxs-lookup"><span data-stu-id="420a3-120">Name</span></span>    | <span data-ttu-id="420a3-121">“值”</span><span class="sxs-lookup"><span data-stu-id="420a3-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="420a3-122">范围</span><span class="sxs-lookup"><span data-stu-id="420a3-122">Scope</span></span>   | <span data-ttu-id="420a3-123">次要</span><span class="sxs-lookup"><span data-stu-id="420a3-123">Minor</span></span>       |
| <span data-ttu-id="420a3-124">Version</span><span class="sxs-lookup"><span data-stu-id="420a3-124">Version</span></span> | <span data-ttu-id="420a3-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="420a3-125">4.6.2</span></span>       |
| <span data-ttu-id="420a3-126">类型</span><span class="sxs-lookup"><span data-stu-id="420a3-126">Type</span></span>    | <span data-ttu-id="420a3-127">重定目标</span><span class="sxs-lookup"><span data-stu-id="420a3-127">Retargeting</span></span> |
