---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614417"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="d5596-101">WPF 在主/从方案中显示 ADO 数据时更改主键</span><span class="sxs-lookup"><span data-stu-id="d5596-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="d5596-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d5596-102">Details</span></span>

<span data-ttu-id="d5596-103">假设你有 `Order` 类型的 ADO 项集合，其关系名为 &quot;OrderDetails&quot;，通过主键 &quot;OrderID&quot; 将其关联到 `Detail` 类型的项集合。</span><span class="sxs-lookup"><span data-stu-id="d5596-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="d5596-104">在 WPF 应用程序中，你可以将列表控件绑定到给定顺序的详细信息：</span><span class="sxs-lookup"><span data-stu-id="d5596-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="d5596-105">其中 DataContext 是一个 `Order`。</span><span class="sxs-lookup"><span data-stu-id="d5596-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="d5596-106">WPF 会获取 `OrderDetails` 属性的值 - 其 `OrderID` 与主项的 `OrderID` 匹配的所有 `Detail` 项的集合 D。</span><span class="sxs-lookup"><span data-stu-id="d5596-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="d5596-107">更改主项的主密钥 `OrderID` 时，会出现行为更改。</span><span class="sxs-lookup"><span data-stu-id="d5596-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="d5596-108">ADO 自动更改详细信息集合中每个受影响记录的 `OrderID`（即复制到集合 D 的信息）。</span><span class="sxs-lookup"><span data-stu-id="d5596-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="d5596-109">但 D 会发生什么？</span><span class="sxs-lookup"><span data-stu-id="d5596-109">But what happens to D?</span></span>

- <span data-ttu-id="d5596-110">旧行为：清除集合 D。</span><span class="sxs-lookup"><span data-stu-id="d5596-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="d5596-111">主项*不会*发出属性 `OrderDetails` 的更改通知。</span><span class="sxs-lookup"><span data-stu-id="d5596-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="d5596-112">列表框将继续使用集合 D，现为空。</span><span class="sxs-lookup"><span data-stu-id="d5596-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="d5596-113">新行为：集合 D 保持不变。</span><span class="sxs-lookup"><span data-stu-id="d5596-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="d5596-114">其中每一项都将发出 `OrderID` 属性的更改通知。</span><span class="sxs-lookup"><span data-stu-id="d5596-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="d5596-115">列表框将持续使用集合 D，并显示新 `OrderID` 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d5596-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="d5596-116">WPF 通过不同的方式创建集合 D 来实现新行为：通过调用 ADO 方法 <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType>，并将 `followParent` 参数设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d5596-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d5596-117">建议</span><span class="sxs-lookup"><span data-stu-id="d5596-117">Suggestion</span></span>

<span data-ttu-id="d5596-118">应用通过使用以下 AppContext 开关获取新行为。</span><span class="sxs-lookup"><span data-stu-id="d5596-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="d5596-119">对于面向 .NET 4.7.1 或更低版本的应用，开关默认为 `true`（旧行为），而对于面向 .NET 4.7.2 或更高版本的应用，开关默认为 `false`（新行为）。</span><span class="sxs-lookup"><span data-stu-id="d5596-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="d5596-120">“属性”</span><span class="sxs-lookup"><span data-stu-id="d5596-120">Name</span></span>    | <span data-ttu-id="d5596-121">“值”</span><span class="sxs-lookup"><span data-stu-id="d5596-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d5596-122">范围</span><span class="sxs-lookup"><span data-stu-id="d5596-122">Scope</span></span>   | <span data-ttu-id="d5596-123">次要</span><span class="sxs-lookup"><span data-stu-id="d5596-123">Minor</span></span>       |
| <span data-ttu-id="d5596-124">版本</span><span class="sxs-lookup"><span data-stu-id="d5596-124">Version</span></span> | <span data-ttu-id="d5596-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="d5596-125">4.7.2</span></span>       |
| <span data-ttu-id="d5596-126">类型</span><span class="sxs-lookup"><span data-stu-id="d5596-126">Type</span></span>    | <span data-ttu-id="d5596-127">重定目标</span><span class="sxs-lookup"><span data-stu-id="d5596-127">Retargeting</span></span> |
