---
title: 窗体和验证
description: 了解如何在中通过客户端验证生成窗体 Blazor 。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: 1a99719f59415872510aef051d1f3c73daf53e15
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173271"
---
# <a name="forms-and-validation"></a><span data-ttu-id="9f3ad-103">窗体和验证</span><span class="sxs-lookup"><span data-stu-id="9f3ad-103">Forms and validation</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9f3ad-104">ASP.NET Web 窗体框架包含一组验证服务器控件，这些控件处理)  (、、等输入到窗体中的验证用户输入 `RequiredFieldValidator` `CompareValidator` `RangeValidator` 。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-104">The ASP.NET Web Forms framework includes a set of validation server controls that handle validating user input entered into a form (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`, and so on).</span></span> <span data-ttu-id="9f3ad-105">ASP.NET Web 窗体框架还支持模型绑定，并基于)  (、、等数据批注验证模型 `[Required]` `[StringLength]` `[Range]` 。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-105">The ASP.NET Web Forms framework also supports model binding and validating the model based on data annotations (`[Required]`, `[StringLength]`, `[Range]`, and so on).</span></span> <span data-ttu-id="9f3ad-106">使用基于 JavaScript 的非强制验证，可以在服务器和客户端上强制实施验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-106">The validation logic can be enforced both on the server and on the client using unobtrusive JavaScript-based validation.</span></span> <span data-ttu-id="9f3ad-107">`ValidationSummary`服务器控件用于向用户显示验证错误的摘要。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-107">The `ValidationSummary` server control is used to display a summary of the validation errors to the user.</span></span>

Blazor<span data-ttu-id="9f3ad-108">支持在客户端和服务器之间共享验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-108"> supports the sharing of validation logic between both the client and the server.</span></span> <span data-ttu-id="9f3ad-109">ASP.NET 提供了许多常见服务器验证的预构建 JavaScript 实现。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-109">ASP.NET provides pre-built JavaScript implementations of many common server validations.</span></span> <span data-ttu-id="9f3ad-110">在许多情况下，开发人员仍需编写 JavaScript 来完全实现应用程序特定的验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-110">In many cases, the developer still has to write JavaScript to fully implement their app-specific validation logic.</span></span> <span data-ttu-id="9f3ad-111">可以在服务器和客户端上使用相同的模型类型、数据注释和验证逻辑。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-111">The same model types, data annotations, and validation logic can be used on both the server and client.</span></span>

Blazor<span data-ttu-id="9f3ad-112">提供一组输入组件。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-112"> provides a set of input components.</span></span> <span data-ttu-id="9f3ad-113">输入组件会将绑定字段数据处理到模型，并在提交窗体时验证用户输入。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-113">The input components handle binding field data to a model and validating the user input when the form is submitted.</span></span>

|<span data-ttu-id="9f3ad-114">输入组件</span><span class="sxs-lookup"><span data-stu-id="9f3ad-114">Input component</span></span>|<span data-ttu-id="9f3ad-115">呈现的 HTML 元素</span><span class="sxs-lookup"><span data-stu-id="9f3ad-115">Rendered HTML element</span></span>    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

<span data-ttu-id="9f3ad-116">`EditForm`组件包装这些输入组件，并通过协调验证过程 `EditContext` 。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-116">The `EditForm` component wraps these input components and orchestrates the validation process through an `EditContext`.</span></span> <span data-ttu-id="9f3ad-117">创建时 `EditForm` ，可以使用参数指定要绑定到的模型实例 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-117">When creating an `EditForm`, you specify what model instance to bind to using the `Model` parameter.</span></span> <span data-ttu-id="9f3ad-118">验证通常是使用数据批注完成的，并且可以进行扩展。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-118">Validation is typically done using data annotations, and it's extensible.</span></span> <span data-ttu-id="9f3ad-119">若要启用基于数据批注的验证，请将该 `DataAnnotationsValidator` 组件添加为的子组件 `EditForm` 。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-119">To enable data annotation-based validation, add the `DataAnnotationsValidator` component as a child of the `EditForm`.</span></span> <span data-ttu-id="9f3ad-120">`EditForm`组件提供了一个方便的事件，用于处理有效的 (`OnValidSubmit`) 和 (`OnInvalidSubmit`) 提交无效。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-120">The `EditForm` component provides a convenient event for handling valid (`OnValidSubmit`) and invalid (`OnInvalidSubmit`) submissions.</span></span> <span data-ttu-id="9f3ad-121">还有一个更通用的 `OnSubmit` 事件，可让你自行触发和处理验证。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-121">There's also a more generic `OnSubmit` event that lets you trigger and handle the validation yourself.</span></span>

<span data-ttu-id="9f3ad-122">若要显示验证错误摘要，请使用 `ValidationSummary` 组件。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-122">To display a validation error summary, use the `ValidationSummary` component.</span></span> <span data-ttu-id="9f3ad-123">若要显示特定输入字段的验证消息，请使用 `ValidationMessage` 组件，并为 `For` 指向相应模型成员的参数指定 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-123">To display validation messages for a specific input field, use the `ValidationMessage` component, specifying a lambda expression for the `For` parameter that points to the appropriate model member.</span></span>

<span data-ttu-id="9f3ad-124">以下模型类型使用数据批注定义了若干验证规则：</span><span class="sxs-lookup"><span data-stu-id="9f3ad-124">The following model type defines several validation rules using data annotations:</span></span>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

<span data-ttu-id="9f3ad-125">下面的组件演示如何 Blazor 基于模型类型在中生成窗体 `Starship` ：</span><span class="sxs-lookup"><span data-stu-id="9f3ad-125">The following component demonstrates building a form in Blazor based on the `Starship` model type:</span></span>

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

<span data-ttu-id="9f3ad-126">提交窗体后，不会将模型绑定的数据保存到任何数据存储，如数据库。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-126">After the form submission, the model-bound data hasn't been saved to any data store, like a database.</span></span> <span data-ttu-id="9f3ad-127">在 Blazor WebAssembly 应用程序中，必须将数据发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-127">In a Blazor WebAssembly app, the data must be sent to the server.</span></span> <span data-ttu-id="9f3ad-128">例如，使用 HTTP POST 请求。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-128">For example, using an HTTP POST request.</span></span> <span data-ttu-id="9f3ad-129">在 Blazor 服务器应用中，数据已在服务器上，但必须持久保存。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-129">In a Blazor Server app, the data is already on the server, but it must be persisted.</span></span> <span data-ttu-id="9f3ad-130">处理应用程序中的数据访问 Blazor 是处理[数据](data.md)部分的主题。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-130">Handling data access in Blazor apps is the subject of the [Dealing with data](data.md) section.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9f3ad-131">其他资源</span><span class="sxs-lookup"><span data-stu-id="9f3ad-131">Additional resources</span></span>

<span data-ttu-id="9f3ad-132">有关应用中[表单和验证](/aspnet/core/blazor/forms-validation)的详细信息 Blazor ，请参阅 Blazor 文档。</span><span class="sxs-lookup"><span data-stu-id="9f3ad-132">For more information on [forms and validation](/aspnet/core/blazor/forms-validation) in Blazor apps, see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9f3ad-133">[上一页](state-management.md)
>[下一页](data.md)</span><span class="sxs-lookup"><span data-stu-id="9f3ad-133">[Previous](state-management.md)
[Next](data.md)</span></span>
