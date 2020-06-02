---
title: 使用标准异常类型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: b8e05f22a66fabeab28cc83a074471df29aae218
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291352"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="a2221-102">使用标准异常类型</span><span class="sxs-lookup"><span data-stu-id="a2221-102">Using Standard Exception Types</span></span>
<span data-ttu-id="a2221-103">本部分介绍框架提供的标准异常及其用法的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a2221-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="a2221-104">列表并不完整。</span><span class="sxs-lookup"><span data-stu-id="a2221-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="a2221-105">请参阅 .NET Framework 参考文档，以了解其他框架异常类型的用法。</span><span class="sxs-lookup"><span data-stu-id="a2221-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="a2221-106">Exception 和 SystemException</span><span class="sxs-lookup"><span data-stu-id="a2221-106">Exception and SystemException</span></span>
 <span data-ttu-id="a2221-107">❌不要引发 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a2221-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="a2221-108">❌不要捕获 `System.Exception` `System.SystemException` 框架代码中的或，除非你打算重新引发。</span><span class="sxs-lookup"><span data-stu-id="a2221-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="a2221-109">❌避免捕获 `System.Exception` 或 `System.SystemException` （顶级异常处理程序除外）。</span><span class="sxs-lookup"><span data-stu-id="a2221-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="a2221-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="a2221-110">ApplicationException</span></span>
 <span data-ttu-id="a2221-111">❌不要引发或派生自 <xref:System.ApplicationException> 。</span><span class="sxs-lookup"><span data-stu-id="a2221-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="a2221-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="a2221-112">InvalidOperationException</span></span>
 <span data-ttu-id="a2221-113"><xref:System.InvalidOperationException>如果对象处于不适当的状态，✔️会引发。</span><span class="sxs-lookup"><span data-stu-id="a2221-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="a2221-114">ArgumentException、System.argumentnullexception 和 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="a2221-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="a2221-115"><xref:System.ArgumentException>如果向成员传递了错误的参数，✔️将引发或其子类型之一。</span><span class="sxs-lookup"><span data-stu-id="a2221-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="a2221-116">如果适用，更喜欢派生程度最高的异常类型。</span><span class="sxs-lookup"><span data-stu-id="a2221-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="a2221-117">✔️ `ParamName` 在引发的子类之一时设置属性 `ArgumentException` 。</span><span class="sxs-lookup"><span data-stu-id="a2221-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="a2221-118">此属性表示导致引发异常的参数的名称。</span><span class="sxs-lookup"><span data-stu-id="a2221-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="a2221-119">请注意，可以使用构造函数重载之一来设置属性。</span><span class="sxs-lookup"><span data-stu-id="a2221-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="a2221-120">✔️用于 `value` 属性 setter 的隐式值参数的名称。</span><span class="sxs-lookup"><span data-stu-id="a2221-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="a2221-121">NullReferenceException、IndexOutOfRangeException 和 AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="a2221-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="a2221-122">❌不要允许可公开调用的 Api 显式或隐式引发 <xref:System.NullReferenceException> 、 <xref:System.AccessViolationException> 或 <xref:System.IndexOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="a2221-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="a2221-123">这些异常由执行引擎保留并引发，在大多数情况下表示 bug。</span><span class="sxs-lookup"><span data-stu-id="a2221-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="a2221-124">执行参数检查以避免引发这些异常。</span><span class="sxs-lookup"><span data-stu-id="a2221-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="a2221-125">引发这些异常会公开方法的实现详细信息，这些详细信息可能会随时间变化。</span><span class="sxs-lookup"><span data-stu-id="a2221-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="a2221-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="a2221-126">StackOverflowException</span></span>
 <span data-ttu-id="a2221-127">❌不要显式引发 <xref:System.StackOverflowException> 。</span><span class="sxs-lookup"><span data-stu-id="a2221-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="a2221-128">异常只应由 CLR 显式引发。</span><span class="sxs-lookup"><span data-stu-id="a2221-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="a2221-129">❌请勿捕获 `StackOverflowException` 。</span><span class="sxs-lookup"><span data-stu-id="a2221-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="a2221-130">几乎无法编写在存在任意堆栈溢出时保持一致的托管代码。</span><span class="sxs-lookup"><span data-stu-id="a2221-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="a2221-131">CLR 的非托管部分保持一致，方法是使用探测将堆栈溢出移到明确定义的位置，而不是通过从任意堆栈溢出中进行回退。</span><span class="sxs-lookup"><span data-stu-id="a2221-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="a2221-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="a2221-132">OutOfMemoryException</span></span>
 <span data-ttu-id="a2221-133">❌不要显式引发 <xref:System.OutOfMemoryException> 。</span><span class="sxs-lookup"><span data-stu-id="a2221-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="a2221-134">此异常仅由 CLR 基础结构引发。</span><span class="sxs-lookup"><span data-stu-id="a2221-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="a2221-135">ComException、SEHException 和 ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="a2221-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="a2221-136">❌不要显式引发 <xref:System.Runtime.InteropServices.COMException> 、 <xref:System.ExecutionEngineException> 和 <xref:System.Runtime.InteropServices.SEHException> 。</span><span class="sxs-lookup"><span data-stu-id="a2221-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="a2221-137">这些异常仅由 CLR 基础结构引发。</span><span class="sxs-lookup"><span data-stu-id="a2221-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="a2221-138">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="a2221-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a2221-139">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="a2221-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a2221-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2221-140">See also</span></span>

- [<span data-ttu-id="a2221-141">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="a2221-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a2221-142">异常设计准则</span><span class="sxs-lookup"><span data-stu-id="a2221-142">Design Guidelines for Exceptions</span></span>](exceptions.md)
