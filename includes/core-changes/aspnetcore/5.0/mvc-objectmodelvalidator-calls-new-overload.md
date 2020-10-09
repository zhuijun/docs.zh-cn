---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609288"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="f0541-101">MVC：ObjectModelValidator 调用 ValidationVisitor.Validate 的新重载</span><span class="sxs-lookup"><span data-stu-id="f0541-101">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="f0541-102">在 ASP.NET Core 5.0 中，添加了 <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> 的重载。</span><span class="sxs-lookup"><span data-stu-id="f0541-102">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="f0541-103">新重载接受包含以下属性的顶级模型实例：</span><span class="sxs-lookup"><span data-stu-id="f0541-103">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="f0541-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> 调用 `ValidationVisitor` 的这一新重载来执行验证。</span><span class="sxs-lookup"><span data-stu-id="f0541-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="f0541-105">如果你的验证库与 ASP.NET Core MVC 的模型验证系统集成，请关注此新重载。</span><span class="sxs-lookup"><span data-stu-id="f0541-105">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="f0541-106">有关讨论，请参阅 GitHub 问题 [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020)。</span><span class="sxs-lookup"><span data-stu-id="f0541-106">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f0541-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="f0541-107">Version introduced</span></span>

<span data-ttu-id="f0541-108">5.0</span><span class="sxs-lookup"><span data-stu-id="f0541-108">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f0541-109">旧行为</span><span class="sxs-lookup"><span data-stu-id="f0541-109">Old behavior</span></span>

<span data-ttu-id="f0541-110">`ObjectModelValidator` 在模型验证过程中调用以下重载：</span><span class="sxs-lookup"><span data-stu-id="f0541-110">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a><span data-ttu-id="f0541-111">新行为</span><span class="sxs-lookup"><span data-stu-id="f0541-111">New behavior</span></span>

<span data-ttu-id="f0541-112">`ObjectModelValidator` 在模型验证过程中调用以下重载：</span><span class="sxs-lookup"><span data-stu-id="f0541-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a><span data-ttu-id="f0541-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="f0541-113">Reason for change</span></span>

<span data-ttu-id="f0541-114">引入此更改是为了支持依赖于检查其他属性的验证程序，例如 <xref:System.ComponentModel.DataAnnotations.CompareAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f0541-114">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f0541-115">建议的操作</span><span class="sxs-lookup"><span data-stu-id="f0541-115">Recommended action</span></span>

<span data-ttu-id="f0541-116">依赖于 `ObjectModelValidator` 调用 `ValidationVisitor` 的现有重载的验证框架在面向 .NET 5.0 或更高版本时必须重写新方法：</span><span class="sxs-lookup"><span data-stu-id="f0541-116">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a><span data-ttu-id="f0541-117">类别</span><span class="sxs-lookup"><span data-stu-id="f0541-117">Category</span></span>

<span data-ttu-id="f0541-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f0541-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f0541-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f0541-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
