---
title: 数组的默认封送处理
description: 了解数组的默认封送处理。 查看托管数组、非托管数组、将数组参数传递给 .NET 代码，以及将数组传递给 COM。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: 6bfe95576a6460efac75fd392e24acf42e36f2de
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555258"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="d25ba-104">数组的默认封送处理</span><span class="sxs-lookup"><span data-stu-id="d25ba-104">Default Marshaling for Arrays</span></span>
<span data-ttu-id="d25ba-105">在完全由托管代码组成的应用程序中，公共语言运行时将数组类型作为 In/Out 参数传递。</span><span class="sxs-lookup"><span data-stu-id="d25ba-105">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="d25ba-106">而互操作封送拆收器默认将数组作为 In 参数传递。</span><span class="sxs-lookup"><span data-stu-id="d25ba-106">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="d25ba-107">使用[固定优化](copying-and-pinning.md)，blittable 数组在与同一单元中的对象交互时，可能看上去像是作为 In/Out 参数运行。</span><span class="sxs-lookup"><span data-stu-id="d25ba-107">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="d25ba-108">但是，如果随后将代码导出到用于生成跨计算机代理的类型库，且该库用于跨单元封送调用，则调用可还原为真正的 In 参数行为。</span><span class="sxs-lookup"><span data-stu-id="d25ba-108">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="d25ba-109">数组本就很复杂，而托管数组和非托管数组之间的差异使它们比其他 blittable 类型具有更多信息。</span><span class="sxs-lookup"><span data-stu-id="d25ba-109">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="d25ba-110">托管数组</span><span class="sxs-lookup"><span data-stu-id="d25ba-110">Managed Arrays</span></span>  
 <span data-ttu-id="d25ba-111">可以有各种托管数组类型；但是，<xref:System.Array?displayProperty=nameWithType> 类是所有数组类型的基类。</span><span class="sxs-lookup"><span data-stu-id="d25ba-111">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="d25ba-112">System.Array 类的属性可确定数组的秩、长度、下限和上限，其方法可用于访问、搜索、复制、创建数组以及对数组排序。</span><span class="sxs-lookup"><span data-stu-id="d25ba-112">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="d25ba-113">这些数组类型是动态类型，在基类库中未定义相应的静态类型。</span><span class="sxs-lookup"><span data-stu-id="d25ba-113">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="d25ba-114">将元素类型和秩的每一种组合视作不同类型的数组非常方便。</span><span class="sxs-lookup"><span data-stu-id="d25ba-114">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="d25ba-115">因此，一维整数数组与一维 double 类型数组是不同的类型。</span><span class="sxs-lookup"><span data-stu-id="d25ba-115">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="d25ba-116">同样，二维整数数组与一维整数数组也不同。</span><span class="sxs-lookup"><span data-stu-id="d25ba-116">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="d25ba-117">比较类型时，不考虑数组界限。</span><span class="sxs-lookup"><span data-stu-id="d25ba-117">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="d25ba-118">如下表所示，托管数组的所有实例都必须有特定的元素类型、秩和下限。</span><span class="sxs-lookup"><span data-stu-id="d25ba-118">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="d25ba-119">托管数组类型</span><span class="sxs-lookup"><span data-stu-id="d25ba-119">Managed array type</span></span>|<span data-ttu-id="d25ba-120">元素类型</span><span class="sxs-lookup"><span data-stu-id="d25ba-120">Element type</span></span>|<span data-ttu-id="d25ba-121">级别</span><span class="sxs-lookup"><span data-stu-id="d25ba-121">Rank</span></span>|<span data-ttu-id="d25ba-122">下限</span><span class="sxs-lookup"><span data-stu-id="d25ba-122">Lower bound</span></span>|<span data-ttu-id="d25ba-123">签名表示法</span><span class="sxs-lookup"><span data-stu-id="d25ba-123">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="d25ba-124">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="d25ba-124">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="d25ba-125">由类型指定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-125">Specified by type.</span></span>|<span data-ttu-id="d25ba-126">由秩指定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-126">Specified by rank.</span></span>|<span data-ttu-id="d25ba-127">由界限视情况指定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-127">Optionally specified by bounds.</span></span>|<span data-ttu-id="d25ba-128">*type* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="d25ba-128">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="d25ba-129">ELEMENT_TYPE_CLASS</span><span class="sxs-lookup"><span data-stu-id="d25ba-129">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="d25ba-130">未知</span><span class="sxs-lookup"><span data-stu-id="d25ba-130">Unknown</span></span>|<span data-ttu-id="d25ba-131">未知</span><span class="sxs-lookup"><span data-stu-id="d25ba-131">Unknown</span></span>|<span data-ttu-id="d25ba-132">未知</span><span class="sxs-lookup"><span data-stu-id="d25ba-132">Unknown</span></span>|<span data-ttu-id="d25ba-133">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="d25ba-133">**System.Array**</span></span>|  
|<span data-ttu-id="d25ba-134">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="d25ba-134">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="d25ba-135">由类型指定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-135">Specified by type.</span></span>|<span data-ttu-id="d25ba-136">1</span><span class="sxs-lookup"><span data-stu-id="d25ba-136">1</span></span>|<span data-ttu-id="d25ba-137">0</span><span class="sxs-lookup"><span data-stu-id="d25ba-137">0</span></span>|<span data-ttu-id="d25ba-138">*type* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="d25ba-138">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="d25ba-139">非托管数组</span><span class="sxs-lookup"><span data-stu-id="d25ba-139">Unmanaged Arrays</span></span>  
 <span data-ttu-id="d25ba-140">非托管数组是 COM 样式安全数组或 C 样式数组，其长度固定或可变。</span><span class="sxs-lookup"><span data-stu-id="d25ba-140">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="d25ba-141">安全数组是自我描述的数组，带有关联数组数据的类型、秩和界限。</span><span class="sxs-lookup"><span data-stu-id="d25ba-141">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="d25ba-142">C 样式数组是具有固定下限 0 的一维类型化数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-142">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="d25ba-143">封送处理服务对两种数组类型的支持均有限。</span><span class="sxs-lookup"><span data-stu-id="d25ba-143">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="d25ba-144">将数组参数传递给 .NET 代码</span><span class="sxs-lookup"><span data-stu-id="d25ba-144">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="d25ba-145">C 样式数组和安全数组都可以作为安全数组或 C 样式数组从非托管代码传递给 .NET 代码。</span><span class="sxs-lookup"><span data-stu-id="d25ba-145">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="d25ba-146">下表显示非托管类型值和导入的类型。</span><span class="sxs-lookup"><span data-stu-id="d25ba-146">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="d25ba-147">非托管类型</span><span class="sxs-lookup"><span data-stu-id="d25ba-147">Unmanaged type</span></span>|<span data-ttu-id="d25ba-148">导入的类型</span><span class="sxs-lookup"><span data-stu-id="d25ba-148">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="d25ba-149">**SafeArray(** *Type* **)**</span><span class="sxs-lookup"><span data-stu-id="d25ba-149">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="d25ba-150">ELEMENT_TYPE_SZARRAY \<** *ConvertedType* **></span><span class="sxs-lookup"><span data-stu-id="d25ba-150">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="d25ba-151">秩 = 1，下限 = 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-151">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="d25ba-152">只有在托管签名中提供大小时，才知道大小。</span><span class="sxs-lookup"><span data-stu-id="d25ba-152">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="d25ba-153">不满足秩 = 1 或下限 = 0 的安全数组不能作为 SZARRAY 封送。</span><span class="sxs-lookup"><span data-stu-id="d25ba-153">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="d25ba-154">*Type*  **[]**</span><span class="sxs-lookup"><span data-stu-id="d25ba-154">*Type*  **[]**</span></span>|<span data-ttu-id="d25ba-155">ELEMENT_TYPE_SZARRAY \<** *ConvertedType* **></span><span class="sxs-lookup"><span data-stu-id="d25ba-155">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="d25ba-156">秩 = 1，下限 = 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-156">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="d25ba-157">只有在托管签名中提供大小时，才知道大小。</span><span class="sxs-lookup"><span data-stu-id="d25ba-157">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="d25ba-158">安全数组</span><span class="sxs-lookup"><span data-stu-id="d25ba-158">Safe Arrays</span></span>  
 <span data-ttu-id="d25ba-159">从类型库将安全数组导入 .NET 程序集时，该数组转换为已知类型（例如 int）的一维数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-159">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="d25ba-160">适用于参数的类型转换规则同样适用于数组元素。</span><span class="sxs-lookup"><span data-stu-id="d25ba-160">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="d25ba-161">例如，BSTR 类型的安全数组可变为托管字符串数组，而变体的安全数组可变为托管对象数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-161">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="d25ba-162">从类型库中捕获 SAFEARRAY 元素类型并将它保存在 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举的 SAFEARRAY 值中 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-162">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="d25ba-163">由于无法根据类型库确定安全数组的秩和界限，因此假定秩等于 1，下限等于 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-163">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="d25ba-164">必须在由[类型库导入程序 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 生成的托管签名中定义秩和界限。</span><span class="sxs-lookup"><span data-stu-id="d25ba-164">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="d25ba-165">如果运行时传递给方法的秩不同，则会引发 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>。</span><span class="sxs-lookup"><span data-stu-id="d25ba-165">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="d25ba-166">如果运行时传递的数组的类型不同，则会引发 <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException>。</span><span class="sxs-lookup"><span data-stu-id="d25ba-166">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="d25ba-167">下面的示例演示托管代码和非托管代码中的安全数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-167">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="d25ba-168">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-168">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="d25ba-169">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-169">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 <span data-ttu-id="d25ba-170">如果修改由 Tlbimp.exe 产生的方法签名以指示元素类型 ELEMENT_TYPE_ARRAY 而非 ELEMENT_TYPE_SZARRAY，则可将多维或非零界限安全数组封送到托管代码中 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-170">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="d25ba-171">或者，可将 /sysarray 开关与 Tlbimp.exe 一起使用，将所有数组作为 <xref:System.Array?displayProperty=nameWithType> 对象导入。</span><span class="sxs-lookup"><span data-stu-id="d25ba-171">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="d25ba-172">如果已知正在传递的数组是多维数组，则可编辑由 Tlbimp.exe 生成的 Microsoft 中间语言 (MSIL) 代码，然后重新编译它。</span><span class="sxs-lookup"><span data-stu-id="d25ba-172">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="d25ba-173">有关如何修改 MSIL 代码的详细信息，请参阅[自定义运行时可调用包装器](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d25ba-173">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="d25ba-174">C 样式数组</span><span class="sxs-lookup"><span data-stu-id="d25ba-174">C-Style Arrays</span></span>  
 <span data-ttu-id="d25ba-175">将 C 样式数组从类型库导入 .NET 程序集中时，数组被转换为 ELEMENT_TYPE_SZARRAY。</span><span class="sxs-lookup"><span data-stu-id="d25ba-175">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="d25ba-176">数组元素类型根据类型库确定并在导入期间保留。</span><span class="sxs-lookup"><span data-stu-id="d25ba-176">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="d25ba-177">适用于参数的转换规则同样适用于数组元素。</span><span class="sxs-lookup"><span data-stu-id="d25ba-177">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="d25ba-178">例如，LPStr 类型的数组变为字符串类型的数组 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-178">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="d25ba-179">Tlbimp.exe 捕获数组元素类型并将 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性应用于该参数。</span><span class="sxs-lookup"><span data-stu-id="d25ba-179">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="d25ba-180">假定数组秩等于 1。</span><span class="sxs-lookup"><span data-stu-id="d25ba-180">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="d25ba-181">如果秩大于 1，则将按列主序将数组作为一维数组封送。</span><span class="sxs-lookup"><span data-stu-id="d25ba-181">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="d25ba-182">下限始终等于 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-182">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="d25ba-183">类型库可包含定长数组或变长数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-183">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="d25ba-184">Tlbimp.exe 只能从类型库中导入定长数组，这是因为类型库缺少封送变长数组所需的信息。</span><span class="sxs-lookup"><span data-stu-id="d25ba-184">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="d25ba-185">对于定长数组，从类型库导入大小，并在应用于参数的 MarshalAsAttribute 中捕获大小。</span><span class="sxs-lookup"><span data-stu-id="d25ba-185">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="d25ba-186">必须手动定义含变长数组的类型库，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d25ba-186">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="d25ba-187">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-187">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="d25ba-188">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-188">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="d25ba-189">虽然可将 size_is 或 length_is 属性应用于接口定义语言 (IDL) 源中的数组，以便将大小传达给客户端，但是 Microsoft 接口定义语言 (MIDL) 编译器不会将该信息传送到类型库 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-189">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="d25ba-190">如果不知道大小，互操作封送处理服务就无法封送数组元素。</span><span class="sxs-lookup"><span data-stu-id="d25ba-190">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="d25ba-191">因此，将变长数组作为引用参数导入。</span><span class="sxs-lookup"><span data-stu-id="d25ba-191">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="d25ba-192">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-192">For example:</span></span>  
  
 <span data-ttu-id="d25ba-193">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-193">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="d25ba-194">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-194">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 <span data-ttu-id="d25ba-195">编辑由 Tlbimp.exe 生成的 Microsoft 中间语言 (MSIL) 代码，再重新编译该代码，即可向封送拆收器提供数组大小。</span><span class="sxs-lookup"><span data-stu-id="d25ba-195">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="d25ba-196">有关如何修改 MSIL 代码的详细信息，请参阅[自定义运行时可调用包装器](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d25ba-196">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="d25ba-197">要指示数组中的元素数，请采用以下任一方式将 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 类型应用于托管方法定义的数组参数：</span><span class="sxs-lookup"><span data-stu-id="d25ba-197">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="d25ba-198">标识含数组中的元素数的另一个参数。</span><span class="sxs-lookup"><span data-stu-id="d25ba-198">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="d25ba-199">按位置标识参数，从第一个参数开始，将第一个参数标识为数字 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-199">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- <span data-ttu-id="d25ba-200">将数组大小定义为常数。</span><span class="sxs-lookup"><span data-stu-id="d25ba-200">Define the size of the array as a constant.</span></span> <span data-ttu-id="d25ba-201">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-201">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="d25ba-202">将数组从非托管代码封送到托管代码时，封送拆收器检查与参数关联的 MarshalAsAttribute 以确定数组大小。</span><span class="sxs-lookup"><span data-stu-id="d25ba-202">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="d25ba-203">如果未指定数组大小，则只封送一个元素。</span><span class="sxs-lookup"><span data-stu-id="d25ba-203">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d25ba-204">将托管数组封送到非托管代码不会受 MarshalAsAttribute 的影响。</span><span class="sxs-lookup"><span data-stu-id="d25ba-204">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="d25ba-205">在该方向上，数组大小通过检查确定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-205">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="d25ba-206">无法封送托管数组的子集。</span><span class="sxs-lookup"><span data-stu-id="d25ba-206">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="d25ba-207">互操作封送拆收器使用 CoTaskMemAlloc 和 CoTaskMemFree 方法分配和检索内存 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-207">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="d25ba-208">非托管代码所执行的内存分配也必须使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="d25ba-208">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="d25ba-209">将数组传递给 COM</span><span class="sxs-lookup"><span data-stu-id="d25ba-209">Passing Arrays to COM</span></span>  
 <span data-ttu-id="d25ba-210">所有托管数组类型都可以从托管代码传递给非托管代码。</span><span class="sxs-lookup"><span data-stu-id="d25ba-210">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="d25ba-211">根据托管类型和应用于它的属性，可将数组作为安全数组或 C 样式数组进行访问，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="d25ba-211">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d25ba-212">托管数组类型</span><span class="sxs-lookup"><span data-stu-id="d25ba-212">Managed array type</span></span>|<span data-ttu-id="d25ba-213">导出结果</span><span class="sxs-lookup"><span data-stu-id="d25ba-213">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="d25ba-214">ELEMENT_TYPE_SZARRAY \<** *type* **></span><span class="sxs-lookup"><span data-stu-id="d25ba-214">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="d25ba-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="d25ba-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="d25ba-216">UnmanagedType.LPArray</span><span class="sxs-lookup"><span data-stu-id="d25ba-216">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="d25ba-217">签名中提供了类型。</span><span class="sxs-lookup"><span data-stu-id="d25ba-217">Type is provided in the signature.</span></span> <span data-ttu-id="d25ba-218">秩始终为 1，下限始终为 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-218">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="d25ba-219">在运行时大小始终为已知。</span><span class="sxs-lookup"><span data-stu-id="d25ba-219">Size is always known at run time.</span></span>|  
|<span data-ttu-id="d25ba-220">ELEMENT_TYPE_ARRAY \<** *type* **> \<** *rank* **>[\<** *bounds* **>]</span><span class="sxs-lookup"><span data-stu-id="d25ba-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="d25ba-221">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="d25ba-221">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="d25ba-222">UnmanagedType.LPArray</span><span class="sxs-lookup"><span data-stu-id="d25ba-222">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="d25ba-223">签名中提供了类型、秩和界限。</span><span class="sxs-lookup"><span data-stu-id="d25ba-223">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="d25ba-224">在运行时大小始终为已知。</span><span class="sxs-lookup"><span data-stu-id="d25ba-224">Size is always known at run time.</span></span>|  
|<span data-ttu-id="d25ba-225">ELEMENT_TYPE_CLASS \<**<xref:System.Array?displayProperty=nameWithType>>\*\*</span><span class="sxs-lookup"><span data-stu-id="d25ba-225">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span></span>|<span data-ttu-id="d25ba-226">UT_Interface</span><span class="sxs-lookup"><span data-stu-id="d25ba-226">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="d25ba-227">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="d25ba-227">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="d25ba-228">在运行时类型、秩、界限和大小始终为已知。</span><span class="sxs-lookup"><span data-stu-id="d25ba-228">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="d25ba-229">在与含有 LPSTR 或 LPWSTR 的结构数组相关的 OLE 自动化中，存在一项限制。</span><span class="sxs-lookup"><span data-stu-id="d25ba-229">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="d25ba-230">因此，必须将 String 字段作为 UnmanagedType.BSTR 封送 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-230">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="d25ba-231">否则，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="d25ba-231">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="d25ba-232">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="d25ba-232">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="d25ba-233">将包含 ELEMENT_TYPE_SZARRAY 参数（一维数组）的方法从 .NET 程序集导出到类型库时，会将该数组参数转换为给定类型的 SAFEARRAY 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-233">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="d25ba-234">同样的转换规则也适用于数组元素类型。</span><span class="sxs-lookup"><span data-stu-id="d25ba-234">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="d25ba-235">自动将托管数组的内容从托管内存复制到 SAFEARRAY 中。</span><span class="sxs-lookup"><span data-stu-id="d25ba-235">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="d25ba-236">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-236">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d25ba-237">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-237">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d25ba-238">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-238">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="d25ba-239">安全数组的秩始终为 1，下限始终为 0。</span><span class="sxs-lookup"><span data-stu-id="d25ba-239">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="d25ba-240">大小在运行时由所传递的托管数组的大小确定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-240">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="d25ba-241">还可以通过使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性将数组作为 C 样式数组封送。</span><span class="sxs-lookup"><span data-stu-id="d25ba-241">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="d25ba-242">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-242">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d25ba-243">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-243">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d25ba-244">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-244">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="d25ba-245">虽然封送拆收器具有封送数组所需的长度信息，但通常会将数组长度作为单独的参数传递，以便将长度传达给被调用方。</span><span class="sxs-lookup"><span data-stu-id="d25ba-245">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="d25ba-246">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="d25ba-246">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="d25ba-247">将包含 ELEMENT_TYPE_ARRAY 参数的方法从 .NET 程序集导出到类型库时，会将该数组参数转换为给定类型的 SAFEARRAY 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-247">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="d25ba-248">自动将托管数组的内容从托管内存复制到 SAFEARRAY 中。</span><span class="sxs-lookup"><span data-stu-id="d25ba-248">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="d25ba-249">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-249">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d25ba-250">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-250">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d25ba-251">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-251">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="d25ba-252">安全数组的秩、大小和界限在运行时由托管数组的特征确定。</span><span class="sxs-lookup"><span data-stu-id="d25ba-252">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="d25ba-253">还可以通过应用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性将数组作为 C 样式数组封送。</span><span class="sxs-lookup"><span data-stu-id="d25ba-253">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="d25ba-254">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-254">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d25ba-255">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-255">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d25ba-256">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-256">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="d25ba-257">无法封送嵌套数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-257">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="d25ba-258">例如，使用[类型库导出程序 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 进行导出时，以下签名将生成错误。</span><span class="sxs-lookup"><span data-stu-id="d25ba-258">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d25ba-259">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-259">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="d25ba-260">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="d25ba-260">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="d25ba-261">将包含 <xref:System.Array?displayProperty=nameWithType> 参数的方法从 .NET 程序集导出到类型库时，会将该数组参数转换为 _Array 接口。</span><span class="sxs-lookup"><span data-stu-id="d25ba-261">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="d25ba-262">只能通过 _Array 接口的方法和属性访问托管数组的内容。</span><span class="sxs-lookup"><span data-stu-id="d25ba-262">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="d25ba-263">还可通过使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性将 System.Array 作为 SAFEARRAY 封送 。</span><span class="sxs-lookup"><span data-stu-id="d25ba-263">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="d25ba-264">作为安全数组封送时，将数组元素视作变体封送。</span><span class="sxs-lookup"><span data-stu-id="d25ba-264">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="d25ba-265">例如：</span><span class="sxs-lookup"><span data-stu-id="d25ba-265">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d25ba-266">托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-266">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d25ba-267">非托管的签名</span><span class="sxs-lookup"><span data-stu-id="d25ba-267">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="d25ba-268">结构中的数组</span><span class="sxs-lookup"><span data-stu-id="d25ba-268">Arrays within Structures</span></span>  
 <span data-ttu-id="d25ba-269">非托管结构可包含嵌入数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-269">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="d25ba-270">默认情况下，将这些嵌入数组字段作为 SAFEARRAY 封送。</span><span class="sxs-lookup"><span data-stu-id="d25ba-270">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="d25ba-271">在以下示例中，`s1` 是直接在结构本身中分配的嵌入数组。</span><span class="sxs-lookup"><span data-stu-id="d25ba-271">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="d25ba-272">非托管表示形式</span><span class="sxs-lookup"><span data-stu-id="d25ba-272">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="d25ba-273">数组可作为 <xref:System.Runtime.InteropServices.UnmanagedType> 封送，这需要设置 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 字段。</span><span class="sxs-lookup"><span data-stu-id="d25ba-273">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="d25ba-274">只能将大小设置为常数。</span><span class="sxs-lookup"><span data-stu-id="d25ba-274">The size can be set only as a constant.</span></span> <span data-ttu-id="d25ba-275">以下代码演示 `MyStruct` 的相应托管定义。</span><span class="sxs-lookup"><span data-stu-id="d25ba-275">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d25ba-276">请参阅</span><span class="sxs-lookup"><span data-stu-id="d25ba-276">See also</span></span>

- [<span data-ttu-id="d25ba-277">默认封送处理行为</span><span class="sxs-lookup"><span data-stu-id="d25ba-277">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="d25ba-278">可直接复制到本机结构中的类型和非直接复制到本机结构中的类型</span><span class="sxs-lookup"><span data-stu-id="d25ba-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="d25ba-279">[方向特性](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d25ba-279">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="d25ba-280">复制和锁定</span><span class="sxs-lookup"><span data-stu-id="d25ba-280">Copying and Pinning</span></span>](copying-and-pinning.md)
