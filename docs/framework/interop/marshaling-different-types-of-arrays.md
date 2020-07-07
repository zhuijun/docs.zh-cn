---
title: 封送处理不同类型的数组
description: 封送不同的数组类型，如按值或引用的整数、按值的二维整数、按值的字符串以及包含整数或字符串的结构。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621491"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="27dad-103">封送处理不同类型的数组</span><span class="sxs-lookup"><span data-stu-id="27dad-103">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="27dad-104">数组是包含有一个或多个相同类型的元素的托管代码中的引用类型。</span><span class="sxs-lookup"><span data-stu-id="27dad-104">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="27dad-105">尽管数组是引用类型，但它们却作为 In 参数传递到非托管函数。</span><span class="sxs-lookup"><span data-stu-id="27dad-105">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="27dad-106">此行为与托管数组传递到托管对象的方式不一致，数组作为 In/Out 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-106">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="27dad-107">有关其他详细信息，请参阅 [复制和锁定](copying-and-pinning.md)。</span><span class="sxs-lookup"><span data-stu-id="27dad-107">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="27dad-108">下表列出了数组的封送处理选项，并描述了它们的用法。</span><span class="sxs-lookup"><span data-stu-id="27dad-108">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="27dad-109">数组</span><span class="sxs-lookup"><span data-stu-id="27dad-109">Array</span></span>|<span data-ttu-id="27dad-110">描述</span><span class="sxs-lookup"><span data-stu-id="27dad-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="27dad-111">通过值传递的整数。</span><span class="sxs-lookup"><span data-stu-id="27dad-111">Of integers by value.</span></span>|<span data-ttu-id="27dad-112">将整数的数组作为 In 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-112">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="27dad-113">通过引用传递的整数。</span><span class="sxs-lookup"><span data-stu-id="27dad-113">Of integers by reference.</span></span>|<span data-ttu-id="27dad-114">将整数的数组作为 In/Out 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-114">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="27dad-115">通过值传递的整数（二维）。</span><span class="sxs-lookup"><span data-stu-id="27dad-115">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="27dad-116">将整数的矩阵作为 In 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-116">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="27dad-117">通过值传递的字符串。</span><span class="sxs-lookup"><span data-stu-id="27dad-117">Of strings by value.</span></span>|<span data-ttu-id="27dad-118">将字符串的数组作为 In 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-118">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="27dad-119">传递具有整数的结构。</span><span class="sxs-lookup"><span data-stu-id="27dad-119">Of structures with integers.</span></span>|<span data-ttu-id="27dad-120">将包含整数的结构数组作为 In 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-120">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="27dad-121">传递具有字符串的结构。</span><span class="sxs-lookup"><span data-stu-id="27dad-121">Of structures with strings.</span></span>|<span data-ttu-id="27dad-122">将仅包含字符串的结构数组作为 In/Out 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-122">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="27dad-123">可以更改数组的成员。</span><span class="sxs-lookup"><span data-stu-id="27dad-123">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27dad-124">示例</span><span class="sxs-lookup"><span data-stu-id="27dad-124">Example</span></span>  
 <span data-ttu-id="27dad-125">本示例演示如何传递以下类型的数组：</span><span class="sxs-lookup"><span data-stu-id="27dad-125">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="27dad-126">通过值传递的整数数组。</span><span class="sxs-lookup"><span data-stu-id="27dad-126">Array of integers by value.</span></span>  
  
- <span data-ttu-id="27dad-127">通过引用传递的整数数组（可以调整大小）。</span><span class="sxs-lookup"><span data-stu-id="27dad-127">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="27dad-128">通过值传递的整数多维数组（矩阵）。</span><span class="sxs-lookup"><span data-stu-id="27dad-128">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="27dad-129">通过值传递的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="27dad-129">Array of strings by value.</span></span>  
  
- <span data-ttu-id="27dad-130">传递具有整数的结构数组。</span><span class="sxs-lookup"><span data-stu-id="27dad-130">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="27dad-131">传递具有字符串的结构数组。</span><span class="sxs-lookup"><span data-stu-id="27dad-131">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="27dad-132">除非数组由引用显式地进行封送处理，否则将以默认行为将数组封送为 In 参数。</span><span class="sxs-lookup"><span data-stu-id="27dad-132">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="27dad-133">通过显示应用 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 属性，可以更改此行为。</span><span class="sxs-lookup"><span data-stu-id="27dad-133">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="27dad-134">数组示例使用以下非托管函数，这些函数与其原始函数声明一起显示：</span><span class="sxs-lookup"><span data-stu-id="27dad-134">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="27dad-135">从 PinvokeLib.dll 导出的**TestArrayOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="27dad-135">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="27dad-136">从 PinvokeLib.dll 导出的**TestRefArrayOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="27dad-136">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="27dad-137">从 PinvokeLib.dll 导出的**TestMatrixOfInts** 。</span><span class="sxs-lookup"><span data-stu-id="27dad-137">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="27dad-138">从 PinvokeLib.dll 导出的**TestArrayOfStrings** 。</span><span class="sxs-lookup"><span data-stu-id="27dad-138">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="27dad-139">从 PinvokeLib.dll 导出的**TestArrayOfStructs** 。</span><span class="sxs-lookup"><span data-stu-id="27dad-139">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="27dad-140">从 PinvokeLib.dll 导出的**TestArrayOfStructs2** 。</span><span class="sxs-lookup"><span data-stu-id="27dad-140">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="27dad-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是一个自定义的非托管库，它包含之前列出的函数、两个结构变量（ **MYPOINT** 和 **MYPERSON**）的实现。</span><span class="sxs-lookup"><span data-stu-id="27dad-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="27dad-142">此结构包含以下元素：</span><span class="sxs-lookup"><span data-stu-id="27dad-142">The structures contain the following elements:</span></span>  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 <span data-ttu-id="27dad-143">在此示例中， `MyPoint` 和 `MyPerson` 结构包含嵌入类型。</span><span class="sxs-lookup"><span data-stu-id="27dad-143">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="27dad-144">设置 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 特性，以确保成员在内存中按照它们出现的顺序进行排列。</span><span class="sxs-lookup"><span data-stu-id="27dad-144">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="27dad-145">`NativeMethods` 类包含一组 `App` 类调用的方法。</span><span class="sxs-lookup"><span data-stu-id="27dad-145">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="27dad-146">有关传递数组的特定详细信息，请参阅以下示例中的注释。</span><span class="sxs-lookup"><span data-stu-id="27dad-146">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="27dad-147">默认情况下，一个引用类型的数组将作为 In 参数进行传递。</span><span class="sxs-lookup"><span data-stu-id="27dad-147">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="27dad-148">为使调用方接收结果， **InAttribute** 和 **OutAttribute** 必须显式应用于包含该数组的参数。</span><span class="sxs-lookup"><span data-stu-id="27dad-148">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="27dad-149">声明原型</span><span class="sxs-lookup"><span data-stu-id="27dad-149">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="27dad-150">调用函数</span><span class="sxs-lookup"><span data-stu-id="27dad-150">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="27dad-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="27dad-151">See also</span></span>

- [<span data-ttu-id="27dad-152">平台调用数据类型</span><span class="sxs-lookup"><span data-stu-id="27dad-152">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="27dad-153">在托管代码中创建原型</span><span class="sxs-lookup"><span data-stu-id="27dad-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
