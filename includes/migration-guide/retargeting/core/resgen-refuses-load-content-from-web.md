---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614367"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="a58f7-101">Resgen 拒绝从 Web 加载内容</span><span class="sxs-lookup"><span data-stu-id="a58f7-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="a58f7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a58f7-102">Details</span></span>

<span data-ttu-id="a58f7-103">.resx 文件可能包含二进制格式的输入。</span><span class="sxs-lookup"><span data-stu-id="a58f7-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="a58f7-104">如果尝试使用 resgen 来加载从不受信任的位置下载的文件，则默认情况下将无法加载该输入。</span><span class="sxs-lookup"><span data-stu-id="a58f7-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a58f7-105">建议</span><span class="sxs-lookup"><span data-stu-id="a58f7-105">Suggestion</span></span>

<span data-ttu-id="a58f7-106">需要从不受信任的位置加载二进制格式输入的 resgen 用户可以从输入文件中删除 Web 标记，也可以应用选择退出。添加以下注册表设置，以应用计算机范围的选择退出：[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span><span class="sxs-lookup"><span data-stu-id="a58f7-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="a58f7-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="a58f7-107">Name</span></span>    | <span data-ttu-id="a58f7-108">“值”</span><span class="sxs-lookup"><span data-stu-id="a58f7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a58f7-109">范围</span><span class="sxs-lookup"><span data-stu-id="a58f7-109">Scope</span></span>   | <span data-ttu-id="a58f7-110">边缘</span><span class="sxs-lookup"><span data-stu-id="a58f7-110">Edge</span></span>        |
| <span data-ttu-id="a58f7-111">Version</span><span class="sxs-lookup"><span data-stu-id="a58f7-111">Version</span></span> | <span data-ttu-id="a58f7-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="a58f7-112">4.7.2</span></span>       |
| <span data-ttu-id="a58f7-113">类型</span><span class="sxs-lookup"><span data-stu-id="a58f7-113">Type</span></span>    | <span data-ttu-id="a58f7-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="a58f7-114">Retargeting</span></span> |
