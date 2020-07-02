---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614382"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a><span data-ttu-id="b6b2b-101">MemberDescriptor.Equals 实现不正确</span><span class="sxs-lookup"><span data-stu-id="b6b2b-101">Incorrect implementation of MemberDescriptor.Equals</span></span>

#### <a name="details"></a><span data-ttu-id="b6b2b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b6b2b-102">Details</span></span>

<span data-ttu-id="b6b2b-103"><xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 方法的原始实现从比较类别名称和描述字符串这两个对象来比较两个不同字符串属性。</span><span class="sxs-lookup"><span data-stu-id="b6b2b-103">The original implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method compares two different string properties from the objects being compared: the category name and the description string.</span></span> <span data-ttu-id="b6b2b-104">解决方法是比较第一个对象的 <xref:System.ComponentModel.MemberDescriptor.Category> 和第二个对象的 <xref:System.ComponentModel.MemberDescriptor.Category>，并比较第一个对象的 <xref:System.ComponentModel.MemberDescriptor.Description> 和第二个对象的 <xref:System.ComponentModel.MemberDescriptor.Description>。</span><span class="sxs-lookup"><span data-stu-id="b6b2b-104">The fix is to compare the <xref:System.ComponentModel.MemberDescriptor.Category> of the first object to the <xref:System.ComponentModel.MemberDescriptor.Category> of the second one, and the <xref:System.ComponentModel.MemberDescriptor.Description> of the first to the <xref:System.ComponentModel.MemberDescriptor.Description> of the second.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b6b2b-105">建议</span><span class="sxs-lookup"><span data-stu-id="b6b2b-105">Suggestion</span></span>

<span data-ttu-id="b6b2b-106">描述符相等时如果应用程序依赖于有时返回 `false` 的 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 并且你面向 .NET Framework 4.6.2 和更高版本，那么可以采用以下几个选项：</span><span class="sxs-lookup"><span data-stu-id="b6b2b-106">If your application depends on <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> sometimes returning `false` when descriptors are equivalent, and you are targeting the .NET Framework 4.6.2 or later, you have several options:</span></span>

- <span data-ttu-id="b6b2b-107">除了调用 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 方法，还需更改代码来手动比较 <xref:System.ComponentModel.MemberDescriptor.Category> 和 <xref:System.ComponentModel.MemberDescriptor.Description> 字段。</span><span class="sxs-lookup"><span data-stu-id="b6b2b-107">Make code changes to compare the <xref:System.ComponentModel.MemberDescriptor.Category> and <xref:System.ComponentModel.MemberDescriptor.Description> fields manually in addition to calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="b6b2b-108">将以下值添加到 app.config 文件从而选择弃用此更改：</span><span class="sxs-lookup"><span data-stu-id="b6b2b-108">Opt out of this change by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

<span data-ttu-id="b6b2b-109">如果应用程序面向 .NET Framework 4.6.1 或更低版本，并且在 .NET Framework 4.6.2 及更高版本上运行且你想要启用此更改，可以通过将以下值添加到 app.config 文件以将兼容性开关设为 `false`：</span><span class="sxs-lookup"><span data-stu-id="b6b2b-109">If your application targets .NET Framework 4.6.1 or earlier and is running on the .NET Framework 4.6.2 or later and you want this change enabled, you can set the compatibility switch to `false` by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| <span data-ttu-id="b6b2b-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="b6b2b-110">Name</span></span>    | <span data-ttu-id="b6b2b-111">值</span><span class="sxs-lookup"><span data-stu-id="b6b2b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b6b2b-112">范围</span><span class="sxs-lookup"><span data-stu-id="b6b2b-112">Scope</span></span>   | <span data-ttu-id="b6b2b-113">边缘</span><span class="sxs-lookup"><span data-stu-id="b6b2b-113">Edge</span></span>        |
| <span data-ttu-id="b6b2b-114">Version</span><span class="sxs-lookup"><span data-stu-id="b6b2b-114">Version</span></span> | <span data-ttu-id="b6b2b-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="b6b2b-115">4.6.2</span></span>       |
| <span data-ttu-id="b6b2b-116">类型</span><span class="sxs-lookup"><span data-stu-id="b6b2b-116">Type</span></span>    | <span data-ttu-id="b6b2b-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="b6b2b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b6b2b-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b6b2b-118">Affected APIs</span></span>

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
