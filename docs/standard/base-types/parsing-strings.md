---
title: 分析 .NET 中的字符串
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277409"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="11507-102">分析 .NET 中的字符串</span><span class="sxs-lookup"><span data-stu-id="11507-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="11507-103">分析操作将表示某种 .NET 基类型的字符串转换为该基类型。</span><span class="sxs-lookup"><span data-stu-id="11507-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="11507-104">例如，分析操作用于将字符串转换为浮点数字或日期和时间值。</span><span class="sxs-lookup"><span data-stu-id="11507-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="11507-105">最常用于执行分析操作的方法是 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="11507-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="11507-106">因为分析是格式设置（涉及将基类型转换为其字符串表示形式）的反向操作，所以有许多相同规则和约定适用。</span><span class="sxs-lookup"><span data-stu-id="11507-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="11507-107">就像格式设置使用对象来实现 <xref:System.IFormatProvider> 接口以提供区域性敏感型格式设置信息一样，分析也使用对象来实现 <xref:System.IFormatProvider> 接口，以确定如何解释字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="11507-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="11507-108">有关详细信息，请参阅[类型格式设置](formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="11507-108">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11507-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="11507-109">In This Section</span></span>  
 [<span data-ttu-id="11507-110">分析数值字符串</span><span class="sxs-lookup"><span data-stu-id="11507-110">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="11507-111">介绍了如何将字符串转换为 .NET 数字类型。</span><span class="sxs-lookup"><span data-stu-id="11507-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="11507-112">分析日期和时间字符串</span><span class="sxs-lookup"><span data-stu-id="11507-112">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="11507-113">介绍了如何将字符串转换为 .NET DateTime  类型。</span><span class="sxs-lookup"><span data-stu-id="11507-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="11507-114">分析其他字符串</span><span class="sxs-lookup"><span data-stu-id="11507-114">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="11507-115">介绍了如何将字符串转换为 Char  、Boolean  和 Enum  类型。</span><span class="sxs-lookup"><span data-stu-id="11507-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11507-116">相关章节</span><span class="sxs-lookup"><span data-stu-id="11507-116">Related Sections</span></span>  
 [<span data-ttu-id="11507-117">格式设置类型</span><span class="sxs-lookup"><span data-stu-id="11507-117">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="11507-118">介绍了基本格式设置概念，如格式说明符和格式提供程序。</span><span class="sxs-lookup"><span data-stu-id="11507-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="11507-119">.NET 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="11507-119">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="11507-120">介绍了如何转换类型。</span><span class="sxs-lookup"><span data-stu-id="11507-120">Describes how to convert types.</span></span>
