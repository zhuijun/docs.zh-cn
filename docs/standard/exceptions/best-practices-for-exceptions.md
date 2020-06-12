---
title: 异常的最佳做法 - .NET
description: 了解异常的最佳做法，例如使用 try/catch/finally、处理没有异常的常见条件以及使用预定义的 .NET 异常类型。
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 90dda00acd32852b032fc383580c5f34022ec9b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447090"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="e594d-103">异常的最佳做法</span><span class="sxs-lookup"><span data-stu-id="e594d-103">Best practices for exceptions</span></span>

<span data-ttu-id="e594d-104">设计良好的应用处理异常和错误以防止应用崩溃。</span><span class="sxs-lookup"><span data-stu-id="e594d-104">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="e594d-105">本部分介绍了处理和创建异常的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="e594d-105">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="e594d-106">使用 try/catch/finally 块从错误中恢复或释放资源</span><span class="sxs-lookup"><span data-stu-id="e594d-106">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="e594d-107">对可能生成异常的代码使用 `try`/`catch` 块，代码就可以从该异常中恢复。</span><span class="sxs-lookup"><span data-stu-id="e594d-107">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="e594d-108">在 `catch` 块中，始终按从派生程度最高到派生程度最低的顺序对异常排序。</span><span class="sxs-lookup"><span data-stu-id="e594d-108">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="e594d-109">所有异常都派生自 <xref:System.Exception>。</span><span class="sxs-lookup"><span data-stu-id="e594d-109">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="e594d-110">位于处理基本异常类的 catch 子句之后的 catch 子句不处理派生程度较高的异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-110">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="e594d-111">当代码无法从异常中恢复时，请勿捕获该异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-111">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="e594d-112">如有可能，请启用调用堆栈中更上层的方法来进行恢复。</span><span class="sxs-lookup"><span data-stu-id="e594d-112">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="e594d-113">使用 `using` 语句或 `finally` 块清除分配的资源。</span><span class="sxs-lookup"><span data-stu-id="e594d-113">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="e594d-114">当引发了异常时，优先使用 `using` 语句自动清除资源。</span><span class="sxs-lookup"><span data-stu-id="e594d-114">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="e594d-115">使用 `finally` 块清除未实现 <xref:System.IDisposable> 的资源。</span><span class="sxs-lookup"><span data-stu-id="e594d-115">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="e594d-116">即使引发了异常，通常也会执行 `finally` 子句中的代码。</span><span class="sxs-lookup"><span data-stu-id="e594d-116">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="e594d-117">在不引发异常的前提下，处理常见情况</span><span class="sxs-lookup"><span data-stu-id="e594d-117">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="e594d-118">对于易于发生但可能会触发异常的情况，请考虑使用能避免引发异常的方法进行处理。</span><span class="sxs-lookup"><span data-stu-id="e594d-118">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="e594d-119">例如，如果尝试关闭已关闭的连接，则会获得 `InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="e594d-119">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="e594d-120">尝试关闭前，可通过使用 `if` 语句检查连接状态，避免该情况。</span><span class="sxs-lookup"><span data-stu-id="e594d-120">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="e594d-121">如果关闭前未检查连接状态，则可能捕获 `InvalidOperationException` 异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-121">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="e594d-122">选择的方法取决于希望时间发生的频率。</span><span class="sxs-lookup"><span data-stu-id="e594d-122">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="e594d-123">如果此事件未经常发生（也就是说，如果此事件确实为异常并指示错误（如意外的文件尾）），则使用异常处理。</span><span class="sxs-lookup"><span data-stu-id="e594d-123">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="e594d-124">如果使用异常处理，将在正常条件下执行较少代码。</span><span class="sxs-lookup"><span data-stu-id="e594d-124">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="e594d-125">如果事件例行发生，且被视为正常性执行的一部分，请检查代码中是否存在错误情况。</span><span class="sxs-lookup"><span data-stu-id="e594d-125">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="e594d-126">检查常见错误情况时，为了避免异常，执行较少的代码。</span><span class="sxs-lookup"><span data-stu-id="e594d-126">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="e594d-127">设计类，以避免异常</span><span class="sxs-lookup"><span data-stu-id="e594d-127">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="e594d-128">类可提供一些方法或属性来确保避免生成会引发异常的调用。</span><span class="sxs-lookup"><span data-stu-id="e594d-128">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="e594d-129">例如，<xref:System.IO.FileStream> 类提供可帮助确实是否已到达文件末尾的方法。</span><span class="sxs-lookup"><span data-stu-id="e594d-129">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="e594d-130">它可用于避免在读取超过文件末尾时引发的异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-130">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="e594d-131">下方示例显示如何读取文件末尾而不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-131">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="e594d-132">避免异常的另一方法是，对极为常见的错误案例返回 NULL（或默认值），而不是引发异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-132">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="e594d-133">极其常见的错误案例可被视为常规控制流。</span><span class="sxs-lookup"><span data-stu-id="e594d-133">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="e594d-134">通过在这些情况下返回 NULL（或默认值），可最大程度地减小对应用的性能产生的影响。</span><span class="sxs-lookup"><span data-stu-id="e594d-134">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="e594d-135">对于值类型，是否使用 `Nullable<T>` 或默认值作为错误指示符是特定应用需要考虑的内容。</span><span class="sxs-lookup"><span data-stu-id="e594d-135">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="e594d-136">通过使用 `Nullable<Guid>`，`default` 变为 `null` 而非 `Guid.Empty`。</span><span class="sxs-lookup"><span data-stu-id="e594d-136">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="e594d-137">有时，添加 `Nullable<T>` 可更加明确值何时存在或不存在。</span><span class="sxs-lookup"><span data-stu-id="e594d-137">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="e594d-138">在其他时候，添加 `Nullable<T>` 可以创建额外的案例以查看不必要的内容，并且仅用于创建潜在的错误源。</span><span class="sxs-lookup"><span data-stu-id="e594d-138">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="e594d-139">引发异常而不是返回错误代码</span><span class="sxs-lookup"><span data-stu-id="e594d-139">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="e594d-140">异常可确保故障不被忽略，因为调用代码不会检查返回代码。</span><span class="sxs-lookup"><span data-stu-id="e594d-140">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="e594d-141">使用预定义的 .NET 异常类型</span><span class="sxs-lookup"><span data-stu-id="e594d-141">Use the predefined .NET exception types</span></span>

<span data-ttu-id="e594d-142">仅当预定义的异常类不适用时，引入新异常类。</span><span class="sxs-lookup"><span data-stu-id="e594d-142">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="e594d-143">例如：</span><span class="sxs-lookup"><span data-stu-id="e594d-143">For example:</span></span>

- <span data-ttu-id="e594d-144">如果根据对象的当前状态，属性集或方法调用不适当，则会引发 <xref:System.InvalidOperationException> 异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-144">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="e594d-145">如果传送了无效的参数，则引发 <xref:System.ArgumentException> 异常或从 <xref:System.ArgumentException> 派生的一个预定义类。</span><span class="sxs-lookup"><span data-stu-id="e594d-145">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="e594d-146">异常类名称的结尾为 `Exception`</span><span class="sxs-lookup"><span data-stu-id="e594d-146">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="e594d-147">需要自定义异常时，对其正确命名并从 <xref:System.Exception> 类进行派生。</span><span class="sxs-lookup"><span data-stu-id="e594d-147">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="e594d-148">例如：</span><span class="sxs-lookup"><span data-stu-id="e594d-148">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="e594d-149">在自定义异常类中包括三种构造函数</span><span class="sxs-lookup"><span data-stu-id="e594d-149">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="e594d-150">创建自己的异常类时，请至少使用三种公共构造函数：无参数构造函数、采用字符串消息的构造函数以及采用字符串消息和内部异常的构造函数。</span><span class="sxs-lookup"><span data-stu-id="e594d-150">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="e594d-151"><xref:System.Exception.%23ctor>（使用默认值）。</span><span class="sxs-lookup"><span data-stu-id="e594d-151"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="e594d-152"><xref:System.Exception.%23ctor%28System.String%29>，它接受字符串消息。</span><span class="sxs-lookup"><span data-stu-id="e594d-152"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="e594d-153"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>，它接受字符串消息和内部异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-153"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="e594d-154">有关示例，请参见 [如何：创建用户定义的异常](how-to-create-user-defined-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="e594d-154">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="e594d-155">确保代码远程执行时异常数据可用</span><span class="sxs-lookup"><span data-stu-id="e594d-155">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="e594d-156">创建用户定义的异常时，请确保异常的元数据对远程执行的代码可用。</span><span class="sxs-lookup"><span data-stu-id="e594d-156">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="e594d-157">例如，在支持应用域的 .NET 实现中，异常可能会跨应用域抛出。</span><span class="sxs-lookup"><span data-stu-id="e594d-157">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="e594d-158">假设应用域 A 创建应用域 B，后者执行引发异常的代码。</span><span class="sxs-lookup"><span data-stu-id="e594d-158">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="e594d-159">应用域 A 若想正确捕获和处理异常，它必须能够找到包含应用域 B 所引发的异常的程序集。如果应用域 B 在其应用程序基下（但未在应用域 A 的应用程序基下）引发了一个包含在程序集内的异常，那么应用域 A 将无法找到异常，且公共语言运行时将引发 <xref:System.IO.FileNotFoundException> 异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-159">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="e594d-160">为避免此情况，可以两种方式部署包含异常信息的程序集：</span><span class="sxs-lookup"><span data-stu-id="e594d-160">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="e594d-161">将程序集放在两个应用域共享的公共应用程序基中。</span><span class="sxs-lookup"><span data-stu-id="e594d-161">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="e594d-162">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e594d-162">\- or -</span></span>

- <span data-ttu-id="e594d-163">如果两个应用域不共享一个公共应用程序基，则用强名称为包含异常信息的程序集签名并将其部署到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="e594d-163">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="e594d-164">使用语法正确的错误消息</span><span class="sxs-lookup"><span data-stu-id="e594d-164">Use grammatically correct error messages</span></span>

<span data-ttu-id="e594d-165">编写清晰的句子，包括结束标点。</span><span class="sxs-lookup"><span data-stu-id="e594d-165">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="e594d-166">分配给 <xref:System.Exception.Message?displayProperty=nameWithType> 属性的字符串中的每个句子应以句点结尾。</span><span class="sxs-lookup"><span data-stu-id="e594d-166">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="e594d-167">例如，“日志表已溢出”。</span><span class="sxs-lookup"><span data-stu-id="e594d-167">For example, "The log table has overflowed."</span></span> <span data-ttu-id="e594d-168">是一个正确的消息字符串。</span><span class="sxs-lookup"><span data-stu-id="e594d-168">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="e594d-169">在每个异常中都包含一个本地化字符串消息</span><span class="sxs-lookup"><span data-stu-id="e594d-169">Include a localized string message in every exception</span></span>

<span data-ttu-id="e594d-170">用户看到的错误消息派生自引发的异常的 <xref:System.Exception.Message?displayProperty=nameWithType> 属性，而不是派生自异常类的名称。</span><span class="sxs-lookup"><span data-stu-id="e594d-170">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="e594d-171">通常将值赋给 <xref:System.Exception.Message?displayProperty=nameWithType> 属性，方法是将消息字符串传递到[异常构造函数](xref:System.Exception.%23ctor%2A)的 `message` 参数。</span><span class="sxs-lookup"><span data-stu-id="e594d-171">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="e594d-172">对于本地化应用程序，应为应用程序可能引发的每个异常提供本地化消息字符串。</span><span class="sxs-lookup"><span data-stu-id="e594d-172">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="e594d-173">资源文件用于提供本地化错误消息。</span><span class="sxs-lookup"><span data-stu-id="e594d-173">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="e594d-174">有关本地化应用程序和检索本地化字符串的信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="e594d-174">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="e594d-175">如何：使用本地化的异常消息创建用户定义的异常</span><span class="sxs-lookup"><span data-stu-id="e594d-175">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="e594d-176">桌面应用中的资源</span><span class="sxs-lookup"><span data-stu-id="e594d-176">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="e594d-177">在自定义异常中，按需提供其他属性</span><span class="sxs-lookup"><span data-stu-id="e594d-177">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="e594d-178">仅当存在附加信息有用的编程方案时，才在异常中提供附加属性（不包括自定义消息字符串）。</span><span class="sxs-lookup"><span data-stu-id="e594d-178">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="e594d-179">例如，<xref:System.IO.FileNotFoundException> 提供 <xref:System.IO.FileNotFoundException.FileName> 属性。</span><span class="sxs-lookup"><span data-stu-id="e594d-179">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="e594d-180">放置引发语句，使得堆栈跟踪有所帮助</span><span class="sxs-lookup"><span data-stu-id="e594d-180">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="e594d-181">堆栈跟踪从引发异常的语句开始，到捕获异常的 `catch` 语句结束。</span><span class="sxs-lookup"><span data-stu-id="e594d-181">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="e594d-182">使用异常生成器方法</span><span class="sxs-lookup"><span data-stu-id="e594d-182">Use exception builder methods</span></span>

<span data-ttu-id="e594d-183">类从其实现中的不同位置引发同一异常是常见的情况。</span><span class="sxs-lookup"><span data-stu-id="e594d-183">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="e594d-184">为避免过多的代码，应使用帮助器方法创建异常并将其返回。</span><span class="sxs-lookup"><span data-stu-id="e594d-184">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="e594d-185">例如：</span><span class="sxs-lookup"><span data-stu-id="e594d-185">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="e594d-186">在某些情况下，更适合使用异常的构造函数生成异常。</span><span class="sxs-lookup"><span data-stu-id="e594d-186">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="e594d-187">例如，<xref:System.ArgumentException> 等全局异常类。</span><span class="sxs-lookup"><span data-stu-id="e594d-187">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="e594d-188">因发生异常而未完成方法时还原状态</span><span class="sxs-lookup"><span data-stu-id="e594d-188">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="e594d-189">当异常从方法引发时，调用方应能够假定没有副作用。</span><span class="sxs-lookup"><span data-stu-id="e594d-189">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="e594d-190">例如，如果你的代码可以通过从一个帐户取钱并存入另一个帐户来转移资金，而在存款时引发了异常，你不希望取款仍然有效。</span><span class="sxs-lookup"><span data-stu-id="e594d-190">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

<span data-ttu-id="e594d-191">上面的方法不会直接引发任何异常，但必须以防御方式进行编写，以便在存款操作失败时撤销取款。</span><span class="sxs-lookup"><span data-stu-id="e594d-191">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="e594d-192">解决这一情况的一种方法是，捕获由存款交易引发的异常，然后回滚取款。</span><span class="sxs-lookup"><span data-stu-id="e594d-192">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

<span data-ttu-id="e594d-193">此示例介绍如何使用 `throw` 重新引发原始异常，让调用方更轻松地发现问题的真正原因，而无需检查 <xref:System.Exception.InnerException> 属性。</span><span class="sxs-lookup"><span data-stu-id="e594d-193">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="e594d-194">另一种方法是，引发一个新的异常并将原始异常包括在其中作为内部异常：</span><span class="sxs-lookup"><span data-stu-id="e594d-194">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a><span data-ttu-id="e594d-195">请参阅</span><span class="sxs-lookup"><span data-stu-id="e594d-195">See also</span></span>

- [<span data-ttu-id="e594d-196">异常</span><span class="sxs-lookup"><span data-stu-id="e594d-196">Exceptions</span></span>](index.md)
