---
title: 保存和还原时区
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
ms.openlocfilehash: 8da26988d2e141ac704f0d3756cd8a50602cb3fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281045"
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="9509a-102">保存和还原时区</span><span class="sxs-lookup"><span data-stu-id="9509a-102">Saving and restoring time zones</span></span>

<span data-ttu-id="9509a-103"><xref:System.TimeZoneInfo>类依赖于注册表来检索预定义的时区数据。</span><span class="sxs-lookup"><span data-stu-id="9509a-103">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="9509a-104">但注册表为动态结构。</span><span class="sxs-lookup"><span data-stu-id="9509a-104">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="9509a-105">此外，操作系统使用的时区信息主要用于处理当前年份的时间调整和转换。</span><span class="sxs-lookup"><span data-stu-id="9509a-105">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="9509a-106">对于依赖于准确时区数据的应用程序，这有两个主要含义：</span><span class="sxs-lookup"><span data-stu-id="9509a-106">This has two major implications for applications that rely on accurate time zone data:</span></span>

- <span data-ttu-id="9509a-107">可能不会在注册表中定义应用程序所需的时区，也可能已对其进行了重命名或删除。</span><span class="sxs-lookup"><span data-stu-id="9509a-107">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

- <span data-ttu-id="9509a-108">在注册表中定义的时区可能缺少有关历史时区转换所需的特定调整规则的信息。</span><span class="sxs-lookup"><span data-stu-id="9509a-108">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="9509a-109"><xref:System.TimeZoneInfo>类通过其对时区数据的序列化（保存）和反序列化（还原）支持来解决这些限制。</span><span class="sxs-lookup"><span data-stu-id="9509a-109">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="9509a-110">时区序列化和反序列化</span><span class="sxs-lookup"><span data-stu-id="9509a-110">Time zone serialization and deserialization</span></span>

<span data-ttu-id="9509a-111">通过序列化和反序列化时区数据来保存和还原时区只涉及两个方法调用：</span><span class="sxs-lookup"><span data-stu-id="9509a-111">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

- <span data-ttu-id="9509a-112">可以 <xref:System.TimeZoneInfo> 通过调用对象的方法来序列化对象 <xref:System.TimeZoneInfo.ToSerializedString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9509a-112">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="9509a-113">方法不采用任何参数，并返回包含时区信息的字符串。</span><span class="sxs-lookup"><span data-stu-id="9509a-113">The method takes no parameters and returns a string that contains time zone information.</span></span>

- <span data-ttu-id="9509a-114">您可以通过将 <xref:System.TimeZoneInfo> 字符串传递给 `static` （ `Shared` Visual Basic）方法将对象从序列化字符串反序列化 <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9509a-114">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="9509a-115">序列化和反序列化方案</span><span class="sxs-lookup"><span data-stu-id="9509a-115">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="9509a-116">能够将对象保存（或序列化） <xref:System.TimeZoneInfo> 到字符串，并将其还原（或反序列化）以供以后使用会提高实用工具和类的灵活性 <xref:System.TimeZoneInfo> 。</span><span class="sxs-lookup"><span data-stu-id="9509a-116">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="9509a-117">本部分介绍了序列化和反序列化最有用的一些情况。</span><span class="sxs-lookup"><span data-stu-id="9509a-117">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="9509a-118">序列化和反序列化应用程序中的时区数据</span><span class="sxs-lookup"><span data-stu-id="9509a-118">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="9509a-119">当需要时，可以从字符串还原序列化时区。</span><span class="sxs-lookup"><span data-stu-id="9509a-119">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="9509a-120">如果从注册表检索的时区无法正确转换特定日期范围内的日期和时间，则应用程序可能会执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9509a-120">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="9509a-121">例如，Windows XP 注册表中的时区数据支持单个调整规则，而 Windows Vista 注册表中定义的时区通常提供有关两个调整规则的信息。</span><span class="sxs-lookup"><span data-stu-id="9509a-121">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="9509a-122">这意味着，历史时间转换可能不准确。</span><span class="sxs-lookup"><span data-stu-id="9509a-122">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="9509a-123">时区数据的序列化和反序列化可处理此限制。</span><span class="sxs-lookup"><span data-stu-id="9509a-123">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="9509a-124">在下面的示例中，不带调整规则的自定义 <xref:System.TimeZoneInfo> 类定义为表示从 1883 年到 1917 年（在引入夏时制之前）的美国东部标准时区。</span><span class="sxs-lookup"><span data-stu-id="9509a-124">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="9509a-125">自定义时区在具有全局作用域的变量中序列化。</span><span class="sxs-lookup"><span data-stu-id="9509a-125">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="9509a-126">时区转换方法将 `ConvertUtcTime` 通过协调世界时（UTC）时间传递来转换。</span><span class="sxs-lookup"><span data-stu-id="9509a-126">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="9509a-127">如果日期和时间出现在1917或更早版本中，则从序列化的字符串还原自定义的东部标准时区，并替换从注册表中检索到的时区。</span><span class="sxs-lookup"><span data-stu-id="9509a-127">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="9509a-128">处理时区异常</span><span class="sxs-lookup"><span data-stu-id="9509a-128">Handling time zone exceptions</span></span>

<span data-ttu-id="9509a-129">由于注册表是动态结构，其内容可能会被意外或有意修改。</span><span class="sxs-lookup"><span data-stu-id="9509a-129">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="9509a-130">这意味着应该在注册表中定义的时区以及成功执行应用程序所需的时区可能不存在。</span><span class="sxs-lookup"><span data-stu-id="9509a-130">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="9509a-131">如果不支持时区序列化和反序列化，则只需进行很少的选择，而 <xref:System.TimeZoneNotFoundException> 通过结束应用程序来处理所生成的。</span><span class="sxs-lookup"><span data-stu-id="9509a-131">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="9509a-132">但是，通过使用时区序列化和反序列化，您可以 <xref:System.TimeZoneNotFoundException> 通过从序列化字符串还原所需的时区来处理意外错误，应用程序将继续运行。</span><span class="sxs-lookup"><span data-stu-id="9509a-132">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="9509a-133">下面的示例创建并序列化自定义中部标准时区。</span><span class="sxs-lookup"><span data-stu-id="9509a-133">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="9509a-134">然后，它会尝试从注册表检索中部标准时区。</span><span class="sxs-lookup"><span data-stu-id="9509a-134">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="9509a-135">如果检索操作引发 <xref:System.TimeZoneNotFoundException> 或 <xref:System.InvalidTimeZoneException> ，则异常处理程序将反序列化时区。</span><span class="sxs-lookup"><span data-stu-id="9509a-135">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="9509a-136">存储序列化字符串并在需要时对其进行还原</span><span class="sxs-lookup"><span data-stu-id="9509a-136">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="9509a-137">前面的示例将时区信息存储在字符串变量中，并在需要时对其进行还原。</span><span class="sxs-lookup"><span data-stu-id="9509a-137">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="9509a-138">但是，包含序列化的时区信息的字符串本身可以存储在某个存储介质中，例如外部文件、嵌入在应用程序中的资源文件或注册表。</span><span class="sxs-lookup"><span data-stu-id="9509a-138">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="9509a-139">（请注意，有关自定义时区的信息应该与系统的时区密钥分开存储在注册表中。）</span><span class="sxs-lookup"><span data-stu-id="9509a-139">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="9509a-140">以这种方式存储序列化时区字符串还可以将时区创建例程与应用程序本身隔开。</span><span class="sxs-lookup"><span data-stu-id="9509a-140">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="9509a-141">例如，时区创建例程可执行并创建包含应用程序可使用的历史时区信息的数据文件。</span><span class="sxs-lookup"><span data-stu-id="9509a-141">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="9509a-142">然后，可以在应用程序中安装数据文件，并在应用程序需要时，可以打开该文件并对其一个或多个时区进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="9509a-142">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="9509a-143">有关使用嵌入资源存储序列化的时区数据的示例，请参阅[如何：将时区保存到嵌入的资源](save-time-zones-to-an-embedded-resource.md)和[如何：从嵌入的资源还原时区](restore-time-zones-from-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="9509a-143">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9509a-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9509a-144">See also</span></span>

- [<span data-ttu-id="9509a-145">日期、时间和时区</span><span class="sxs-lookup"><span data-stu-id="9509a-145">Dates, times, and time zones</span></span>](index.md)
