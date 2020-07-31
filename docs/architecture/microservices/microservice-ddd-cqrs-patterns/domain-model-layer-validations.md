---
title: 在域模型层中设计验证
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 了解域模型验证的关键概念。
ms.date: 10/08/2018
ms.openlocfilehash: f1e2d7430c642ad47f79cdd34d3a65e2cc70e239
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164280"
---
# <a name="design-validations-in-the-domain-model-layer"></a><span data-ttu-id="09b13-103">在域模型层中设计验证</span><span class="sxs-lookup"><span data-stu-id="09b13-103">Design validations in the domain model layer</span></span>

<span data-ttu-id="09b13-104">在 DDD 中，验证规则可以看作不变量。</span><span class="sxs-lookup"><span data-stu-id="09b13-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="09b13-105">聚合的主要责任是对该聚合内所有实体跨状态更改来执行不变量。</span><span class="sxs-lookup"><span data-stu-id="09b13-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="09b13-106">域实体应始终为有效的实体。</span><span class="sxs-lookup"><span data-stu-id="09b13-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="09b13-107">应始终为 true 的对象存在一定数量的不变量。</span><span class="sxs-lookup"><span data-stu-id="09b13-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="09b13-108">例如，订单项对象始终得有一个必须为正整数的数量，以及项目名称和价格。</span><span class="sxs-lookup"><span data-stu-id="09b13-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="09b13-109">因此，执行不变量是域实体（尤其是聚合根）的职责，而实体对象应不能在无效的情况下存在。</span><span class="sxs-lookup"><span data-stu-id="09b13-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="09b13-110">不变量规则只需表达为协定，当它们遭违反时会引发异常或通知。</span><span class="sxs-lookup"><span data-stu-id="09b13-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="09b13-111">这背后的原因是，很多 bug 因对象处于它们不应处于的状态而发生。</span><span class="sxs-lookup"><span data-stu-id="09b13-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="09b13-112">来自 Greg Young 的[联机讨论](http://codebetter.com/gregyoung/2009/05/22/always-valid/)给出了很好的解释。</span><span class="sxs-lookup"><span data-stu-id="09b13-112">This [online discussion](http://codebetter.com/gregyoung/2009/05/22/always-valid/) is a good explanation from Greg Young.</span></span>

<span data-ttu-id="09b13-113">比如说，我们现在有一个采用 UserProfile 的 SendUserCreationEmailService...我们可以如何理性解释该服务中其名称不为 null？</span><span class="sxs-lookup"><span data-stu-id="09b13-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="09b13-114">是不是要再次检查？</span><span class="sxs-lookup"><span data-stu-id="09b13-114">Do we check it again?</span></span> <span data-ttu-id="09b13-115">或者更有可能...不需要花精力检查而是“期待更好的发生”- 希望其他人在将其发送给你之前花时间进行了验证。</span><span class="sxs-lookup"><span data-stu-id="09b13-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="09b13-116">当然，使用 TDD 时，我们首先应该编写的一个测试是，我是否向客户发送了会引发错误的 null 名称。</span><span class="sxs-lookup"><span data-stu-id="09b13-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="09b13-117">但是，一旦我们开始反复编写这些类型的测试，我们就会认识到...“等一下，如果我们从不允许名称成为 null，我们就不会有所有这些测试”。</span><span class="sxs-lookup"><span data-stu-id="09b13-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests".</span></span>

## <a name="implement-validations-in-the-domain-model-layer"></a><span data-ttu-id="09b13-118">在域模型层中实现验证</span><span class="sxs-lookup"><span data-stu-id="09b13-118">Implement validations in the domain model layer</span></span>

<span data-ttu-id="09b13-119">验证通常在域实体构造函数或可以更改该实体的方法中实现。</span><span class="sxs-lookup"><span data-stu-id="09b13-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="09b13-120">有多种方法来实现验证，例如验证失败时验证数据和引发的异常。</span><span class="sxs-lookup"><span data-stu-id="09b13-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="09b13-121">还有更多高级的模式，例如使用验证的规范模式和通知模式来返回一系列错误，而不是在异常发生时返回每个验证的异常。</span><span class="sxs-lookup"><span data-stu-id="09b13-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validate-conditions-and-throw-exceptions"></a><span data-ttu-id="09b13-122">验证条件和引发异常</span><span class="sxs-lookup"><span data-stu-id="09b13-122">Validate conditions and throw exceptions</span></span>

<span data-ttu-id="09b13-123">下面的代码示例通过引发异常显示域实体中最简单的验证方法。</span><span class="sxs-lookup"><span data-stu-id="09b13-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="09b13-124">在本部分末尾的引用表中，可以看到指向基于之前讨论的模式的更多高级实现。</span><span class="sxs-lookup"><span data-stu-id="09b13-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="09b13-125">更好的示例将演示，需要确保内部状态未更改，或者方法的所有变化都已发生。</span><span class="sxs-lookup"><span data-stu-id="09b13-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="09b13-126">例如，下面的实现将使对象保持处于无效状态：</span><span class="sxs-lookup"><span data-stu-id="09b13-126">For example, the following implementation would leave the object in an invalid state:</span></span>

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shippingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

<span data-ttu-id="09b13-127">如果状态的值无效，则第一个地址行和城市已更改。</span><span class="sxs-lookup"><span data-stu-id="09b13-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="09b13-128">这可能使地址无效。</span><span class="sxs-lookup"><span data-stu-id="09b13-128">That might make the address invalid.</span></span>

<span data-ttu-id="09b13-129">类似的方法可用于实体的构造函数中，引发异常来确保实体在创建后是有效的。</span><span class="sxs-lookup"><span data-stu-id="09b13-129">A similar approach can be used in the entity's constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="use-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="09b13-130">在模型中根据数据注释使用验证属性</span><span class="sxs-lookup"><span data-stu-id="09b13-130">Use validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="09b13-131">数据注释与 Required 或 MaxLength 特性一样，可用于配置 EF Core 数据库字段属性（[表映射](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping)部分对此进行了详细说明）。自 .NET Framework 中的 EF 4.x 以来，可使用数据注释进行实体验证，但[它们不再适用于 EF Core 中的实体验证](https://github.com/dotnet/efcore/issues/3680)（<xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> 方法也是如此）。</span><span class="sxs-lookup"><span data-stu-id="09b13-131">Data annotations, like the Required or MaxLength attributes, can be used to configure EF Core database field properties, as explained in detail in the [Table mapping](infrastructure-persistence-layer-implementation-entity-framework-core.md#table-mapping) section, but [they no longer work for entity validation in EF Core](https://github.com/dotnet/efcore/issues/3680) (neither does the <xref:System.ComponentModel.DataAnnotations.IValidatableObject.Validate%2A?displayProperty=nameWithType> method), as they have done since EF 4.x in .NET Framework.</span></span>

<span data-ttu-id="09b13-132">在模型绑定期间（即，在像往常一样调用控制器的操作之前），数据注释和 <xref:System.ComponentModel.DataAnnotations.IValidatableObject> 接口仍然可用于模型验证，但该模型应该是一个视图模型或 DTO，因此这属于 MVC 或 API 方面的问题，而不是域模型方面的问题。</span><span class="sxs-lookup"><span data-stu-id="09b13-132">Data annotations and the <xref:System.ComponentModel.DataAnnotations.IValidatableObject> interface can still be used for model validation during model binding, prior to the controller's actions invocation as usual, but that model is meant to be a ViewModel or DTO and that's an MVC or API concern not a domain model concern.</span></span>

<span data-ttu-id="09b13-133">弄清楚概念上的差别后，如果你的操作收到实体类对象参数，你仍然可以在实体类中使用数据注释和 `IValidatableObject` 进行验证，虽然并不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="09b13-133">Having made the conceptual difference clear, you can still use data annotations and `IValidatableObject` in the entity class for validation, if your actions receive an entity class object parameter, which is not recommended.</span></span> <span data-ttu-id="09b13-134">在这种情况下，将在模型绑定期间（就在调用操作之前）进行验证，你可以检查控制器的 ModelState.IsValid 属性以检查结果，但是，验证操作发生在控制器中，而不是在将实体对象永久保存在 DbContext 中之前，这一点也与自 EF 4.x 以来的版本不同。</span><span class="sxs-lookup"><span data-stu-id="09b13-134">In that case, validation will occur upon model binding, just before invoking the action and you can check the controller's ModelState.IsValid property to check the result, but then again, it happens in the controller, not before persisting the entity object in the DbContext, as it had done since EF 4.x.</span></span>

<span data-ttu-id="09b13-135">你仍然可以通过重写 DbContext 的 SaveChanges 方法，在实体类中使用数据注释和 `IValidatableObject.Validate` 方法来实现自定义验证。</span><span class="sxs-lookup"><span data-stu-id="09b13-135">You can still implement custom validation in the entity class using data annotations and the `IValidatableObject.Validate` method, by overriding the DbContext's SaveChanges method.</span></span>

<span data-ttu-id="09b13-136">在 [GitHub 上的此注释](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539)中，可以看到用于验证 `IValidatableObject` 实体的示例实现。</span><span class="sxs-lookup"><span data-stu-id="09b13-136">You can see a sample implementation for validating `IValidatableObject` entities in [this comment on GitHub](https://github.com/dotnet/efcore/issues/3680#issuecomment-155502539).</span></span> <span data-ttu-id="09b13-137">该示例不执行基于属性的验证，但应该可以在同一替代机制中使用反射来轻松实现此类验证。</span><span class="sxs-lookup"><span data-stu-id="09b13-137">That sample doesn't do attribute-based validations, but they should be easy to implement using reflection in the same override.</span></span>

<span data-ttu-id="09b13-138">但是，从 DDD 的角度来看，最好通过在实体行为方法中使用异常，或者通过实现规范和通知模式来执行验证规则，从而使域模型保持精简。</span><span class="sxs-lookup"><span data-stu-id="09b13-138">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity's behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span>

<span data-ttu-id="09b13-139">在将接受输入的 ViewModel 类（而非域实体）中在应用程序层上使用数据注释来允许 UI 层中的模型验证很有意义。</span><span class="sxs-lookup"><span data-stu-id="09b13-139">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="09b13-140">但是，这不应在域模型内排除验证时完成。</span><span class="sxs-lookup"><span data-stu-id="09b13-140">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validate-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="09b13-141">通过实现规范模式和通知模式来验证实体</span><span class="sxs-lookup"><span data-stu-id="09b13-141">Validate entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="09b13-142">最后，域模型中实现验证的更复杂方法是，通过结合使用通知模式来实现规范模式，如后面列出的其他资源中所述。</span><span class="sxs-lookup"><span data-stu-id="09b13-142">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="09b13-143">值得一提的是，还可使用这些模式中一个 - 例如通过控制语句进行手动验证，但使用通知模式来堆叠并返回验证错误列表。</span><span class="sxs-lookup"><span data-stu-id="09b13-143">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="use-deferred-validation-in-the-domain"></a><span data-ttu-id="09b13-144">在域中使用延迟的验证</span><span class="sxs-lookup"><span data-stu-id="09b13-144">Use deferred validation in the domain</span></span>

<span data-ttu-id="09b13-145">有数种方法来处理域中的延迟验证。</span><span class="sxs-lookup"><span data-stu-id="09b13-145">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="09b13-146">[实现域驱动设计](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)一书中，Vaughn Vernon 在验证部分讨论了这些。</span><span class="sxs-lookup"><span data-stu-id="09b13-146">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="09b13-147">双重验证</span><span class="sxs-lookup"><span data-stu-id="09b13-147">Two-step validation</span></span>

<span data-ttu-id="09b13-148">此外考虑双重验证。</span><span class="sxs-lookup"><span data-stu-id="09b13-148">Also consider two-step validation.</span></span> <span data-ttu-id="09b13-149">在命令数据传输对象 (DTO) 上使用字段级别验证，在实体内使用域级别验证。</span><span class="sxs-lookup"><span data-stu-id="09b13-149">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="09b13-150">通过返回结果对象而非异常来让处理验证错误变得更容易，以便执行此操作。</span><span class="sxs-lookup"><span data-stu-id="09b13-150">You can do this by returning a result object instead of exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="09b13-151">例如通过将字段验证用于数据注释，你不用重复验证定义。</span><span class="sxs-lookup"><span data-stu-id="09b13-151">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="09b13-152">然而在 DTO（例如命令和 Viewmodel）的情况下，执行可以既位于服务器端又位于客户端端。</span><span class="sxs-lookup"><span data-stu-id="09b13-152">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="09b13-153">其他资源</span><span class="sxs-lookup"><span data-stu-id="09b13-153">Additional resources</span></span>

- <span data-ttu-id="09b13-154">**Rachel Appel。ASP.NET Core MVC 模型验证简介** </span><span class="sxs-lookup"><span data-stu-id="09b13-154">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC** </span></span>\
  <https://docs.microsoft.com/aspnet/core/mvc/models/validation>

- <span data-ttu-id="09b13-155">**Rick Anderson。添加验证** </span><span class="sxs-lookup"><span data-stu-id="09b13-155">**Rick Anderson. Adding validation** </span></span>\
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

- <span data-ttu-id="09b13-156">**Martin Fowler。Replacing Throwing Exceptions with Notification in Validations** \（在验证中将引发异常替换为通知）</span><span class="sxs-lookup"><span data-stu-id="09b13-156">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations** </span></span>\
  <https://martinfowler.com/articles/replaceThrowWithNotification.html>

- <span data-ttu-id="09b13-157">**Specification and Notification Patterns** \（规范和通知模式）</span><span class="sxs-lookup"><span data-stu-id="09b13-157">**Specification and Notification Patterns** </span></span>\
  <https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns>

- <span data-ttu-id="09b13-158">**Lev Gorodinski.Validation in Domain-Driven Design (DDD)**  \（域驱动设计 (DDD) 中的验证）</span><span class="sxs-lookup"><span data-stu-id="09b13-158">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)** </span></span>\
  <http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/>

- <span data-ttu-id="09b13-159">**Colin Jack。Domain Model Validation** \（域模型验证）</span><span class="sxs-lookup"><span data-stu-id="09b13-159">**Colin Jack. Domain Model Validation** </span></span>\
  <https://colinjack.blogspot.com/2008/03/domain-model-validation.html>

- <span data-ttu-id="09b13-160">**Jimmy Bogard。Validation in a DDD world** \（DDD 中的验证）</span><span class="sxs-lookup"><span data-stu-id="09b13-160">**Jimmy Bogard. Validation in a DDD world** </span></span>\
  <https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/>

> [!div class="step-by-step"]
> <span data-ttu-id="09b13-161">[上一页](enumeration-classes-over-enum-types.md)
> [下一页](client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="09b13-161">[Previous](enumeration-classes-over-enum-types.md)
[Next](client-side-validation.md)</span></span>
