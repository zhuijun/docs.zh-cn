---
title: 如何编写用于 JSON 序列化的自定义转换器 - .NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: e0b769d7bb6b336d226cd48de1932524c4d7e74d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811062"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="f06ba-102">如何在 .NET 中编写用于 JSON 序列化（封送）的自定义转换器</span><span class="sxs-lookup"><span data-stu-id="f06ba-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="f06ba-103">本文介绍如何为 <xref:System.Text.Json> 命名空间中提供的 JSON 序列化类创建自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="f06ba-104">有关 `System.Text.Json` 简介，请参阅[如何在 .NET 中对 JSON 数据进行序列化和反序列化](system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="f06ba-105">转换器是一种将对象或值与 JSON 相互转换的类。</span><span class="sxs-lookup"><span data-stu-id="f06ba-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="f06ba-106">`System.Text.Json` 命名空间为映射到 JavaScript 基元的大多数基元类型提供内置转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="f06ba-107">可以编写自定义转换器来实现以下目标：</span><span class="sxs-lookup"><span data-stu-id="f06ba-107">You can write custom converters:</span></span>

* <span data-ttu-id="f06ba-108">重写内置转换器的默认行为。</span><span class="sxs-lookup"><span data-stu-id="f06ba-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="f06ba-109">例如，可能希望用 mm/dd/yyyy 格式而不是默认 ISO 8601-1:2019 格式来表示 `DateTime` 值。</span><span class="sxs-lookup"><span data-stu-id="f06ba-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="f06ba-110">支持自定义值类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-110">To support a custom value type.</span></span> <span data-ttu-id="f06ba-111">例如，`PhoneNumber` 结构。</span><span class="sxs-lookup"><span data-stu-id="f06ba-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="f06ba-112">还可以编写自定义转换器，以使用当前版本中未包含的功能自定义或扩展 `System.Text.Json`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="f06ba-113">本文后面部分介绍了以下方案：</span><span class="sxs-lookup"><span data-stu-id="f06ba-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="f06ba-114">[将推断类型反序列化为对象属性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="f06ba-115">[支持包含非字符串键的字典](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="f06ba-116">[支持多态反序列化](#support-polymorphic-deserialization)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="f06ba-117">[支持堆栈的往返\<T>](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="f06ba-118">自定义转换器模式</span><span class="sxs-lookup"><span data-stu-id="f06ba-118">Custom converter patterns</span></span>

<span data-ttu-id="f06ba-119">用于创建自定义转换器的模式有两种：基本模式和工厂模式。</span><span class="sxs-lookup"><span data-stu-id="f06ba-119">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="f06ba-120">工厂模式适用于处理类型 `Enum` 或开放式泛型的转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-120">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="f06ba-121">基本模式适用于非泛型或封闭式泛型类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-121">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="f06ba-122">例如，适用于以下类型的转换器需要工厂模式：</span><span class="sxs-lookup"><span data-stu-id="f06ba-122">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="f06ba-123">可以通过基本模式处理的类型的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="f06ba-123">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="f06ba-124">基本模式创建的类可以处理一种类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-124">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="f06ba-125">工厂模式创建的类在运行时确定所需的特定类型，并动态创建适当的转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-125">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="f06ba-126">示例基本转换器</span><span class="sxs-lookup"><span data-stu-id="f06ba-126">Sample basic converter</span></span>

<span data-ttu-id="f06ba-127">下面的示例是一个转换器，可重写现有数据类型的默认序列化。</span><span class="sxs-lookup"><span data-stu-id="f06ba-127">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="f06ba-128">该转换器将 mm/dd/yyyy 格式用于 `DateTimeOffset` 属性。</span><span class="sxs-lookup"><span data-stu-id="f06ba-128">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="f06ba-129">示例工厂模式转换器</span><span class="sxs-lookup"><span data-stu-id="f06ba-129">Sample factory pattern converter</span></span>

<span data-ttu-id="f06ba-130">下面的代码演示一个处理 `Dictionary<Enum,TValue>` 的自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-130">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="f06ba-131">该代码遵循工厂模式，因为第一个泛型类型参数是 `Enum`，第二个参数是开放参数。</span><span class="sxs-lookup"><span data-stu-id="f06ba-131">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="f06ba-132">`CanConvert` 方法仅对具有两个泛型参数的 `Dictionary` 返回 `true`，其中第一个参数是 `Enum` 类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-132">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="f06ba-133">内部转换器获取现有转换器，以处理在运行时为 `TValue` 提供的任何类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-133">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="f06ba-134">前面的代码与本文后面的[支持包含非字符串键的字典](#support-dictionary-with-non-string-key)中演示的代码相同。</span><span class="sxs-lookup"><span data-stu-id="f06ba-134">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="f06ba-135">遵循基本模式的步骤</span><span class="sxs-lookup"><span data-stu-id="f06ba-135">Steps to follow the basic pattern</span></span>

<span data-ttu-id="f06ba-136">以下步骤说明如何遵循基本模式来创建转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-136">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="f06ba-137">创建一个派生自 <xref:System.Text.Json.Serialization.JsonConverter%601> 的类，其中 `T` 是要进行序列化和反序列化的类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-137">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="f06ba-138">重写 `Read` 方法，以反序列化传入 JSON 并将其转换为类型 `T`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-138">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="f06ba-139">使用传递给方法的 <xref:System.Text.Json.Utf8JsonReader> 读取 JSON。</span><span class="sxs-lookup"><span data-stu-id="f06ba-139">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="f06ba-140">重写 `Write` 方法以序列化 `T` 类型的传入对象。</span><span class="sxs-lookup"><span data-stu-id="f06ba-140">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="f06ba-141">使用传递给方法的 <xref:System.Text.Json.Utf8JsonWriter> 写入 JSON。</span><span class="sxs-lookup"><span data-stu-id="f06ba-141">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="f06ba-142">仅当需要时才重写 `CanConvert` 方法。</span><span class="sxs-lookup"><span data-stu-id="f06ba-142">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="f06ba-143">当要转换的类型属于类型 `T` 时，默认实现会返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-143">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="f06ba-144">因此，仅支持类型 `T` 的转换器不需要重写此方法。</span><span class="sxs-lookup"><span data-stu-id="f06ba-144">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="f06ba-145">有关的确需要重写此方法的转换器的示例，请参阅本文后面的[多态反序列化](#support-polymorphic-deserialization)部分。</span><span class="sxs-lookup"><span data-stu-id="f06ba-145">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="f06ba-146">可以参阅[内置转换器源代码](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/)作为用于编写自定义转换器的参考实现。</span><span class="sxs-lookup"><span data-stu-id="f06ba-146">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="f06ba-147">遵循工厂模式的步骤</span><span class="sxs-lookup"><span data-stu-id="f06ba-147">Steps to follow the factory pattern</span></span>

<span data-ttu-id="f06ba-148">以下步骤说明如何遵循工厂模式来创建转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-148">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="f06ba-149">创建一个从 <xref:System.Text.Json.Serialization.JsonConverterFactory> 派生的类。</span><span class="sxs-lookup"><span data-stu-id="f06ba-149">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="f06ba-150">重写 `CanConvert` 方法，以在要转换的类型是转换器可处理的类型时返回 true。</span><span class="sxs-lookup"><span data-stu-id="f06ba-150">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="f06ba-151">例如，如果转换器适用于 `List<T>`，则它可能仅处理 `List<int>`、`List<string>` 和 `List<DateTime>`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-151">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="f06ba-152">重写 `CreateConverter` 方法，以返回将处理在运行时提供的要转换的类型的转换器类实例。</span><span class="sxs-lookup"><span data-stu-id="f06ba-152">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="f06ba-153">创建 `CreateConverter` 方法实例化的转换器类。</span><span class="sxs-lookup"><span data-stu-id="f06ba-153">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="f06ba-154">开放式泛型需要工厂模式，因为用于将对象与字符串相互转换的代码对于所有类型并不相同。</span><span class="sxs-lookup"><span data-stu-id="f06ba-154">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="f06ba-155">适用于开放式泛型类型（例如 `List<T>`）的转换器必须在幕后为封闭式泛型类型（例如 `List<DateTime>`）创建转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-155">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="f06ba-156">必须编写代码来处理转换器可处理的每种封闭式泛型类型。</span><span class="sxs-lookup"><span data-stu-id="f06ba-156">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="f06ba-157">`Enum` 类型类似于开放式泛型类型：适用于 `Enum` 的转换器必须在幕后为特定 `Enum`（例如`WeekdaysEnum`）创建转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-157">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="f06ba-158">错误处理</span><span class="sxs-lookup"><span data-stu-id="f06ba-158">Error handling</span></span>

<span data-ttu-id="f06ba-159">如果需要在错误处理代码中引发异常，请考虑在不使用消息的情况下引发 <xref:System.Text.Json.JsonException>。</span><span class="sxs-lookup"><span data-stu-id="f06ba-159">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="f06ba-160">此异常类型会自动创建消息，其中包括导致错误的 JSON 部分的路径。</span><span class="sxs-lookup"><span data-stu-id="f06ba-160">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="f06ba-161">例如，语句 `throw new JsonException();` 会生成如以下示例的错误消息：</span><span class="sxs-lookup"><span data-stu-id="f06ba-161">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="f06ba-162">如果提供消息（例如 `throw new JsonException("Error occurred")`），则异常仍会在 <xref:System.Text.Json.JsonException.Path> 属性中提供路径。</span><span class="sxs-lookup"><span data-stu-id="f06ba-162">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="f06ba-163">注册自定义转换器</span><span class="sxs-lookup"><span data-stu-id="f06ba-163">Register a custom converter</span></span>

<span data-ttu-id="f06ba-164">注册自定义转换器，使 `Serialize` 和 `Deserialize` 方法可使用它。</span><span class="sxs-lookup"><span data-stu-id="f06ba-164">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="f06ba-165">选择以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="f06ba-165">Choose one of the following approaches:</span></span>

* <span data-ttu-id="f06ba-166">向 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合添加转换器类的实例。</span><span class="sxs-lookup"><span data-stu-id="f06ba-166">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="f06ba-167">将 [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 特性应用于需要自定义转换器的属性。</span><span class="sxs-lookup"><span data-stu-id="f06ba-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="f06ba-168">将 [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 特性应用于表示自定义值类型的类或结构。</span><span class="sxs-lookup"><span data-stu-id="f06ba-168">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="f06ba-169">注册示例 - 转换器集合</span><span class="sxs-lookup"><span data-stu-id="f06ba-169">Registration sample - Converters collection</span></span>

<span data-ttu-id="f06ba-170">下面是一个示例，该示例将 <xref:System.ComponentModel.DateTimeOffsetConverter> 设为类型 <xref:System.DateTimeOffset> 的属性的默认值：</span><span class="sxs-lookup"><span data-stu-id="f06ba-170">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="f06ba-171">假设序列化以下类型的实例：</span><span class="sxs-lookup"><span data-stu-id="f06ba-171">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="f06ba-172">下面是演示使用自定义转换器的 JSON 输出的示例：</span><span class="sxs-lookup"><span data-stu-id="f06ba-172">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="f06ba-173">下面的代码使用的方法与使用自定义 `DateTimeOffset` 转换器进行反序列化相同：</span><span class="sxs-lookup"><span data-stu-id="f06ba-173">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="f06ba-174">注册示例 - 属性上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="f06ba-174">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="f06ba-175">下面的代码为 `Date` 属性选择自定义转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-175">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="f06ba-176">用于序列化 `WeatherForecastWithConverterAttribute` 的代码不需要使用 `JsonSerializeOptions.Converters`：</span><span class="sxs-lookup"><span data-stu-id="f06ba-176">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="f06ba-177">用于反序列化的代码也不需要使用 `Converters`：</span><span class="sxs-lookup"><span data-stu-id="f06ba-177">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="f06ba-178">注册示例 - 类型上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="f06ba-178">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="f06ba-179">下面的代码创建一个结构并向它应用 `[JsonConverter]` 属性：</span><span class="sxs-lookup"><span data-stu-id="f06ba-179">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="f06ba-180">下面是适用于上述结构的自定义转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-180">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="f06ba-181">结构上的 `[JsonConvert]` 属性将自定义转换器注册为类型 `Temperature` 的属性的默认值。</span><span class="sxs-lookup"><span data-stu-id="f06ba-181">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="f06ba-182">进行序列化或反序列化时，转换器会自动用于以下类型的 `TemperatureCelsius` 属性：</span><span class="sxs-lookup"><span data-stu-id="f06ba-182">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="f06ba-183">转换器注册优先级</span><span class="sxs-lookup"><span data-stu-id="f06ba-183">Converter registration precedence</span></span>

<span data-ttu-id="f06ba-184">在序列化或反序列化过程中，按以下顺序（从最高优先级到最低优先级来列出）为每个 JSON 元素选择转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-184">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="f06ba-185">应用于属性的 `[JsonConverter]`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-185">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="f06ba-186">向 `Converters` 集合添加的转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-186">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="f06ba-187">应用于自定义值类型或 POCO 的 `[JsonConverter]`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-187">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="f06ba-188">如果在 `Converters` 集合中注册了适用于某种类型的多个自定义转换器，则使用第一个为 `CanConvert` 返回 true 的转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-188">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="f06ba-189">仅当未注册适用自定义转换器时，才会选择内置转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-189">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="f06ba-190">常见方案的转换器示例</span><span class="sxs-lookup"><span data-stu-id="f06ba-190">Converter samples for common scenarios</span></span>

<span data-ttu-id="f06ba-191">以下各部分提供的转换器示例用于解决内置功能不处理的一些常见方案。</span><span class="sxs-lookup"><span data-stu-id="f06ba-191">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="f06ba-192">将推断类型反序列化为对象属性</span><span class="sxs-lookup"><span data-stu-id="f06ba-192">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="f06ba-193">支持包含非字符串键的字典</span><span class="sxs-lookup"><span data-stu-id="f06ba-193">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="f06ba-194">支持多态反序列化</span><span class="sxs-lookup"><span data-stu-id="f06ba-194">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)
* <span data-ttu-id="f06ba-195">[支持堆栈的往返\<T>](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-195">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="f06ba-196">将推断类型反序列化为对象属性</span><span class="sxs-lookup"><span data-stu-id="f06ba-196">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="f06ba-197">反序列化为类型 `object` 的属性时，将创建一个 `JsonElement` 对象。</span><span class="sxs-lookup"><span data-stu-id="f06ba-197">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="f06ba-198">这是因为反序列化程序不知道要创建的 CLR 类型，也不会尝试进行猜测。</span><span class="sxs-lookup"><span data-stu-id="f06ba-198">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="f06ba-199">例如，如果 JSON 属性具有“true”，则反序列化程序不会推断值为 `Boolean`，如果元素具有“01/01/2019”，则反序列化程序不会推断它是 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-199">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="f06ba-200">类型推理可能不准确。</span><span class="sxs-lookup"><span data-stu-id="f06ba-200">Type inference can be inaccurate.</span></span> <span data-ttu-id="f06ba-201">如果反序列化程序将没有小数点的 JSON 数字分析为 `long`，则当值最初序列化为 `ulong` 或 `BigInteger` 时，这可能会导致超出范围问题。</span><span class="sxs-lookup"><span data-stu-id="f06ba-201">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="f06ba-202">如果数字最初序列化为 `decimal`，则将具有小数点的数字分析为 `double` 可能会损失精度。</span><span class="sxs-lookup"><span data-stu-id="f06ba-202">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="f06ba-203">对于需要类型推理的方案，以下代码演示适用于 `object` 属性的自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-203">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="f06ba-204">代码：</span><span class="sxs-lookup"><span data-stu-id="f06ba-204">The code converts:</span></span>

* <span data-ttu-id="f06ba-205">将 `true` 和 `false` 转换为 `Boolean`</span><span class="sxs-lookup"><span data-stu-id="f06ba-205">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="f06ba-206">将不带小数的数字转换为 `long`</span><span class="sxs-lookup"><span data-stu-id="f06ba-206">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="f06ba-207">将带有小数的数字转换为 `double`</span><span class="sxs-lookup"><span data-stu-id="f06ba-207">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="f06ba-208">将日期转换为 `DateTime`</span><span class="sxs-lookup"><span data-stu-id="f06ba-208">Dates to `DateTime`</span></span>
* <span data-ttu-id="f06ba-209">将字符串转换为 `string`</span><span class="sxs-lookup"><span data-stu-id="f06ba-209">Strings to `string`</span></span>
* <span data-ttu-id="f06ba-210">将其他所有内容转换为 `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="f06ba-210">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="f06ba-211">下面的代码注册转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-211">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="f06ba-212">下面是一种具有 `object` 属性的示例类型：</span><span class="sxs-lookup"><span data-stu-id="f06ba-212">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="f06ba-213">以下要反序列化的 JSON 示例包含将作为 `DateTime`、`long` 和 `string` 进行反序列化的值：</span><span class="sxs-lookup"><span data-stu-id="f06ba-213">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="f06ba-214">如果没有自定义转换器，则反序列化会将 `JsonElement` 放入每个属性中。</span><span class="sxs-lookup"><span data-stu-id="f06ba-214">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="f06ba-215">`System.Text.Json.Serialization` 命名空间中的[单元测试文件夹](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)包含处理到 `object` 属性的反序列化的自定义转换器的更多示例。</span><span class="sxs-lookup"><span data-stu-id="f06ba-215">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="f06ba-216">支持包含非字符串键的字典</span><span class="sxs-lookup"><span data-stu-id="f06ba-216">Support Dictionary with non-string key</span></span>

<span data-ttu-id="f06ba-217">对字典集合的内置支持适用于 `Dictionary<string, TValue>`。</span><span class="sxs-lookup"><span data-stu-id="f06ba-217">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="f06ba-218">即，键必须是字符串。</span><span class="sxs-lookup"><span data-stu-id="f06ba-218">That is, the key must be a string.</span></span> <span data-ttu-id="f06ba-219">若要支持将整数或某种其他类型用作键的字典，需要自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-219">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="f06ba-220">下面的代码演示一个处理 `Dictionary<Enum,TValue>` 的自定义转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-220">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="f06ba-221">下面的代码注册转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-221">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="f06ba-222">该转换器可以序列化和反序列化使用以下 `Enum` 的以下类的 `TemperatureRanges` 属性：</span><span class="sxs-lookup"><span data-stu-id="f06ba-222">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="f06ba-223">来自序列化的 JSON 输出类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="f06ba-223">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="f06ba-224">`System.Text.Json.Serialization` 命名空间中的[单元测试文件夹](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)包含处理非字符串键字典的自定义转换器的更多示例。</span><span class="sxs-lookup"><span data-stu-id="f06ba-224">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="f06ba-225">支持多态反序列化</span><span class="sxs-lookup"><span data-stu-id="f06ba-225">Support polymorphic deserialization</span></span>

<span data-ttu-id="f06ba-226">内置功能提供有限范围的[多态序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)，但完全不支持反序列化。</span><span class="sxs-lookup"><span data-stu-id="f06ba-226">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="f06ba-227">反序列化需要自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-227">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="f06ba-228">例如，假设有一个 `Person` 抽象基类，其中包含 `Employee` 和 `Customer` 派生类。</span><span class="sxs-lookup"><span data-stu-id="f06ba-228">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="f06ba-229">多态反序列化意味着可以在设计时将 `Person` 指定为反序列化目标，JSON 中的 `Customer` 和 `Employee` 对象会在运行时正确地进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="f06ba-229">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="f06ba-230">在反序列化过程中，必须查找标识 JSON 中所需类型的线索。</span><span class="sxs-lookup"><span data-stu-id="f06ba-230">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="f06ba-231">可用的线索类型因各个方案而异。</span><span class="sxs-lookup"><span data-stu-id="f06ba-231">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="f06ba-232">例如，可以使用鉴别器属性，或者可能必须依赖于特定属性是否存在。</span><span class="sxs-lookup"><span data-stu-id="f06ba-232">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="f06ba-233">`System.Text.Json` 的当前版本不提供属性来指定如何处理多态反序列化方案，因此需要自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-233">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="f06ba-234">下面的代码演示一个基类、两个派生类和适用于它们的一个自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-234">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="f06ba-235">该转换器使用鉴别器属性执行多态反序列化。</span><span class="sxs-lookup"><span data-stu-id="f06ba-235">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="f06ba-236">类型鉴别器不在类定义中，而是在序列化过程中创建，在反序列化过程中进行读取。</span><span class="sxs-lookup"><span data-stu-id="f06ba-236">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="f06ba-237">下面的代码注册转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-237">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="f06ba-238">该转换器可以反序列化通过用于序列化的相同转换器而创建的 JSON，例如：</span><span class="sxs-lookup"><span data-stu-id="f06ba-238">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

<span data-ttu-id="f06ba-239">前面示例中的转换器代码会手动读取和写入每个属性。</span><span class="sxs-lookup"><span data-stu-id="f06ba-239">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="f06ba-240">一种替代方法是调用 `Deserialize` 或 `Serialize` 以执行某些工作。</span><span class="sxs-lookup"><span data-stu-id="f06ba-240">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="f06ba-241">有关示例，请参阅[此 StackOverflow 文章](https://stackoverflow.com/a/59744873/12509023)。</span><span class="sxs-lookup"><span data-stu-id="f06ba-241">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="f06ba-242">支持堆栈的往返\<T></span><span class="sxs-lookup"><span data-stu-id="f06ba-242">Support round-trip for Stack\<T></span></span>

<span data-ttu-id="f06ba-243">如果将 JSON 字符串反序列化为 <xref:System.Collections.Generic.Stack%601> 对象，然后再序列化该对象，则堆栈的内容将按相反的顺序排列。</span><span class="sxs-lookup"><span data-stu-id="f06ba-243">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="f06ba-244">此行为适用于以下类型和接口以及从它们派生的用户定义类型：</span><span class="sxs-lookup"><span data-stu-id="f06ba-244">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="f06ba-245">若要支持在堆栈中保留原始顺序的序列化和反序列化，则需要自定义转换器。</span><span class="sxs-lookup"><span data-stu-id="f06ba-245">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="f06ba-246">下面的代码演示了一个自定义转换器，用于实现与 `Stack<T>` 对象之间的来回转换：</span><span class="sxs-lookup"><span data-stu-id="f06ba-246">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="f06ba-247">下面的代码注册转换器：</span><span class="sxs-lookup"><span data-stu-id="f06ba-247">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a><span data-ttu-id="f06ba-248">其他自定义转换器示例</span><span class="sxs-lookup"><span data-stu-id="f06ba-248">Other custom converter samples</span></span>

<span data-ttu-id="f06ba-249">[从 Newtonsoft.Json 迁移到 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) 一文包含自定义转换器的其他示例。</span><span class="sxs-lookup"><span data-stu-id="f06ba-249">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="f06ba-250">`System.Text.Json.Serialization` 源代码中的[单元测试文件夹](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)包含其他自定义转换器示例，例如：</span><span class="sxs-lookup"><span data-stu-id="f06ba-250">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="f06ba-251">[在反序列化时将 null 转换为 0 的 Int32 转换器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="f06ba-251">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="f06ba-252">[在反序列化时允许同时使用字符串和数字值的 Int32 转换器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="f06ba-252">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="f06ba-253">[枚举转换器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="f06ba-253">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="f06ba-254">接受外部数据的 [List\<T> 转换器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="f06ba-254">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="f06ba-255">[处理以逗号分隔的数字列表的 Long[] 转换器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="f06ba-255">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="f06ba-256">如果需要创建修改现有内置转换器行为的转换器，则可以获取[现有转换器的源代码](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)作为自定义的起点。</span><span class="sxs-lookup"><span data-stu-id="f06ba-256">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f06ba-257">其他资源</span><span class="sxs-lookup"><span data-stu-id="f06ba-257">Additional resources</span></span>

* <span data-ttu-id="f06ba-258">[内置转换器的源代码](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="f06ba-258">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="f06ba-259">System.Text.Json 中的 DateTime 和 DateTimeOffset 支持</span><span class="sxs-lookup"><span data-stu-id="f06ba-259">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="f06ba-260">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="f06ba-260">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f06ba-261">如何使用 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f06ba-261">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f06ba-262">如何从 Newtonsoft.Json 迁移</span><span class="sxs-lookup"><span data-stu-id="f06ba-262">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* <span data-ttu-id="f06ba-263">[System.Text.Json API 参考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f06ba-263">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f06ba-264">[System.Text.Json.Serialization API 参考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f06ba-264">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
