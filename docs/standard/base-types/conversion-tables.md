---
title: .NET 中的类型转换表
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: bb696c65078a5dae0b81a48bffc786d2257496c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290560"
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="b4b87-102">.NET 中的类型转换表</span><span class="sxs-lookup"><span data-stu-id="b4b87-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="b4b87-103">当一种类型的值转换为大小相等或更大的另一类型时，将发生扩大转换。</span><span class="sxs-lookup"><span data-stu-id="b4b87-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="b4b87-104">当一种类型的值转换为较小的另一种类型时，将发生收缩转换。</span><span class="sxs-lookup"><span data-stu-id="b4b87-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="b4b87-105">本主题中的表格解释了这两种转换类型的行为。</span><span class="sxs-lookup"><span data-stu-id="b4b87-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="b4b87-106">扩大转换</span><span class="sxs-lookup"><span data-stu-id="b4b87-106">Widening Conversions</span></span>  
 <span data-ttu-id="b4b87-107">下表列出了执行不会导致信息丢失的扩大转换。</span><span class="sxs-lookup"><span data-stu-id="b4b87-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="b4b87-108">类型</span><span class="sxs-lookup"><span data-stu-id="b4b87-108">Type</span></span>|<span data-ttu-id="b4b87-109">可在不丢失数据的情况下转换为</span><span class="sxs-lookup"><span data-stu-id="b4b87-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="b4b87-110"><xref:System.UInt16>、<xref:System.Int16>、<xref:System.UInt32>、<xref:System.Int32>、<xref:System.UInt64>、<xref:System.Int64>、<xref:System.Single>、<xref:System.Double>、<xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="b4b87-111"><xref:System.Int16>、 <xref:System.Int32>、 <xref:System.Int64>、 <xref:System.Single>、 <xref:System.Double>、 <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="b4b87-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="b4b87-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="b4b87-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="b4b87-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="b4b87-116"><xref:System.Int64>、<xref:System.UInt64>、<xref:System.Double>、<xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="b4b87-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="b4b87-117">一些目标为 <xref:System.Single> 或 <xref:System.Double> 的扩大转换可能会导致精度丢失。</span><span class="sxs-lookup"><span data-stu-id="b4b87-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="b4b87-118">下面的表格描述了有时会导致信息丢失的扩大转换。</span><span class="sxs-lookup"><span data-stu-id="b4b87-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="b4b87-119">类型</span><span class="sxs-lookup"><span data-stu-id="b4b87-119">Type</span></span>|<span data-ttu-id="b4b87-120">可转换为</span><span class="sxs-lookup"><span data-stu-id="b4b87-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="b4b87-121"><xref:System.Single>， <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b4b87-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b4b87-122"><xref:System.Single>， <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b4b87-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b4b87-123"><xref:System.Single>， <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="b4b87-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="b4b87-124">收缩转换</span><span class="sxs-lookup"><span data-stu-id="b4b87-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="b4b87-125">目标为 <xref:System.Single> 或 <xref:System.Double> 的收缩转换可能会导致信息丢失。</span><span class="sxs-lookup"><span data-stu-id="b4b87-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="b4b87-126">如果目标类型无法正确表达源类型的大小，则结果类型将设置为常数 `PositiveInfinity` 或 `NegativeInfinity`。</span><span class="sxs-lookup"><span data-stu-id="b4b87-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="b4b87-127">`PositiveInfinity` 是正数除以 0 的结果，也在 <xref:System.Single> 或 <xref:System.Double> 的值大于 `MaxValue` 字段的值时返回。</span><span class="sxs-lookup"><span data-stu-id="b4b87-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="b4b87-128">`NegativeInfinity` 是负数除以 0 的结果，也在 <xref:System.Single> 或 <xref:System.Double> 的值小于 `MinValue` 字段的值时返回。</span><span class="sxs-lookup"><span data-stu-id="b4b87-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="b4b87-129">从 <xref:System.Double> 转换到 <xref:System.Single> 可能会导致 `PositiveInfinity` 或 `NegativeInfinity`。</span><span class="sxs-lookup"><span data-stu-id="b4b87-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="b4b87-130">收缩转换还可能导致其他数据类型的信息丢失。</span><span class="sxs-lookup"><span data-stu-id="b4b87-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="b4b87-131">不过，如果要转换的类型值不在目标类型的 `MaxValue` 和 `MinValue` 字段指定的范围内，就会抛出 <xref:System.OverflowException>，并且运行时会检查转换，以确保目标类型的值不超出它的 `MaxValue` 或 `MinValue`。</span><span class="sxs-lookup"><span data-stu-id="b4b87-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="b4b87-132">始终以这种方式检查使用 <xref:System.Convert?displayProperty=nameWithType> 类执行的转换。</span><span class="sxs-lookup"><span data-stu-id="b4b87-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="b4b87-133">下表列出了使用 <xref:System.Convert?displayProperty=nameWithType> 抛出 <xref:System.OverflowException> 的转换，或要转换类型的值不在生成类型的定义范围内的任何已检查转换。</span><span class="sxs-lookup"><span data-stu-id="b4b87-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="b4b87-134">类型</span><span class="sxs-lookup"><span data-stu-id="b4b87-134">Type</span></span>|<span data-ttu-id="b4b87-135">可转换为</span><span class="sxs-lookup"><span data-stu-id="b4b87-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="b4b87-136"><xref:System.Byte>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b4b87-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="b4b87-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="b4b87-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="b4b87-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="b4b87-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="b4b87-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="b4b87-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="b4b87-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="b4b87-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="b4b87-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b4b87-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b4b87-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="b4b87-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b4b87-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b4b87-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="b4b87-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b4b87-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="b4b87-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="b4b87-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4b87-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4b87-146">See also</span></span>

- <xref:System.Convert?displayProperty=nameWithType>
- [<span data-ttu-id="b4b87-147">.NET 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="b4b87-147">Type Conversion in .NET</span></span>](type-conversion.md)
