---
title: 示例：动态编程疑难解答
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128442"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="5e3f1-102">示例：动态编程疑难解答</span><span class="sxs-lookup"><span data-stu-id="5e3f1-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
> <span data-ttu-id="5e3f1-103">该主题是指 .NET Native 开发者预览版这款预发布软件。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="5e3f1-104">可从 [Microsoft Connect 网站](https://go.microsoft.com/fwlink/?LinkId=394611)（需要注册）下载该预览版。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="5e3f1-105">并非所有使用 .NET Native 工具链开发的应用中的元数据查找失败都会导致异常。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-105">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="5e3f1-106">有些可能会在一个应用中以不可预知的方式显示。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="5e3f1-107">以下实例展示了由引用一个空对象造成的访问冲突：</span><span class="sxs-lookup"><span data-stu-id="5e3f1-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```output
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 <span data-ttu-id="5e3f1-108">我们可尝试通过使用[入门](getting-started-with-net-native.md)的“手动解析丢失的元数据”一节中列出的三步方法来解决这个异常。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="5e3f1-109">应用过去在执行什么操作？</span><span class="sxs-lookup"><span data-stu-id="5e3f1-109">What was the app doing?</span></span>  
 <span data-ttu-id="5e3f1-110">第一件要提起注意的是堆栈基部的 `async` 关键字机械设备。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="5e3f1-111">要确定该设备过去正在一个 `async` 方法中实际上在执行什么操作可能会很困难，因为堆栈已经丢失了始发调用的上下文并且已经在另一个不同的线程上运行了 `async` 代码。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="5e3f1-112">然而，我们可以推断出该应用正在试图加载其首页。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="5e3f1-113">在 `NavigationArgs.Setup` 的实现过程中，以下代码引起了访问冲突：</span><span class="sxs-lookup"><span data-stu-id="5e3f1-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="5e3f1-114">在此实例中，`AppViewModel.Current` 上的 `LayoutVM` 属性是 null\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="5e3f1-115">某些元数据的缺失引起微妙的行为差异并导致一个属性（而不是集）未以该应用预设的方式得到初始化。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="5e3f1-116">在 `LayoutVM` 应该得到初始化的代码中设置一个断点可能会缓解这一情况。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="5e3f1-117">然而，请注意 `LayoutVM` 的类型是 `App.Core.ViewModels.Layout.LayoutApplicationVM`。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="5e3f1-118">目前 rd.xml 文件中存在的唯一元数据指令是：</span><span class="sxs-lookup"><span data-stu-id="5e3f1-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="5e3f1-119">引起失败的可能原因是 `App.Core.ViewModels.Layout.LayoutApplicationVM` 是丢失的元数据，原因在于它位于一个不同的命名空间。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="5e3f1-120">在这种情况下，添加一个运行时指令让 `App.Core.ViewModels` 解决这一问题。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="5e3f1-121">根本原因在于 API 调用了返回 null 的 <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> 方法，且该应用默认忽略这一问题直到发生故障\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="5e3f1-122">在动态编程中，在 .NET Native 下使用反射 Api 是一种很好的做法，就是使用 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 在失败时引发异常的重载。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-122">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="5e3f1-123">这是一个孤立情形吗？</span><span class="sxs-lookup"><span data-stu-id="5e3f1-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="5e3f1-124">当使用 `App.Core.ViewModels` 时，可能也会出现其他问题。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="5e3f1-125">你必须决定是否值得确定并修复每个丢失的元数据异常，或节省时间并为类型的一个更大类添加指令。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="5e3f1-126">此处，为 `dynamic` 添加 `App.Core.ViewModels` 元数据可能最好的方法，前提是输出的二进制代码变大不会产生问题。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="5e3f1-127">代码能够重写吗？</span><span class="sxs-lookup"><span data-stu-id="5e3f1-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="5e3f1-128">如果该应用过去使用的是 `typeof(LayoutApplicationVM)` 而不是 `Type.GetType("LayoutApplicationVM")`，工具链可能已经保存了 `browse` 元数据。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="5e3f1-129">然而，它也可能没有创建 `invoke` 元数据，这在实例化该类型时可能会导致 [MissingMetadataException](missingmetadataexception-class-net-native.md) 异常。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="5e3f1-130">要阻止这一异常，你仍然必须为命名空间添加一个运行时指令或指定 `dynamic` 策略的类型。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="5e3f1-131">有关运行时指令的信息，请参阅 [运行时指令 (rd.xml) 配置文件参考](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="5e3f1-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3f1-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e3f1-132">See also</span></span>

- [<span data-ttu-id="5e3f1-133">入门</span><span class="sxs-lookup"><span data-stu-id="5e3f1-133">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="5e3f1-134">示例：处理绑定数据时出现的异常</span><span class="sxs-lookup"><span data-stu-id="5e3f1-134">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)
