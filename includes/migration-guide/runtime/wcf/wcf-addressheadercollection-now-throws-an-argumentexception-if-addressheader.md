---
ms.openlocfilehash: 3506653bfc749ae3d8002715ca72ca89de7a681b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "91025210"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="ec69b-101">如果 addressHeader 元素为 null，则 WCF AddressHeaderCollection 现在引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="ec69b-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="ec69b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ec69b-102">Details</span></span>

<span data-ttu-id="ec69b-103">自 .NET Framework 4.7.1 起，如果有一个元素为 `null`，<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> 构造函数就会引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="ec69b-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="ec69b-104">在 .NET Framework 4.7 和更低版本中，不引发异常。</span><span class="sxs-lookup"><span data-stu-id="ec69b-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ec69b-105">建议</span><span class="sxs-lookup"><span data-stu-id="ec69b-105">Suggestion</span></span>

<span data-ttu-id="ec69b-106">如果在包含此更改的 .NET Framework 4.7.1 或更高版本中遇到兼容性问题，可以通过在 app.config 文件的 `<runtime>` 部分添加下面的代码行选择退出它：</span><span class="sxs-lookup"><span data-stu-id="ec69b-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="ec69b-107">名称</span><span class="sxs-lookup"><span data-stu-id="ec69b-107">Name</span></span>    | <span data-ttu-id="ec69b-108">值</span><span class="sxs-lookup"><span data-stu-id="ec69b-108">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="ec69b-109">范围</span><span class="sxs-lookup"><span data-stu-id="ec69b-109">Scope</span></span>   | <span data-ttu-id="ec69b-110">次要</span><span class="sxs-lookup"><span data-stu-id="ec69b-110">Minor</span></span>   |
| <span data-ttu-id="ec69b-111">Version</span><span class="sxs-lookup"><span data-stu-id="ec69b-111">Version</span></span> | <span data-ttu-id="ec69b-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="ec69b-112">4.7.1</span></span>   |
| <span data-ttu-id="ec69b-113">类型</span><span class="sxs-lookup"><span data-stu-id="ec69b-113">Type</span></span>    | <span data-ttu-id="ec69b-114">运行时</span><span class="sxs-lookup"><span data-stu-id="ec69b-114">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ec69b-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ec69b-115">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
