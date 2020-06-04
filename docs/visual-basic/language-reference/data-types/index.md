---
title: 数据类型摘要
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 5eb52ef937a677c0b7498d058b5a39a375351ddc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415617"
---
# <a name="data-type-summary-visual-basic"></a><span data-ttu-id="38a28-102">数据类型摘要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38a28-102">Data Type Summary (Visual Basic)</span></span>

<span data-ttu-id="38a28-103">下表显示了 Visual Basic 的数据类型、其支持的公共语言运行时类型、其名义存储分配及其值范围。</span><span class="sxs-lookup"><span data-stu-id="38a28-103">The following table shows the Visual Basic data types, their supporting common language runtime types, their nominal storage allocation, and their value ranges.</span></span>  
  
|<span data-ttu-id="38a28-104">Visual Basic 类型</span><span class="sxs-lookup"><span data-stu-id="38a28-104">Visual Basic type</span></span>|<span data-ttu-id="38a28-105">公共语言运行时类型结构</span><span class="sxs-lookup"><span data-stu-id="38a28-105">Common language runtime type structure</span></span>|<span data-ttu-id="38a28-106">标称存储分配</span><span class="sxs-lookup"><span data-stu-id="38a28-106">Nominal storage allocation</span></span>|<span data-ttu-id="38a28-107">取值范围</span><span class="sxs-lookup"><span data-stu-id="38a28-107">Value range</span></span>|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[<span data-ttu-id="38a28-108">布尔值</span><span class="sxs-lookup"><span data-stu-id="38a28-108">Boolean</span></span>](boolean-data-type.md)|<xref:System.Boolean>|<span data-ttu-id="38a28-109">依赖于实现平台</span><span class="sxs-lookup"><span data-stu-id="38a28-109">Depends on implementing platform</span></span>|<span data-ttu-id="38a28-110">`True` 或 `False`</span><span class="sxs-lookup"><span data-stu-id="38a28-110">`True` or `False`</span></span>|  
|[<span data-ttu-id="38a28-111">Byte</span><span class="sxs-lookup"><span data-stu-id="38a28-111">Byte</span></span>](byte-data-type.md)|<xref:System.Byte>|<span data-ttu-id="38a28-112">1 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-112">1 byte</span></span>|<span data-ttu-id="38a28-113">0到255（无符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-113">0 through 255 (unsigned)</span></span>|  
|<span data-ttu-id="38a28-114">[Char](char-data-type.md) （单个字符）</span><span class="sxs-lookup"><span data-stu-id="38a28-114">[Char](char-data-type.md) (single character)</span></span>|<xref:System.Char>|<span data-ttu-id="38a28-115">2 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-115">2 bytes</span></span>|<span data-ttu-id="38a28-116">0到65535（无符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-116">0 through 65535 (unsigned)</span></span>|  
|[<span data-ttu-id="38a28-117">Date</span><span class="sxs-lookup"><span data-stu-id="38a28-117">Date</span></span>](date-data-type.md)|<xref:System.DateTime>|<span data-ttu-id="38a28-118">8 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-118">8 bytes</span></span>|<span data-ttu-id="38a28-119">0:00:00 年1月1日至12月31日下午11:59:59，（午夜）9999</span><span class="sxs-lookup"><span data-stu-id="38a28-119">0:00:00 (midnight) on January 1, 0001 through 11:59:59 PM on December 31, 9999</span></span>|  
|[<span data-ttu-id="38a28-120">小数</span><span class="sxs-lookup"><span data-stu-id="38a28-120">Decimal</span></span>](decimal-data-type.md)|<xref:System.Decimal>|<span data-ttu-id="38a28-121">16 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-121">16 bytes</span></span>|<span data-ttu-id="38a28-122">0到 +/-79228162514264337593543950335 （+/-7.9...E + 28） <sup>†</sup> ，无小数点;0到 +/-7.9228162514264337593543950335，小数点右侧有28个位置;</span><span class="sxs-lookup"><span data-stu-id="38a28-122">0 through +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9...E+28) <sup>†</sup> with no decimal point; 0 through +/-7.9228162514264337593543950335 with 28 places to the right of the decimal;</span></span><br /><br /> <span data-ttu-id="38a28-123">最小非零数字为 +/-0.0000000000000000000000000001 （+/-1E-28） <sup>†</sup></span><span class="sxs-lookup"><span data-stu-id="38a28-123">smallest nonzero number is +/-0.0000000000000000000000000001 (+/-1E-28) <sup>†</sup></span></span>|  
|<span data-ttu-id="38a28-124">[双](double-data-type.md)精度（双精度浮点）</span><span class="sxs-lookup"><span data-stu-id="38a28-124">[Double](double-data-type.md) (double-precision floating-point)</span></span>|<xref:System.Double>|<span data-ttu-id="38a28-125">8 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-125">8 bytes</span></span>|<span data-ttu-id="38a28-126">-1.79769313486231570 e + 308 到-4.94065645841246544 E-324 <sup>†</sup>表示负值;</span><span class="sxs-lookup"><span data-stu-id="38a28-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 <sup>†</sup> for negative values;</span></span><br /><br /> <span data-ttu-id="38a28-127">4.94065645841246544 e-324 到 1.79769313486231570 E + 308 <sup>†</sup>用于正值</span><span class="sxs-lookup"><span data-stu-id="38a28-127">4.94065645841246544E-324 through 1.79769313486231570E+308 <sup>†</sup> for positive values</span></span>|  
|[<span data-ttu-id="38a28-128">整数</span><span class="sxs-lookup"><span data-stu-id="38a28-128">Integer</span></span>](integer-data-type.md)|<xref:System.Int32>|<span data-ttu-id="38a28-129">4 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-129">4 bytes</span></span>|<span data-ttu-id="38a28-130">-2147483648 到2147483647（有符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-130">-2,147,483,648 through 2,147,483,647 (signed)</span></span>|  
|<span data-ttu-id="38a28-131">[Long](long-data-type.md) （长整型）</span><span class="sxs-lookup"><span data-stu-id="38a28-131">[Long](long-data-type.md) (long integer)</span></span>|<xref:System.Int64>|<span data-ttu-id="38a28-132">8 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-132">8 bytes</span></span>|<span data-ttu-id="38a28-133">-9223372036854775808 到9223372036854775807（9.2. E + 18 <sup>†</sup>）（有符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-133">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18 <sup>†</sup>) (signed)</span></span>|  
|[<span data-ttu-id="38a28-134">对象</span><span class="sxs-lookup"><span data-stu-id="38a28-134">Object</span></span>](object-data-type.md)|<span data-ttu-id="38a28-135"><xref:System.Object>班级</span><span class="sxs-lookup"><span data-stu-id="38a28-135"><xref:System.Object> (class)</span></span>|<span data-ttu-id="38a28-136">32位平台上的4个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-136">4 bytes on 32-bit platform</span></span><br /><br /> <span data-ttu-id="38a28-137">64位平台上的8个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-137">8 bytes on 64-bit platform</span></span>|<span data-ttu-id="38a28-138">任何类型都可以存储在类型的变量中`Object`</span><span class="sxs-lookup"><span data-stu-id="38a28-138">Any type can be stored in a variable of type `Object`</span></span>|  
|[<span data-ttu-id="38a28-139">SByte</span><span class="sxs-lookup"><span data-stu-id="38a28-139">SByte</span></span>](sbyte-data-type.md)|<xref:System.SByte>|<span data-ttu-id="38a28-140">1 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-140">1 byte</span></span>|<span data-ttu-id="38a28-141">-128 到127（有符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-141">-128 through 127 (signed)</span></span>|  
|<span data-ttu-id="38a28-142">[Short](short-data-type.md) （短整型）</span><span class="sxs-lookup"><span data-stu-id="38a28-142">[Short](short-data-type.md) (short integer)</span></span>|<xref:System.Int16>|<span data-ttu-id="38a28-143">2 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-143">2 bytes</span></span>|<span data-ttu-id="38a28-144">-32768 到32767（有符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-144">-32,768 through 32,767 (signed)</span></span>|  
|<span data-ttu-id="38a28-145">[单](single-data-type.md)精度（单精度浮点）</span><span class="sxs-lookup"><span data-stu-id="38a28-145">[Single](single-data-type.md) (single-precision floating-point)</span></span>|<xref:System.Single>|<span data-ttu-id="38a28-146">4 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-146">4 bytes</span></span>|<span data-ttu-id="38a28-147">-3.4028235 e + 38 到-1.401298 E-45 <sup>†</sup>表示负值;</span><span class="sxs-lookup"><span data-stu-id="38a28-147">-3.4028235E+38 through -1.401298E-45 <sup>†</sup> for negative values;</span></span><br /><br /> <span data-ttu-id="38a28-148">1.401298 e-45 到 3.4028235 E + 38 <sup>†</sup>用于正值</span><span class="sxs-lookup"><span data-stu-id="38a28-148">1.401298E-45 through 3.4028235E+38 <sup>†</sup> for positive values</span></span>|  
|<span data-ttu-id="38a28-149">[字符串](string-data-type.md)（可变长度）</span><span class="sxs-lookup"><span data-stu-id="38a28-149">[String](string-data-type.md) (variable-length)</span></span>|<span data-ttu-id="38a28-150"><xref:System.String>班级</span><span class="sxs-lookup"><span data-stu-id="38a28-150"><xref:System.String> (class)</span></span>|<span data-ttu-id="38a28-151">依赖于实现平台</span><span class="sxs-lookup"><span data-stu-id="38a28-151">Depends on implementing platform</span></span>|<span data-ttu-id="38a28-152">0到约 2000000000 Unicode 字符</span><span class="sxs-lookup"><span data-stu-id="38a28-152">0 to approximately 2 billion Unicode characters</span></span>|  
|[<span data-ttu-id="38a28-153">UInteger</span><span class="sxs-lookup"><span data-stu-id="38a28-153">UInteger</span></span>](uinteger-data-type.md)|<xref:System.UInt32>|<span data-ttu-id="38a28-154">4 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-154">4 bytes</span></span>|<span data-ttu-id="38a28-155">0到4294967295（无符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-155">0 through 4,294,967,295 (unsigned)</span></span>|  
|[<span data-ttu-id="38a28-156">ULong</span><span class="sxs-lookup"><span data-stu-id="38a28-156">ULong</span></span>](ulong-data-type.md)|<xref:System.UInt64>|<span data-ttu-id="38a28-157">8 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-157">8 bytes</span></span>|<span data-ttu-id="38a28-158">0到18446744073709551615（1.8 ... E + 19 <sup>†</sup>）（无符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-158">0 through 18,446,744,073,709,551,615 (1.8...E+19 <sup>†</sup>) (unsigned)</span></span>|  
|<span data-ttu-id="38a28-159">[用户定义的](user-defined-data-type.md)（结构）</span><span class="sxs-lookup"><span data-stu-id="38a28-159">[User-Defined](user-defined-data-type.md) (structure)</span></span>|<span data-ttu-id="38a28-160">（继承自 <xref:System.ValueType> ）</span><span class="sxs-lookup"><span data-stu-id="38a28-160">(inherits from <xref:System.ValueType>)</span></span>|<span data-ttu-id="38a28-161">依赖于实现平台</span><span class="sxs-lookup"><span data-stu-id="38a28-161">Depends on implementing platform</span></span>|<span data-ttu-id="38a28-162">结构的每个成员都有一个由其数据类型确定的范围，并与其他成员的范围无关</span><span class="sxs-lookup"><span data-stu-id="38a28-162">Each member of the structure has a range determined by its data type and independent of the ranges of the other members</span></span>|  
|[<span data-ttu-id="38a28-163">UShort</span><span class="sxs-lookup"><span data-stu-id="38a28-163">UShort</span></span>](ushort-data-type.md)|<xref:System.UInt16>|<span data-ttu-id="38a28-164">2 个字节</span><span class="sxs-lookup"><span data-stu-id="38a28-164">2 bytes</span></span>|<span data-ttu-id="38a28-165">0到65535（无符号）</span><span class="sxs-lookup"><span data-stu-id="38a28-165">0 through 65,535 (unsigned)</span></span>|  
  
 <span data-ttu-id="38a28-166"><sup>†</sup>使用*科学记数法*时，"E" 指的是10的幂。</span><span class="sxs-lookup"><span data-stu-id="38a28-166"><sup>†</sup> In *scientific notation*, "E" refers to a power of 10.</span></span> <span data-ttu-id="38a28-167">因此，3.56 E + 2 表示 3.56 x 10<sup>2</sup>或356，3.56 e-2 表示 3.56/10<sup>2</sup>或0.0356。</span><span class="sxs-lookup"><span data-stu-id="38a28-167">So 3.56E+2 signifies 3.56 x 10<sup>2</sup> or 356, and 3.56E-2 signifies 3.56 / 10<sup>2</sup> or 0.0356.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38a28-168">对于包含文本的字符串，请使用 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函数从一种文本格式转换为另一种文本格式。</span><span class="sxs-lookup"><span data-stu-id="38a28-168">For strings containing text, use the <xref:Microsoft.VisualBasic.Strings.StrConv%2A> function to convert from one text format to another.</span></span>  
  
 <span data-ttu-id="38a28-169">除了在声明语句中指定数据类型之外，还可以使用类型字符强制某些编程元素的数据类型。</span><span class="sxs-lookup"><span data-stu-id="38a28-169">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements by using a type character.</span></span> <span data-ttu-id="38a28-170">请参阅[类型字符](../../programming-guide/language-features/data-types/type-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="38a28-170">See [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="memory-consumption"></a><span data-ttu-id="38a28-171">内存消耗</span><span class="sxs-lookup"><span data-stu-id="38a28-171">Memory Consumption</span></span>  

 <span data-ttu-id="38a28-172">在声明基本数据类型时，不安全地假定其内存消耗与其名义存储分配相同。</span><span class="sxs-lookup"><span data-stu-id="38a28-172">When you declare an elementary data type, it is not safe to assume that its memory consumption is the same as its nominal storage allocation.</span></span> <span data-ttu-id="38a28-173">这是由于下列注意事项：</span><span class="sxs-lookup"><span data-stu-id="38a28-173">This is due to the following considerations:</span></span>  
  
- <span data-ttu-id="38a28-174">**存储分配。**</span><span class="sxs-lookup"><span data-stu-id="38a28-174">**Storage Assignment.**</span></span> <span data-ttu-id="38a28-175">公共语言运行时可以基于执行应用程序的平台的当前特性来分配存储空间。</span><span class="sxs-lookup"><span data-stu-id="38a28-175">The common language runtime can assign storage based on the current characteristics of the platform on which your application is executing.</span></span> <span data-ttu-id="38a28-176">如果内存几乎已满，则可能会将声明的元素尽可能紧密地打包在一起。</span><span class="sxs-lookup"><span data-stu-id="38a28-176">If memory is nearly full, it might pack your declared elements as closely together as possible.</span></span> <span data-ttu-id="38a28-177">在其他情况下，它可能会将内存地址与自然硬件边界对齐，以优化性能。</span><span class="sxs-lookup"><span data-stu-id="38a28-177">In other cases it might align their memory addresses to natural hardware boundaries to optimize performance.</span></span>  
  
- <span data-ttu-id="38a28-178">**平台宽度。**</span><span class="sxs-lookup"><span data-stu-id="38a28-178">**Platform Width.**</span></span> <span data-ttu-id="38a28-179">64位平台上的存储分配不同于32位平台上的分配。</span><span class="sxs-lookup"><span data-stu-id="38a28-179">Storage assignment on a 64-bit platform is different from assignment on a 32-bit platform.</span></span>  
  
### <a name="composite-data-types"></a><span data-ttu-id="38a28-180">复合数据类型</span><span class="sxs-lookup"><span data-stu-id="38a28-180">Composite Data Types</span></span>  

 <span data-ttu-id="38a28-181">相同的注意事项也适用于复合数据类型的每个成员，如结构或数组。</span><span class="sxs-lookup"><span data-stu-id="38a28-181">The same considerations apply to each member of a composite data type, such as a structure or an array.</span></span> <span data-ttu-id="38a28-182">你不能只是将类型成员的标称存储分配组合在一起。</span><span class="sxs-lookup"><span data-stu-id="38a28-182">You cannot rely on simply adding together the nominal storage allocations of the type's members.</span></span> <span data-ttu-id="38a28-183">此外，还有其他注意事项，如以下内容：</span><span class="sxs-lookup"><span data-stu-id="38a28-183">Furthermore, there are other considerations, such as the following:</span></span>  
  
- <span data-ttu-id="38a28-184">**费用.**</span><span class="sxs-lookup"><span data-stu-id="38a28-184">**Overhead.**</span></span> <span data-ttu-id="38a28-185">某些复合类型具有额外的内存需求。</span><span class="sxs-lookup"><span data-stu-id="38a28-185">Some composite types have additional memory requirements.</span></span> <span data-ttu-id="38a28-186">例如，数组对数组本身和每个维度使用额外的内存。</span><span class="sxs-lookup"><span data-stu-id="38a28-186">For example, an array uses extra memory for the array itself and also for each dimension.</span></span> <span data-ttu-id="38a28-187">在32位平台上，此开销目前为每个维度12个字节加上8个字节。</span><span class="sxs-lookup"><span data-stu-id="38a28-187">On a 32-bit platform, this overhead is currently 12 bytes plus 8 bytes for each dimension.</span></span> <span data-ttu-id="38a28-188">在64位平台上，此要求翻倍。</span><span class="sxs-lookup"><span data-stu-id="38a28-188">On a 64-bit platform this requirement is doubled.</span></span>  
  
- <span data-ttu-id="38a28-189">**存储布局。**</span><span class="sxs-lookup"><span data-stu-id="38a28-189">**Storage Layout.**</span></span> <span data-ttu-id="38a28-190">不能安全地假设内存中存储的顺序与声明顺序相同。</span><span class="sxs-lookup"><span data-stu-id="38a28-190">You cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="38a28-191">甚至不能对字节对齐进行假设，如2字节或4字节边界。</span><span class="sxs-lookup"><span data-stu-id="38a28-191">You cannot even make assumptions about byte alignment, such as a 2-byte or 4-byte boundary.</span></span> <span data-ttu-id="38a28-192">如果要定义类或结构，并且需要控制其成员的存储布局，则可以将属性应用于 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 类或结构。</span><span class="sxs-lookup"><span data-stu-id="38a28-192">If you are defining a class or structure and you need to control the storage layout of its members, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the class or structure.</span></span>  
  
### <a name="object-overhead"></a><span data-ttu-id="38a28-193">对象开销</span><span class="sxs-lookup"><span data-stu-id="38a28-193">Object Overhead</span></span>  

 <span data-ttu-id="38a28-194">`Object`除数据类型中包含的数据外，引用任何基本数据类型或复合数据类型的也使用4个字节。</span><span class="sxs-lookup"><span data-stu-id="38a28-194">An `Object` referring to any elementary or composite data type uses 4 bytes in addition to the data contained in the data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a28-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38a28-195">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="38a28-196">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="38a28-196">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="38a28-197">转换摘要</span><span class="sxs-lookup"><span data-stu-id="38a28-197">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="38a28-198">类型字符</span><span class="sxs-lookup"><span data-stu-id="38a28-198">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="38a28-199">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="38a28-199">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
