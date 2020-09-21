---
ms.openlocfilehash: 015696d8687dddc144c1dee3804e9ac3393cde4d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539569"
---
### <a name="obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed"></a><span data-ttu-id="221c3-101">已删除过时防伪、CORS、诊断、MVC 和路由 API</span><span class="sxs-lookup"><span data-stu-id="221c3-101">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>

<span data-ttu-id="221c3-102">删除了 ASP.NET Core 2.2 中的过时成员和兼容性开关。</span><span class="sxs-lookup"><span data-stu-id="221c3-102">Obsolete members and compatibility switches in ASP.NET Core 2.2 were removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="221c3-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="221c3-103">Version introduced</span></span>

<span data-ttu-id="221c3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="221c3-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="221c3-105">更改原因</span><span class="sxs-lookup"><span data-stu-id="221c3-105">Reason for change</span></span>

<span data-ttu-id="221c3-106">随着时间的推移，API 图面会得到改进。</span><span class="sxs-lookup"><span data-stu-id="221c3-106">Improvement of API surface over time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="221c3-107">建议操作</span><span class="sxs-lookup"><span data-stu-id="221c3-107">Recommended action</span></span>

<span data-ttu-id="221c3-108">针对 .NET Core 2.2 时，请遵循过时生成消息中的指导来改为采用新 API。</span><span class="sxs-lookup"><span data-stu-id="221c3-108">While targeting .NET Core 2.2, follow the guidance in the obsolete build messages to adopt new APIs instead.</span></span>

#### <a name="category"></a><span data-ttu-id="221c3-109">类别</span><span class="sxs-lookup"><span data-stu-id="221c3-109">Category</span></span>

<span data-ttu-id="221c3-110">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="221c3-110">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="221c3-111">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="221c3-111">Affected APIs</span></span>

<span data-ttu-id="221c3-112">以下类型和成员标记为对 ASP.NET Core 2.1 和 2.2 过时：</span><span class="sxs-lookup"><span data-stu-id="221c3-112">The following types and members were marked as obsolete for ASP.NET Core 2.1 and 2.2:</span></span>

<span data-ttu-id="221c3-113">**类型**</span><span class="sxs-lookup"><span data-stu-id="221c3-113">**Types**</span></span>

- `Microsoft.AspNetCore.Diagnostics.Views.WelcomePage`
- `Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue`
- `Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView`
- `Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperResult`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Wrapper`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Wrapper`
- `Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsFeatureProvider`
- `Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder`
- `Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata`
- `Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata`

<span data-ttu-id="221c3-114">**构造函数**</span><span class="sxs-lookup"><span data-stu-id="221c3-114">**Constructors**</span></span>

- `Microsoft.AspNetCore.Cors.Infrastructure.CorsService(IOptions{CorsOptions})`
- `Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder(ILoggerFactory,UrlEncoder,ObjectPool{UriBuildingContext},IInlineConstraintResolver)`
- `Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext`
- `Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider(IOptions{MvcOptions},IInlineConstraintResolver,IModelMetadataProvider)`
- `Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider(IOptions{MvcOptions},IInlineConstraintResolver,IModelMetadataProvider,IActionResultTypeMapper)`
- `Microsoft.AspNetCore.Mvc.Formatters.FormatFilter(IOptions{MvcOptions})`
- ``Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder`1(IModelBinder)``
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder`
- [<span data-ttu-id="221c3-115">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder\`1(IModelBinder)</span><span class="sxs-lookup"><span data-stu-id="221c3-115">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder\`1(IModelBinder)</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.binders.collectionmodelbinder-1.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_ModelBinding_Binders_CollectionModelBinder_1__ctor_Microsoft_AspNetCore_Mvc_ModelBinding_IModelBinder_)
- [<span data-ttu-id="221c3-116">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder(IDictionary\`2)</span><span class="sxs-lookup"><span data-stu-id="221c3-116">Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder(IDictionary\`2)</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.binders.complextypemodelbinder.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_ModelBinding_Binders_ComplexTypeModelBinder__ctor_System_Collections_Generic_IDictionary_Microsoft_AspNetCore_Mvc_ModelBinding_ModelMetadata_Microsoft_AspNetCore_Mvc_ModelBinding_IModelBinder__)
- ``Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder`2(IModelBinder,IModelBinder)``
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder(System.Globalization.NumberStyles)`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder(System.Globalization.NumberStyles)`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder`
- ``Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder`2(IModelBinder,IModelBinder)``
- `Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder(System.Type)`
- `Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes(IEnumerable{System.Object})`
- `Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes(IEnumerable{System.Object},IEnumerable{System.Object})`
- `Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory(IModelMetadataProvider,IOptions{MvcOptions})`
- `Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder(IModelMetadataProvider,IModelBinderFactory,IObjectModelValidator)`
- [<span data-ttu-id="221c3-117">Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint()</span><span class="sxs-lookup"><span data-stu-id="221c3-117">Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint()</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.routing.knownroutevalueconstraint.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_Routing_KnownRouteValueConstraint__ctor)
- `Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter`
- `Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter(System.Boolean)`
- `Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter(MvcOptions)`
- `Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter`
- `Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter(System.Boolean)`
- `Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter(MvcOptions)`
- [<span data-ttu-id="221c3-118">Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper(IHostingEnvironment,IMemoryCache,HtmlEncoder,IUrlHelperFactory)</span><span class="sxs-lookup"><span data-stu-id="221c3-118">Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper(IHostingEnvironment,IMemoryCache,HtmlEncoder,IUrlHelperFactory)</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.taghelpers.imagetaghelper.-ctor?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_TagHelpers_ImageTagHelper__ctor_Microsoft_AspNetCore_Hosting_IHostingEnvironment_Microsoft_Extensions_Caching_Memory_IMemoryCache_System_Text_Encodings_Web_HtmlEncoder_Microsoft_AspNetCore_Mvc_Routing_IUrlHelperFactory_)
- `Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper(IHostingEnvironment,IMemoryCache,HtmlEncoder,JavaScriptEncoder,IUrlHelperFactory)`
- `Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper(IHostingEnvironment,IMemoryCache,HtmlEncoder,JavaScriptEncoder,IUrlHelperFactory)`
- `Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter(RazorPageBase)`

<span data-ttu-id="221c3-119">**属性**</span><span class="sxs-lookup"><span data-stu-id="221c3-119">**Properties**</span></span>

- `Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain`
- `Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName`
- `Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath`
- `Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl`
- `Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery`
- `Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses`
- `Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName`
- `Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain`
- `Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat`
- `Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes`
- `Microsoft.AspNetCore.Mvc.MvcOptions.AllowCombiningAuthorizeFilters`
- `Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent`
- `Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes`
- `Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy`
- `Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType`
- `Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute`
- `Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix`
- `Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas`
- `Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptionsRequests`
- `Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler`

<span data-ttu-id="221c3-120">**方法**</span><span class="sxs-lookup"><span data-stu-id="221c3-120">**Methods**</span></span>

- `Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(ActionContext)`
- `Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(ActionContext)`
- `Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(ActionContext)`
- `Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(ActionContext)`
- `Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(ActionContext)`
- `Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(ActionContext,IValueProvider,ParameterDescriptor)`
- [<span data-ttu-id="221c3-121">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(ActionContext,IValueProvider,ParameterDescriptor,Object)</span><span class="sxs-lookup"><span data-stu-id="221c3-121">Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(ActionContext,IValueProvider,ParameterDescriptor,Object)</span></span>](/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.parameterbinder.bindmodelasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Mvc_ModelBinding_ParameterBinder_BindModelAsync_Microsoft_AspNetCore_Mvc_ActionContext_Microsoft_AspNetCore_Mvc_ModelBinding_IValueProvider_Microsoft_AspNetCore_Mvc_Abstractions_ParameterDescriptor_System_Object_)

<!--

#### Affected APIs

**Types**

- `T:Microsoft.AspNetCore.Diagnostics.Views.WelcomePage`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperResult`
- `T:Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Wrapper`
- `T:Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Wrapper`
- `T:Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsFeatureProvider`
- `T:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder`
- `T:Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata`
- `T:Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata`

**Constructors**

- `M:Microsoft.AspNetCore.Cors.Infrastructure.CorsService.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Cors.Infrastructure.CorsOptions})`
- `M:Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder.#ctor(Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.UrlEncoder,Microsoft.Extensions.ObjectPool.ObjectPool{Microsoft.AspNetCore.Routing.Internal.UriBuildingContext},Microsoft.AspNetCore.Routing.IInlineConstraintResolver)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider)`
- `M:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.Infrastructure.IActionResultTypeMapper)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.FormatFilter.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})",
"nameWithType": "FormatFilter.FormatFilter(IOptions<MvcOptions>)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder`1.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder`1.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder.#ctor(System.Collections.Generic.IDictionary{Microsoft.AspNetCore.Mvc.ModelBinding.ModelMetadata,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder`2.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder.#ctor(System.Globalization.NumberStyles)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder.#ctor(System.Globalization.NumberStyles)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder`2.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder.#ctor(System.Type)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.#ctor(System.Collections.Generic.IEnumerable{System.Object})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.#ctor(System.Collections.Generic.IEnumerable{System.Object},System.Collections.Generic.IEnumerable{System.Object})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinderFactory,Microsoft.AspNetCore.Mvc.ModelBinding.Validation.IObjectModelValidator)`
- `M:Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor(System.Boolean)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor(Microsoft.AspNetCore.Mvc.MvcOptions)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor(System.Boolean)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor(Microsoft.AspNetCore.Mvc.MvcOptions)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter.#ctor(Microsoft.AspNetCore.Mvc.Razor.RazorPageBase)`

**Properties**

- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl`
- `P:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery`
- `P:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path`
- `P:Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes`
- `P:Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowCombiningAuthorizeFilters`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType`
- `P:Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute`
- `P:Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptionsRequests`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler`

**Methods**

- `M:Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor,System.Object)`

-->
