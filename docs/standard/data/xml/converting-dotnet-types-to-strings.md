---
title: 将 .NET Framework 类型转换为字符串
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287813"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="0e9b8-102">将 .NET Framework 类型转换为字符串</span><span class="sxs-lookup"><span data-stu-id="0e9b8-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="0e9b8-103">若要将 .NET Framework 类型转换为字符串，请使用 ToString  方法。</span><span class="sxs-lookup"><span data-stu-id="0e9b8-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="0e9b8-104">ToString  方法返回传入的类型的字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="0e9b8-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="0e9b8-105">下表列出了以映射到 XML 架构 (XSD) 规范的格式返回字符串的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="0e9b8-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="0e9b8-106">.NET Framework 类型</span><span class="sxs-lookup"><span data-stu-id="0e9b8-106">.NET Framework type</span></span>|<span data-ttu-id="0e9b8-107">返回的字符串类型</span><span class="sxs-lookup"><span data-stu-id="0e9b8-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="0e9b8-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="0e9b8-108">Boolean</span></span>|<span data-ttu-id="0e9b8-109">“true”、“false”</span><span class="sxs-lookup"><span data-stu-id="0e9b8-109">"true", "false"</span></span>|  
|<span data-ttu-id="0e9b8-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="0e9b8-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="0e9b8-111">“INF”</span><span class="sxs-lookup"><span data-stu-id="0e9b8-111">"INF"</span></span>|  
|<span data-ttu-id="0e9b8-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="0e9b8-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="0e9b8-113">“-INF”</span><span class="sxs-lookup"><span data-stu-id="0e9b8-113">"-INF"</span></span>|  
|<span data-ttu-id="0e9b8-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="0e9b8-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="0e9b8-115">“INF”</span><span class="sxs-lookup"><span data-stu-id="0e9b8-115">"INF"</span></span>|  
|<span data-ttu-id="0e9b8-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="0e9b8-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="0e9b8-117">“-INF”</span><span class="sxs-lookup"><span data-stu-id="0e9b8-117">"-INF"</span></span>|  
|<span data-ttu-id="0e9b8-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="0e9b8-118">DateTime</span></span>|<span data-ttu-id="0e9b8-119">格式为 yyyy-MM-ddTHH:mm:sszzzzzz 及其子集。</span><span class="sxs-lookup"><span data-stu-id="0e9b8-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="0e9b8-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="0e9b8-120">Timespan</span></span>|<span data-ttu-id="0e9b8-121">格式是 PnYnMnTnHnMnS，例如，`P2Y10M15DT10H30M20S` 表示长 2 年 10 个月 15 天 10 小时 30 分钟 20 秒的持续时间。</span><span class="sxs-lookup"><span data-stu-id="0e9b8-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e9b8-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="0e9b8-122">See also</span></span>

- [<span data-ttu-id="0e9b8-123">XML 数据类型转换</span><span class="sxs-lookup"><span data-stu-id="0e9b8-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="0e9b8-124">将字符串转换为 .NET Framework 数据类型</span><span class="sxs-lookup"><span data-stu-id="0e9b8-124">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
