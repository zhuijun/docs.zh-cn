---
title: 封送类、结构和联合
description: 查看如何封送类、结构和联合。 查看封送类的示例、具有嵌套结构的结构、结构的数组和联合。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 5e616b5bb513939cadd8fe5c72675ba0b6e070a3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621517"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="65fea-104">封送类、结构和联合</span><span class="sxs-lookup"><span data-stu-id="65fea-104">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="65fea-105">.NET Framework 中类和结构非常相似。</span><span class="sxs-lookup"><span data-stu-id="65fea-105">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="65fea-106">它们都可以具有字段、属性和事件。</span><span class="sxs-lookup"><span data-stu-id="65fea-106">Both can have fields, properties, and events.</span></span> <span data-ttu-id="65fea-107">并且都可以具有静态和非静态方法。</span><span class="sxs-lookup"><span data-stu-id="65fea-107">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="65fea-108">一个显著区别是结构是值类型，而类是引用类型。</span><span class="sxs-lookup"><span data-stu-id="65fea-108">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="65fea-109">下表列出了类、结构和联合的封送处理选项；描述了它们的用法；并提供了到相应平台调用示例的链接。</span><span class="sxs-lookup"><span data-stu-id="65fea-109">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="65fea-110">类型</span><span class="sxs-lookup"><span data-stu-id="65fea-110">Type</span></span>|<span data-ttu-id="65fea-111">描述</span><span class="sxs-lookup"><span data-stu-id="65fea-111">Description</span></span>|<span data-ttu-id="65fea-112">示例</span><span class="sxs-lookup"><span data-stu-id="65fea-112">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="65fea-113">按值传递类。</span><span class="sxs-lookup"><span data-stu-id="65fea-113">Class by value.</span></span>|<span data-ttu-id="65fea-114">将具有整数成员的类传递为 In/Out 参数，与托管的情形相似。</span><span class="sxs-lookup"><span data-stu-id="65fea-114">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="65fea-115">SysTime 示例</span><span class="sxs-lookup"><span data-stu-id="65fea-115">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="65fea-116">按值传递结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-116">Structure by value.</span></span>|<span data-ttu-id="65fea-117">将结构作为 In 参数传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-117">Passes structures as In parameters.</span></span>|[<span data-ttu-id="65fea-118">结构示例</span><span class="sxs-lookup"><span data-stu-id="65fea-118">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="65fea-119">按引用传递结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-119">Structure by reference.</span></span>|<span data-ttu-id="65fea-120">将结构作为 In/Out 参数传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-120">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="65fea-121">[OSInfo 示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65fea-121">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="65fea-122">具有内嵌结构（平展）的结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-122">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="65fea-123">传递非托管函数中表示内嵌结构的结构的类。</span><span class="sxs-lookup"><span data-stu-id="65fea-123">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="65fea-124">此结构在托管的原型中将平展为一个大的结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-124">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="65fea-125">FindFile 示例</span><span class="sxs-lookup"><span data-stu-id="65fea-125">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="65fea-126">具有指向另一结构的指针的结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-126">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="65fea-127">将包含指向第二结构的指针的结构作为成员传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-127">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="65fea-128">结构示例</span><span class="sxs-lookup"><span data-stu-id="65fea-128">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="65fea-129">按值传递具有整数的结构数组。</span><span class="sxs-lookup"><span data-stu-id="65fea-129">Array of structures with integers by value.</span></span>|<span data-ttu-id="65fea-130">将仅包含整数的结构数组作为 In/Out 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-130">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="65fea-131">可以更改数组的成员。</span><span class="sxs-lookup"><span data-stu-id="65fea-131">Members of the array can be changed.</span></span>|[<span data-ttu-id="65fea-132">数组示例</span><span class="sxs-lookup"><span data-stu-id="65fea-132">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="65fea-133">按引用传递具有整数和字符串的结构数组。</span><span class="sxs-lookup"><span data-stu-id="65fea-133">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="65fea-134">将包含整数和字符串的结构数组作为 Out 参数传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-134">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="65fea-135">被调用的函数为数组分配内存。</span><span class="sxs-lookup"><span data-stu-id="65fea-135">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="65fea-136">OutArrayOfStructs 示例</span><span class="sxs-lookup"><span data-stu-id="65fea-136">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="65fea-137">具有值类型的联合。</span><span class="sxs-lookup"><span data-stu-id="65fea-137">Unions with value types.</span></span>|<span data-ttu-id="65fea-138">传递具有值类型（整数和双精度）的联合。</span><span class="sxs-lookup"><span data-stu-id="65fea-138">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="65fea-139">联合示例</span><span class="sxs-lookup"><span data-stu-id="65fea-139">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="65fea-140">具有混合类型的联合。</span><span class="sxs-lookup"><span data-stu-id="65fea-140">Unions with mixed types.</span></span>|<span data-ttu-id="65fea-141">传递具有混合类型（整数和字符串）的联合。</span><span class="sxs-lookup"><span data-stu-id="65fea-141">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="65fea-142">联合示例</span><span class="sxs-lookup"><span data-stu-id="65fea-142">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="65fea-143">具有特定于平台的布局的结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-143">Struct with platform-specific layout.</span></span>|<span data-ttu-id="65fea-144">使用本机打包定义传递类型。</span><span class="sxs-lookup"><span data-stu-id="65fea-144">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="65fea-145">平台示例</span><span class="sxs-lookup"><span data-stu-id="65fea-145">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="65fea-146">结构中的 null 值。</span><span class="sxs-lookup"><span data-stu-id="65fea-146">Null values in structure.</span></span>|<span data-ttu-id="65fea-147">传递空引用（Visual Basic 中为 Nothing），而不传递对值类型的引用。</span><span class="sxs-lookup"><span data-stu-id="65fea-147">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="65fea-148">[HandleRef 示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="65fea-148">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="65fea-149">结构示例</span><span class="sxs-lookup"><span data-stu-id="65fea-149">Structures sample</span></span>

<span data-ttu-id="65fea-150">此示例演示了如何传递指向第二结构的结构、具有嵌入结构的结构和具有嵌入数组的结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-150">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="65fea-151">“结构”示例使用以下非托管函数（与原始函数声明一同显示）：</span><span class="sxs-lookup"><span data-stu-id="65fea-151">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="65fea-152">从 PinvokeLib.dll 导出的 TestStructInStruct。</span><span class="sxs-lookup"><span data-stu-id="65fea-152">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="65fea-153">从 PinvokeLib.dll 导出的 TestStructInStruct3。</span><span class="sxs-lookup"><span data-stu-id="65fea-153">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="65fea-154">从 PinvokeLib.dll 导出的 TestArrayInStruct。</span><span class="sxs-lookup"><span data-stu-id="65fea-154">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="65fea-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是一种自定义的非托管库，包含上述函数和 4 种结构（MYPERSON、MYPERSON2、MYPERSON3 和 MYARRAYSTRUCT   ）的实现。</span><span class="sxs-lookup"><span data-stu-id="65fea-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="65fea-156">这些结构包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="65fea-156">These structures contain the following elements:</span></span>

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

<span data-ttu-id="65fea-157">托管的 `MyPerson`、`MyPerson2`、`MyPerson3` 和 `MyArrayStruct` 结构具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="65fea-157">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="65fea-158">`MyPerson` 仅包含字符串成员。</span><span class="sxs-lookup"><span data-stu-id="65fea-158">`MyPerson` contains only string members.</span></span> <span data-ttu-id="65fea-159">[CharSet](specifying-a-character-set.md) 字段在传递到非托管函数时将字符串设置为 ANSI 格式。</span><span class="sxs-lookup"><span data-stu-id="65fea-159">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="65fea-160">`MyPerson2` 将 IntPtr 包含到 `MyPerson` 结构中。</span><span class="sxs-lookup"><span data-stu-id="65fea-160">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="65fea-161">IntPtr 类型替换指向非托管结构的原始指针，因为 .NET Framework 应用程序不使用指针，除非代码被标记为“不安全” 。</span><span class="sxs-lookup"><span data-stu-id="65fea-161">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="65fea-162">`MyPerson3` 将 `MyPerson` 作为嵌入结构包含在内。</span><span class="sxs-lookup"><span data-stu-id="65fea-162">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="65fea-163">嵌入其他结构的结构可通过将嵌入结构的元素直接放入主结构中来进行平展，还可以保留为嵌入结构，如本示例中操作所示。</span><span class="sxs-lookup"><span data-stu-id="65fea-163">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="65fea-164">`MyArrayStruct` 包含整数数组。</span><span class="sxs-lookup"><span data-stu-id="65fea-164">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="65fea-165"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性将 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举值设置为 ByValArray，此值用于指示数组中的元素数。</span><span class="sxs-lookup"><span data-stu-id="65fea-165">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="65fea-166">对于此示例中的所有结构，应用 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性以确保成员在内存中按出现的顺序进行排列。</span><span class="sxs-lookup"><span data-stu-id="65fea-166">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="65fea-167">`NativeMethods` 类包含 `App` 类所调用的 `TestStructInStruct`、`TestStructInStruct3` 和 `TestArrayInStruct` 方法的托管原型。</span><span class="sxs-lookup"><span data-stu-id="65fea-167">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="65fea-168">每个原型均声明一个参数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="65fea-168">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="65fea-169">`TestStructInStruct` 将对 `MyPerson2` 类型的引用声明为其参数。</span><span class="sxs-lookup"><span data-stu-id="65fea-169">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="65fea-170">`TestStructInStruct3` 将 `MyPerson3` 类型声明为其参数并按值传递此参数。</span><span class="sxs-lookup"><span data-stu-id="65fea-170">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="65fea-171">`TestArrayInStruct` 将对 `MyArrayStruct` 类型的引用声明为其参数。</span><span class="sxs-lookup"><span data-stu-id="65fea-171">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="65fea-172">作为方法自变量的结构按值传递，除非此参数包含 ref（Visual Basic 中为 ByRef）关键字 。</span><span class="sxs-lookup"><span data-stu-id="65fea-172">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="65fea-173">例如，`TestStructInStruct` 方法将对 `MyPerson2` 类型对象的引用（地址的值）传递到非托管代码。</span><span class="sxs-lookup"><span data-stu-id="65fea-173">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="65fea-174">为了处理 `MyPerson2` 指向的结构，此示例创建了具有指定大小的缓冲区，并同时使用 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> 和 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法返回其地址。</span><span class="sxs-lookup"><span data-stu-id="65fea-174">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="65fea-175">然后，此示例将该托管结构的内容复制到非托管的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="65fea-175">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="65fea-176">最后，此示例使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> 方法将非托管缓冲区的数据封送到托管对象，并使用 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> 方法释放非托管的内存块。</span><span class="sxs-lookup"><span data-stu-id="65fea-176">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="65fea-177">声明原型</span><span class="sxs-lookup"><span data-stu-id="65fea-177">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="65fea-178">调用函数</span><span class="sxs-lookup"><span data-stu-id="65fea-178">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="65fea-179">FindFile 示例</span><span class="sxs-lookup"><span data-stu-id="65fea-179">FindFile sample</span></span>

<span data-ttu-id="65fea-180">此示例演示了如何将包含第二、嵌入结构的结构传递到非托管函数。</span><span class="sxs-lookup"><span data-stu-id="65fea-180">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="65fea-181">它还演示了如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性在结构中声明固定长度的数组。</span><span class="sxs-lookup"><span data-stu-id="65fea-181">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="65fea-182">在此示例中，嵌入的结构元素将添加到父结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-182">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="65fea-183">有关未平展的嵌入结构的示例，请参阅[结构示例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="65fea-183">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="65fea-184">FindFile 示例使用以下的非托管函数（与其原始函数声明一同显示）：</span><span class="sxs-lookup"><span data-stu-id="65fea-184">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="65fea-185">从 Kernel32.dll 导出的 FindFirstFile。</span><span class="sxs-lookup"><span data-stu-id="65fea-185">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="65fea-186">传递至函数的原始结构包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="65fea-186">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

<span data-ttu-id="65fea-187">在此示例中，`FindData` 类包含原始结构和嵌入结构中每个元素的对应数据成员。</span><span class="sxs-lookup"><span data-stu-id="65fea-187">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="65fea-188">如果存在 2 个原始字符缓冲区，类将替换字符串。</span><span class="sxs-lookup"><span data-stu-id="65fea-188">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="65fea-189">MarshalAsAttribute 将 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举设置为 ByValTStr，它用于标识非托管结构中出现的定长内联字符数组 。</span><span class="sxs-lookup"><span data-stu-id="65fea-189">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="65fea-190">`NativeMethods` 类包含 `FindFirstFile` 方法的托管原型，此方法将 `FindData` 类作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-190">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="65fea-191">此参数必须使用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 属性进行声明，因为作为引用类型的类默认传递为 In 参数。</span><span class="sxs-lookup"><span data-stu-id="65fea-191">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="65fea-192">声明原型</span><span class="sxs-lookup"><span data-stu-id="65fea-192">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="65fea-193">调用函数</span><span class="sxs-lookup"><span data-stu-id="65fea-193">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="65fea-194">“联合”示例</span><span class="sxs-lookup"><span data-stu-id="65fea-194">Unions sample</span></span>

<span data-ttu-id="65fea-195">此示例演示了如何将仅包含值类型的结构以及包含值类型和字符串的结构作为参数传递至需要联合的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="65fea-195">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="65fea-196">联合是指可由两个或多个变量共享的内存位置。</span><span class="sxs-lookup"><span data-stu-id="65fea-196">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="65fea-197">“联合”示例使用以下非托管函数（与其原始函数声明一同显示）：</span><span class="sxs-lookup"><span data-stu-id="65fea-197">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="65fea-198">从 PinvokeLib.dll 导出的 TestUnion。</span><span class="sxs-lookup"><span data-stu-id="65fea-198">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="65fea-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是一种自定义的非托管库，包含上述函数和两个联合（MYUNION 和 MYUNION2）的实现。</span><span class="sxs-lookup"><span data-stu-id="65fea-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="65fea-200">联合包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="65fea-200">The unions contain the following elements:</span></span>

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

<span data-ttu-id="65fea-201">在托管代码中，将联合定义为结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-201">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="65fea-202">`MyUnion` 结构包含两个值类型（整数和双精度值），将其作为成员。</span><span class="sxs-lookup"><span data-stu-id="65fea-202">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="65fea-203"><xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性设置为控制每个数据成员的精确位置。</span><span class="sxs-lookup"><span data-stu-id="65fea-203">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="65fea-204"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> 属性提供联合的非托管表示形式中字段的物理位置。</span><span class="sxs-lookup"><span data-stu-id="65fea-204">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="65fea-205">请注意，这两个成员具有相同的偏移值，因此成员可以定义相同的内存块数。</span><span class="sxs-lookup"><span data-stu-id="65fea-205">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="65fea-206">`MyUnion2_1` 和 `MyUnion2_2` 分别包含值类型（整数）和字符串。</span><span class="sxs-lookup"><span data-stu-id="65fea-206">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="65fea-207">在托管代码中，值类型和引用类型不允许重叠。</span><span class="sxs-lookup"><span data-stu-id="65fea-207">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="65fea-208">此示例使用方法重载以使调用方在调用同一个非托管函数时能够使用这两种类型。</span><span class="sxs-lookup"><span data-stu-id="65fea-208">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="65fea-209">`MyUnion2_1` 的布局是显式的且具有准确的偏移值。</span><span class="sxs-lookup"><span data-stu-id="65fea-209">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="65fea-210">与此相反，`MyUnion2_2` 的布局是按顺序的，因为不允许引用类型使用显式布局。</span><span class="sxs-lookup"><span data-stu-id="65fea-210">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="65fea-211"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性将 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举设置为 ByValTStr，它用于标识在联合的非托管表示形式中出现的定长内联字符数组。</span><span class="sxs-lookup"><span data-stu-id="65fea-211">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="65fea-212">`NativeMethods` 类包含 `TestUnion` 和 `TestUnion2` 方法的原型。</span><span class="sxs-lookup"><span data-stu-id="65fea-212">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="65fea-213">已重载 `TestUnion2` 以将 `MyUnion2_1` 或 `MyUnion2_2` 声明为参数。</span><span class="sxs-lookup"><span data-stu-id="65fea-213">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="65fea-214">声明原型</span><span class="sxs-lookup"><span data-stu-id="65fea-214">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="65fea-215">调用函数</span><span class="sxs-lookup"><span data-stu-id="65fea-215">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="65fea-216">平台示例</span><span class="sxs-lookup"><span data-stu-id="65fea-216">Platform sample</span></span>

<span data-ttu-id="65fea-217">在某些情况下，`struct` 和 `union` 布局会因目标平台而异。</span><span class="sxs-lookup"><span data-stu-id="65fea-217">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="65fea-218">例如，在 COM 场景中定义时，请考虑 [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) 类型：</span><span class="sxs-lookup"><span data-stu-id="65fea-218">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

<span data-ttu-id="65fea-219">上述 `struct` 是通过影响类型的内存布局的 Windows 标头声明的。</span><span class="sxs-lookup"><span data-stu-id="65fea-219">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="65fea-220">在托管环境中定义时，需要使用这些布局详细信息来正确地与本机代码互操作。</span><span class="sxs-lookup"><span data-stu-id="65fea-220">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="65fea-221">在 32 位进程中，此类型的正确托管定义为：</span><span class="sxs-lookup"><span data-stu-id="65fea-221">The correct managed definition of this type in a 32-bit process is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

<span data-ttu-id="65fea-222">在 64 位进程中，大小和字段偏移量不同。</span><span class="sxs-lookup"><span data-stu-id="65fea-222">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="65fea-223">正确布局是：</span><span class="sxs-lookup"><span data-stu-id="65fea-223">The correct layout is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

<span data-ttu-id="65fea-224">如果未能在互操作场景中正确考虑本机布局，会导致随机故障或更糟糕的情况 - 计算不正确。</span><span class="sxs-lookup"><span data-stu-id="65fea-224">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="65fea-225">默认情况下，.NET 程序集可以在 32 位和 64 位版本的 .NET 运行时中运行。</span><span class="sxs-lookup"><span data-stu-id="65fea-225">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="65fea-226">应用必须等待运行时，以确定要使用的前几个定义。</span><span class="sxs-lookup"><span data-stu-id="65fea-226">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="65fea-227">下面的代码片段演示了如何在运行时，在 32 位和 64 位定义之间进行选择的示例。</span><span class="sxs-lookup"><span data-stu-id="65fea-227">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a><span data-ttu-id="65fea-228">SysTime 示例</span><span class="sxs-lookup"><span data-stu-id="65fea-228">SysTime sample</span></span>

<span data-ttu-id="65fea-229">此示例演示了如何将指向类的指针传递到需要指向结构的指针的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="65fea-229">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="65fea-230">SysTime 示例使用以下非托管函数（与其其原始函数声明一同显示）：</span><span class="sxs-lookup"><span data-stu-id="65fea-230">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="65fea-231">从 Kernel32.dll 导出的 GetSystemTime。</span><span class="sxs-lookup"><span data-stu-id="65fea-231">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="65fea-232">传递至函数的原始结构包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="65fea-232">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="65fea-233">在此示例中，`SystemTime` 类包含原始结构中表示为类成员的元素。</span><span class="sxs-lookup"><span data-stu-id="65fea-233">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="65fea-234">设置 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 特性，以确保成员在内存中按照它们出现的顺序进行排列。</span><span class="sxs-lookup"><span data-stu-id="65fea-234">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="65fea-235">`NativeMethods` 类包含 `GetSystemTime` 方法的托管原型，此方法在默认情况下将 `SystemTime` 类作为 In/Out 参数传递。</span><span class="sxs-lookup"><span data-stu-id="65fea-235">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="65fea-236">此参数必须使用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 属性进行声明，因为作为引用类型的类默认传递为 In 参数。</span><span class="sxs-lookup"><span data-stu-id="65fea-236">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="65fea-237">为使调用方接收结果，这些[方向特性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))必须显式应用。</span><span class="sxs-lookup"><span data-stu-id="65fea-237">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="65fea-238">`App` 类创建 `SystemTime` 类的新实例，并访问它的数据字段。</span><span class="sxs-lookup"><span data-stu-id="65fea-238">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="65fea-239">代码示例</span><span class="sxs-lookup"><span data-stu-id="65fea-239">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="65fea-240">OutArrayOfStructs 示例</span><span class="sxs-lookup"><span data-stu-id="65fea-240">OutArrayOfStructs sample</span></span>

<span data-ttu-id="65fea-241">此示例显示如何将包含整数和字符串的结构数组作为 Out 参数传递到非托管函数。</span><span class="sxs-lookup"><span data-stu-id="65fea-241">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="65fea-242">此示例演示如何通过使用 <xref:System.Runtime.InteropServices.Marshal> 类和使用不安全代码调用本机函数。</span><span class="sxs-lookup"><span data-stu-id="65fea-242">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="65fea-243">此示例使用 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 中定义（且位于源文件）的包装器函数和平台调用。</span><span class="sxs-lookup"><span data-stu-id="65fea-243">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="65fea-244">它使用 `TestOutArrayOfStructs` 函数和 `MYSTRSTRUCT2` 结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-244">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="65fea-245">结构包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="65fea-245">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="65fea-246">`MyStruct` 类包含 ANSI 字符的字符串对象。</span><span class="sxs-lookup"><span data-stu-id="65fea-246">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="65fea-247"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 字段指定 ANSI 格式。</span><span class="sxs-lookup"><span data-stu-id="65fea-247">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="65fea-248">`MyUnsafeStruct` 是一种包含 <xref:System.IntPtr> 类型（而非字符串）的结构。</span><span class="sxs-lookup"><span data-stu-id="65fea-248">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="65fea-249">`NativeMethods` 类包含已重载 `TestOutArrayOfStructs` 原型方法。</span><span class="sxs-lookup"><span data-stu-id="65fea-249">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="65fea-250">如果方法将指针声明为参数，则应使用 `unsafe` 关键字标记类。</span><span class="sxs-lookup"><span data-stu-id="65fea-250">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="65fea-251">因为 Visual Basic 无法使用不安全的代码，所以重载的方法、不安全的修饰符和 `MyUnsafeStruct` 结构不是必需的。</span><span class="sxs-lookup"><span data-stu-id="65fea-251">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="65fea-252">`App` 类实现 `UsingMarshaling` 方法，此方法执行传递数组所需的全部任务。</span><span class="sxs-lookup"><span data-stu-id="65fea-252">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="65fea-253">使用 `out`（Visual Basic 中的 `ByRef`）关键字标记数组，以指示数据从被调用方传递至调用方。</span><span class="sxs-lookup"><span data-stu-id="65fea-253">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="65fea-254">实现使用以下 <xref:System.Runtime.InteropServices.Marshal> 类方法：</span><span class="sxs-lookup"><span data-stu-id="65fea-254">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="65fea-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>，用于将数据从非托管缓冲区封送到托管对象。</span><span class="sxs-lookup"><span data-stu-id="65fea-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="65fea-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>用于释放为结构中的字符串保留的内存。</span><span class="sxs-lookup"><span data-stu-id="65fea-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="65fea-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>用于释放为数组保留的内存。</span><span class="sxs-lookup"><span data-stu-id="65fea-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="65fea-258">正如上文所述，C# 允许使用不安全的代码，而 Visual Basic 不允许。</span><span class="sxs-lookup"><span data-stu-id="65fea-258">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="65fea-259">在 C# 示例中，`UsingUnsafePointer` 是一种替代性方法实现，使用指针（而非 <xref:System.Runtime.InteropServices.Marshal> 类）传递会包含 `MyUnsafeStruct` 结构的数组。</span><span class="sxs-lookup"><span data-stu-id="65fea-259">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="65fea-260">声明原型</span><span class="sxs-lookup"><span data-stu-id="65fea-260">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="65fea-261">调用函数</span><span class="sxs-lookup"><span data-stu-id="65fea-261">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="65fea-262">请参阅</span><span class="sxs-lookup"><span data-stu-id="65fea-262">See also</span></span>

- [<span data-ttu-id="65fea-263">用平台调用封送数据</span><span class="sxs-lookup"><span data-stu-id="65fea-263">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="65fea-264">封送处理字符串</span><span class="sxs-lookup"><span data-stu-id="65fea-264">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="65fea-265">封送处理不同类型的数组</span><span class="sxs-lookup"><span data-stu-id="65fea-265">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
