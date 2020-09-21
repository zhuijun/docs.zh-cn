---
title: 对象的默认封送处理
description: 了解对象的默认封送处理。 查看封送处理选项。 将对象封送到接口或变量、对象的变体和 ByRef 变体。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: 3e07ceef62d97db4206f530aa0859b101fe41a11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555089"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="73a6d-105">对象的默认封送处理</span><span class="sxs-lookup"><span data-stu-id="73a6d-105">Default Marshaling for Objects</span></span>

<span data-ttu-id="73a6d-106">可将类型化为 <xref:System.Object?displayProperty=nameWithType> 的参数和字段作为下列任一类型向非托管代码公开：</span><span class="sxs-lookup"><span data-stu-id="73a6d-106">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="73a6d-107">对象为参数时，作为变体。</span><span class="sxs-lookup"><span data-stu-id="73a6d-107">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="73a6d-108">对象为结构字段时，作为接口。</span><span class="sxs-lookup"><span data-stu-id="73a6d-108">An interface when the object is a structure field.</span></span>

<span data-ttu-id="73a6d-109">仅 COM 互操作支持对象类型的封送处理。</span><span class="sxs-lookup"><span data-stu-id="73a6d-109">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="73a6d-110">默认行为是将对象封送到 COM 变体。</span><span class="sxs-lookup"><span data-stu-id="73a6d-110">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="73a6d-111">这些规则只适用于 Object 类型，不适用于从 Object 类派生的强类型对象 。</span><span class="sxs-lookup"><span data-stu-id="73a6d-111">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="73a6d-112">封送处理选项</span><span class="sxs-lookup"><span data-stu-id="73a6d-112">Marshaling Options</span></span>

<span data-ttu-id="73a6d-113">下表显示 Object 数据类型的封送处理选项。</span><span class="sxs-lookup"><span data-stu-id="73a6d-113">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="73a6d-114"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性提供若干个 <xref:System.Runtime.InteropServices.UnmanagedType> 枚举值来封送对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-114">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="73a6d-115">枚举类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-115">Enumeration type</span></span>|<span data-ttu-id="73a6d-116">非托管格式说明</span><span class="sxs-lookup"><span data-stu-id="73a6d-116">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="73a6d-117">UnmanagedType.Struct</span><span class="sxs-lookup"><span data-stu-id="73a6d-117">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="73a6d-118">（参数默认值）</span><span class="sxs-lookup"><span data-stu-id="73a6d-118">(default for parameters)</span></span>|<span data-ttu-id="73a6d-119">COM 样式的变体。</span><span class="sxs-lookup"><span data-stu-id="73a6d-119">A COM-style variant.</span></span>|
|<span data-ttu-id="73a6d-120">UnmanagedType.Interface</span><span class="sxs-lookup"><span data-stu-id="73a6d-120">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="73a6d-121">如果可能，为 IDispatch 接口；否则为 IUnknown 接口 。</span><span class="sxs-lookup"><span data-stu-id="73a6d-121">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="73a6d-122">UnmanagedType.IUnknown</span><span class="sxs-lookup"><span data-stu-id="73a6d-122">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="73a6d-123">（字段默认值）</span><span class="sxs-lookup"><span data-stu-id="73a6d-123">(default for fields)</span></span>|<span data-ttu-id="73a6d-124">IUnknown 接口。</span><span class="sxs-lookup"><span data-stu-id="73a6d-124">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="73a6d-125">UnmanagedType.IDispatch</span><span class="sxs-lookup"><span data-stu-id="73a6d-125">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="73a6d-126">IDispatch 接口。</span><span class="sxs-lookup"><span data-stu-id="73a6d-126">An **IDispatch** interface.</span></span>|

<span data-ttu-id="73a6d-127">以下示例显示了 `MarshalObject` 的托管接口定义。</span><span class="sxs-lookup"><span data-stu-id="73a6d-127">The following example shows the managed interface definition for `MarshalObject`.</span></span>

```vb
Interface MarshalObject
   Sub SetVariant(o As Object)
   Sub SetVariantRef(ByRef o As Object)
   Function GetVariant() As Object

   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _
      As Object)
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _
      As Object)
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object
End Interface
```

```csharp
interface MarshalObject {
   void SetVariant(Object o);
   void SetVariantRef(ref Object o);
   Object GetVariant();

   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();
}
```

<span data-ttu-id="73a6d-128">以下代码将 `MarshalObject` 接口导出到类型库。</span><span class="sxs-lookup"><span data-stu-id="73a6d-128">The following code exports the `MarshalObject` interface to a type library.</span></span>

```cpp
interface MarshalObject {
   HRESULT SetVariant([in] VARIANT o);
   HRESULT SetVariantRef([in,out] VARIANT *o);
   HRESULT GetVariant([out,retval] VARIANT *o)
   HRESULT SetIDispatch([in] IDispatch *o);
   HRESULT SetIDispatchRef([in,out] IDispatch **o);
   HRESULT GetIDispatch([out,retval] IDispatch **o)
   HRESULT SetIUnknown([in] IUnknown *o);
   HRESULT SetIUnknownRef([in,out] IUnknown **o);
   HRESULT GetIUnknown([out,retval] IUnknown **o)
}
```

> [!NOTE]
> <span data-ttu-id="73a6d-129">互操作封送拆收器在调用后自动释放变体内所有已分配的对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-129">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="73a6d-130">以下示例显示已设置格式的值类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-130">The following example shows a formatted value type.</span></span>

```vb
Public Structure ObjectHolder
   Dim o1 As Object
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object
End Structure
```

```csharp
public struct ObjectHolder {
   Object o1;
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;
}
```

<span data-ttu-id="73a6d-131">以下代码将已设置格式的类型导出到类型库。</span><span class="sxs-lookup"><span data-stu-id="73a6d-131">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="73a6d-132">将对象封送到接口</span><span class="sxs-lookup"><span data-stu-id="73a6d-132">Marshaling Object to Interface</span></span>

<span data-ttu-id="73a6d-133">将对象作为接口向 COM 公开时，该接口是托管类型 <xref:System.Object> 的类接口（即 _Object 接口）。</span><span class="sxs-lookup"><span data-stu-id="73a6d-133">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="73a6d-134">该接口被类型化为 IDispatch (<xref:System.Runtime.InteropServices.UnmanagedType>) 或所得类型库中的 IUnknown (UnmanagedType.IUnknown)  。</span><span class="sxs-lookup"><span data-stu-id="73a6d-134">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="73a6d-135">通过 _Object 接口，COM 客户端可动态调用托管类的成员或由该托管类的派生类实现的任何成员。</span><span class="sxs-lookup"><span data-stu-id="73a6d-135">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="73a6d-136">客户端还可调用 QueryInterface 获取由托管类型显式实现的任何其他接口。</span><span class="sxs-lookup"><span data-stu-id="73a6d-136">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="73a6d-137">将对象封送到变体</span><span class="sxs-lookup"><span data-stu-id="73a6d-137">Marshaling Object to Variant</span></span>

<span data-ttu-id="73a6d-138">将对象封送到变体时，在运行时根据以下规则确定内部变体类型：</span><span class="sxs-lookup"><span data-stu-id="73a6d-138">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="73a6d-139">如果对象引用为 null（Visual Basic 中为 Nothing），则将对象封送到 VT_EMPTY 类型的变体 。</span><span class="sxs-lookup"><span data-stu-id="73a6d-139">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="73a6d-140">如果对象是下表中列出的任何类型的实例，则得到的变体类型由封送拆收器内置的规则确定，并且显示在下表中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-140">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="73a6d-141">需要显式控制封送行为的其他对象可实现 <xref:System.IConvertible> 接口。</span><span class="sxs-lookup"><span data-stu-id="73a6d-141">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="73a6d-142">在这种情况下，变体类型由从 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> 方法返回的类型代码确定。</span><span class="sxs-lookup"><span data-stu-id="73a6d-142">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="73a6d-143">否则，将对象作为 VT_UNKNOWN 类型的变体封送。</span><span class="sxs-lookup"><span data-stu-id="73a6d-143">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="73a6d-144">将系统类型封送到变体</span><span class="sxs-lookup"><span data-stu-id="73a6d-144">Marshaling System Types to Variant</span></span>

<span data-ttu-id="73a6d-145">下表显示托管对象类型及其相应的 COM 变体类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-145">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="73a6d-146">仅当所调用方法的签名属于 <xref:System.Object?displayProperty=nameWithType> 类型时，才转换这些类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-146">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="73a6d-147">对象类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-147">Object type</span></span>|<span data-ttu-id="73a6d-148">COM 变体类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-148">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="73a6d-149">Null 对象引用（在 Visual Basic 中为 Nothing）。</span><span class="sxs-lookup"><span data-stu-id="73a6d-149">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="73a6d-150">VT_EMPTY</span><span class="sxs-lookup"><span data-stu-id="73a6d-150">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="73a6d-151">VT_NULL</span><span class="sxs-lookup"><span data-stu-id="73a6d-151">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="73a6d-152">VT_ERROR</span><span class="sxs-lookup"><span data-stu-id="73a6d-152">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="73a6d-153">带 E_PARAMNOTFOUND 的 VT_ERROR </span><span class="sxs-lookup"><span data-stu-id="73a6d-153">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="73a6d-154">VT_DISPATCH</span><span class="sxs-lookup"><span data-stu-id="73a6d-154">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="73a6d-155">VT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="73a6d-155">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="73a6d-156">VT_CY</span><span class="sxs-lookup"><span data-stu-id="73a6d-156">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="73a6d-157">VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="73a6d-157">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="73a6d-158">VT_I1</span><span class="sxs-lookup"><span data-stu-id="73a6d-158">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="73a6d-159">VT_UI1</span><span class="sxs-lookup"><span data-stu-id="73a6d-159">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="73a6d-160">VT_I2</span><span class="sxs-lookup"><span data-stu-id="73a6d-160">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="73a6d-161">VT_UI2</span><span class="sxs-lookup"><span data-stu-id="73a6d-161">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="73a6d-162">VT_I4</span><span class="sxs-lookup"><span data-stu-id="73a6d-162">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="73a6d-163">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="73a6d-163">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="73a6d-164">VT_I8</span><span class="sxs-lookup"><span data-stu-id="73a6d-164">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="73a6d-165">VT_UI8</span><span class="sxs-lookup"><span data-stu-id="73a6d-165">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="73a6d-166">VT_R4</span><span class="sxs-lookup"><span data-stu-id="73a6d-166">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="73a6d-167">VT_R8</span><span class="sxs-lookup"><span data-stu-id="73a6d-167">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="73a6d-168">VT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="73a6d-168">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="73a6d-169">VT_DATE</span><span class="sxs-lookup"><span data-stu-id="73a6d-169">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="73a6d-170">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="73a6d-170">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="73a6d-171">VT_INT</span><span class="sxs-lookup"><span data-stu-id="73a6d-171">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="73a6d-172">VT_UINT</span><span class="sxs-lookup"><span data-stu-id="73a6d-172">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="73a6d-173">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="73a6d-173">**VT_ARRAY**</span></span>|

<span data-ttu-id="73a6d-174">以下代码示例使用前一示例中定义的 `MarshalObject` 接口，演示如何将各种类型的变体传递给 COM 服务器。</span><span class="sxs-lookup"><span data-stu-id="73a6d-174">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

```vb
Dim mo As New MarshalObject()
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.
```

```csharp
MarshalObject mo = new MarshalObject();
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.
```

<span data-ttu-id="73a6d-175">可使用 <xref:System.Runtime.InteropServices.ErrorWrapper>、<xref:System.Runtime.InteropServices.DispatchWrapper>、<xref:System.Runtime.InteropServices.UnknownWrapper> 和 <xref:System.Runtime.InteropServices.CurrencyWrapper> 等包装类封送不具有相应托管类型的 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-175">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="73a6d-176">以下代码示例演示如何使用这些包装类将各种类型的变体传递给 COM 服务器。</span><span class="sxs-lookup"><span data-stu-id="73a6d-176">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

```vb
Imports System.Runtime.InteropServices
' Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(New UnknownWrapper(inew))
' Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(New DispatchWrapper(inew))
' Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(New ErrorWrapper(&H80054002))
' Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))
```

```csharp
using System.Runtime.InteropServices;
// Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(new UnknownWrapper(inew));
// Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(new DispatchWrapper(inew));
// Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(new ErrorWrapper(0x80054002));
// Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));
```

<span data-ttu-id="73a6d-177">包装类在 <xref:System.Runtime.InteropServices> 命名空间中定义。</span><span class="sxs-lookup"><span data-stu-id="73a6d-177">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="73a6d-178">将 IConvertible 接口封送到变体</span><span class="sxs-lookup"><span data-stu-id="73a6d-178">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="73a6d-179">类型（上一节中列出的类型除外）可通过实现 <xref:System.IConvertible> 接口来控制封送处理它们的方式。</span><span class="sxs-lookup"><span data-stu-id="73a6d-179">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="73a6d-180">如果对象实现 IConvertible 接口，则 COM 变体类型将在运行时由从 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> 方法返回的 <xref:System.TypeCode> 枚举值确定。</span><span class="sxs-lookup"><span data-stu-id="73a6d-180">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="73a6d-181">下表显示 TypeCode 枚举可能的值以及每个值相应的 COM 变体类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-181">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="73a6d-182">TypeCode</span><span class="sxs-lookup"><span data-stu-id="73a6d-182">TypeCode</span></span>|<span data-ttu-id="73a6d-183">COM 变体类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-183">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="73a6d-184">TypeCode.Empty</span><span class="sxs-lookup"><span data-stu-id="73a6d-184">**TypeCode.Empty**</span></span>|<span data-ttu-id="73a6d-185">VT_EMPTY</span><span class="sxs-lookup"><span data-stu-id="73a6d-185">**VT_EMPTY**</span></span>|
|<span data-ttu-id="73a6d-186">TypeCode.Object</span><span class="sxs-lookup"><span data-stu-id="73a6d-186">**TypeCode.Object**</span></span>|<span data-ttu-id="73a6d-187">VT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="73a6d-187">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="73a6d-188">TypeCode.DBNull</span><span class="sxs-lookup"><span data-stu-id="73a6d-188">**TypeCode.DBNull**</span></span>|<span data-ttu-id="73a6d-189">VT_NULL</span><span class="sxs-lookup"><span data-stu-id="73a6d-189">**VT_NULL**</span></span>|
|<span data-ttu-id="73a6d-190">TypeCode.Boolean</span><span class="sxs-lookup"><span data-stu-id="73a6d-190">**TypeCode.Boolean**</span></span>|<span data-ttu-id="73a6d-191">VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="73a6d-191">**VT_BOOL**</span></span>|
|<span data-ttu-id="73a6d-192">TypeCode.Char</span><span class="sxs-lookup"><span data-stu-id="73a6d-192">**TypeCode.Char**</span></span>|<span data-ttu-id="73a6d-193">VT_UI2</span><span class="sxs-lookup"><span data-stu-id="73a6d-193">**VT_UI2**</span></span>|
|<span data-ttu-id="73a6d-194">TypeCode.Sbyte</span><span class="sxs-lookup"><span data-stu-id="73a6d-194">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="73a6d-195">VT_I1</span><span class="sxs-lookup"><span data-stu-id="73a6d-195">**VT_I1**</span></span>|
|<span data-ttu-id="73a6d-196">TypeCode.Byte</span><span class="sxs-lookup"><span data-stu-id="73a6d-196">**TypeCode.Byte**</span></span>|<span data-ttu-id="73a6d-197">VT_UI1</span><span class="sxs-lookup"><span data-stu-id="73a6d-197">**VT_UI1**</span></span>|
|<span data-ttu-id="73a6d-198">TypeCode.Int16</span><span class="sxs-lookup"><span data-stu-id="73a6d-198">**TypeCode.Int16**</span></span>|<span data-ttu-id="73a6d-199">VT_I2</span><span class="sxs-lookup"><span data-stu-id="73a6d-199">**VT_I2**</span></span>|
|<span data-ttu-id="73a6d-200">TypeCode.UInt16</span><span class="sxs-lookup"><span data-stu-id="73a6d-200">**TypeCode.UInt16**</span></span>|<span data-ttu-id="73a6d-201">VT_UI2</span><span class="sxs-lookup"><span data-stu-id="73a6d-201">**VT_UI2**</span></span>|
|<span data-ttu-id="73a6d-202">TypeCode.Int32</span><span class="sxs-lookup"><span data-stu-id="73a6d-202">**TypeCode.Int32**</span></span>|<span data-ttu-id="73a6d-203">VT_I4</span><span class="sxs-lookup"><span data-stu-id="73a6d-203">**VT_I4**</span></span>|
|<span data-ttu-id="73a6d-204">TypeCode.UInt32</span><span class="sxs-lookup"><span data-stu-id="73a6d-204">**TypeCode.UInt32**</span></span>|<span data-ttu-id="73a6d-205">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="73a6d-205">**VT_UI4**</span></span>|
|<span data-ttu-id="73a6d-206">TypeCode.Int64</span><span class="sxs-lookup"><span data-stu-id="73a6d-206">**TypeCode.Int64**</span></span>|<span data-ttu-id="73a6d-207">VT_I8</span><span class="sxs-lookup"><span data-stu-id="73a6d-207">**VT_I8**</span></span>|
|<span data-ttu-id="73a6d-208">TypeCode.UInt64</span><span class="sxs-lookup"><span data-stu-id="73a6d-208">**TypeCode.UInt64**</span></span>|<span data-ttu-id="73a6d-209">VT_UI8</span><span class="sxs-lookup"><span data-stu-id="73a6d-209">**VT_UI8**</span></span>|
|<span data-ttu-id="73a6d-210">TypeCode.Single</span><span class="sxs-lookup"><span data-stu-id="73a6d-210">**TypeCode.Single**</span></span>|<span data-ttu-id="73a6d-211">VT_R4</span><span class="sxs-lookup"><span data-stu-id="73a6d-211">**VT_R4**</span></span>|
|<span data-ttu-id="73a6d-212">TypeCode.Double</span><span class="sxs-lookup"><span data-stu-id="73a6d-212">**TypeCode.Double**</span></span>|<span data-ttu-id="73a6d-213">VT_R8</span><span class="sxs-lookup"><span data-stu-id="73a6d-213">**VT_R8**</span></span>|
|<span data-ttu-id="73a6d-214">TypeCode.Decimal</span><span class="sxs-lookup"><span data-stu-id="73a6d-214">**TypeCode.Decimal**</span></span>|<span data-ttu-id="73a6d-215">VT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="73a6d-215">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="73a6d-216">TypeCode.DateTime</span><span class="sxs-lookup"><span data-stu-id="73a6d-216">**TypeCode.DateTime**</span></span>|<span data-ttu-id="73a6d-217">VT_DATE</span><span class="sxs-lookup"><span data-stu-id="73a6d-217">**VT_DATE**</span></span>|
|<span data-ttu-id="73a6d-218">TypeCode.String</span><span class="sxs-lookup"><span data-stu-id="73a6d-218">**TypeCode.String**</span></span>|<span data-ttu-id="73a6d-219">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="73a6d-219">**VT_BSTR**</span></span>|
|<span data-ttu-id="73a6d-220">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-220">Not supported.</span></span>|<span data-ttu-id="73a6d-221">VT_INT</span><span class="sxs-lookup"><span data-stu-id="73a6d-221">**VT_INT**</span></span>|
|<span data-ttu-id="73a6d-222">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-222">Not supported.</span></span>|<span data-ttu-id="73a6d-223">VT_UINT</span><span class="sxs-lookup"><span data-stu-id="73a6d-223">**VT_UINT**</span></span>|
|<span data-ttu-id="73a6d-224">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-224">Not supported.</span></span>|<span data-ttu-id="73a6d-225">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="73a6d-225">**VT_ARRAY**</span></span>|
|<span data-ttu-id="73a6d-226">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-226">Not supported.</span></span>|<span data-ttu-id="73a6d-227">VT_RECORD</span><span class="sxs-lookup"><span data-stu-id="73a6d-227">**VT_RECORD**</span></span>|
|<span data-ttu-id="73a6d-228">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-228">Not supported.</span></span>|<span data-ttu-id="73a6d-229">VT_CY</span><span class="sxs-lookup"><span data-stu-id="73a6d-229">**VT_CY**</span></span>|
|<span data-ttu-id="73a6d-230">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-230">Not supported.</span></span>|<span data-ttu-id="73a6d-231">VT_VARIANT</span><span class="sxs-lookup"><span data-stu-id="73a6d-231">**VT_VARIANT**</span></span>|

<span data-ttu-id="73a6d-232">通过调用 IConvertible.To Type 接口确定 COM 变体的值，其中 To Type 是转换例程，它对应于从 IConvertible.GetTypeCode 返回的类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-232">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="73a6d-233">例如，将从 IConvertible.GetTypeCode 返回 TypeCode.Double 的对象作为 VT_R8 类型的 COM 变体封送  。</span><span class="sxs-lookup"><span data-stu-id="73a6d-233">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="73a6d-234">通过强制转换为 IConvertible 接口并调用 <xref:System.IConvertible.ToDouble%2A> 方法，可获取变体值（存储在 COM 变体的 dblVal 字段中） 。</span><span class="sxs-lookup"><span data-stu-id="73a6d-234">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="73a6d-235">将变体封送到对象</span><span class="sxs-lookup"><span data-stu-id="73a6d-235">Marshaling Variant to Object</span></span>

<span data-ttu-id="73a6d-236">将变体封送到对象时，所封送变体的类型（有时是值）确定生成的对象类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-236">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="73a6d-237">下表标识每个变体类型以及变体从 COM 传递给 .NET Framework 时封送拆收器所创建的相应对象类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-237">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="73a6d-238">COM 变体类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-238">COM variant type</span></span>|<span data-ttu-id="73a6d-239">对象类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-239">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="73a6d-240">VT_EMPTY</span><span class="sxs-lookup"><span data-stu-id="73a6d-240">**VT_EMPTY**</span></span>|<span data-ttu-id="73a6d-241">Null 对象引用（在 Visual Basic 中为 Nothing）。</span><span class="sxs-lookup"><span data-stu-id="73a6d-241">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="73a6d-242">VT_NULL</span><span class="sxs-lookup"><span data-stu-id="73a6d-242">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-243">VT_DISPATCH</span><span class="sxs-lookup"><span data-stu-id="73a6d-243">**VT_DISPATCH**</span></span>|<span data-ttu-id="73a6d-244">System.__ComObject；如果 (pdispVal == null)，则为 null</span><span class="sxs-lookup"><span data-stu-id="73a6d-244">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="73a6d-245">VT_UNKNOWN</span><span class="sxs-lookup"><span data-stu-id="73a6d-245">**VT_UNKNOWN**</span></span>|<span data-ttu-id="73a6d-246">System.__ComObject；如果 (punkVal == null)，则为 null</span><span class="sxs-lookup"><span data-stu-id="73a6d-246">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="73a6d-247">VT_ERROR</span><span class="sxs-lookup"><span data-stu-id="73a6d-247">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-248">VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="73a6d-248">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-249">VT_I1</span><span class="sxs-lookup"><span data-stu-id="73a6d-249">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-250">VT_UI1</span><span class="sxs-lookup"><span data-stu-id="73a6d-250">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-251">VT_I2</span><span class="sxs-lookup"><span data-stu-id="73a6d-251">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-252">VT_UI2</span><span class="sxs-lookup"><span data-stu-id="73a6d-252">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-253">VT_I4</span><span class="sxs-lookup"><span data-stu-id="73a6d-253">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-254">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="73a6d-254">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-255">VT_I8</span><span class="sxs-lookup"><span data-stu-id="73a6d-255">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-256">VT_UI8</span><span class="sxs-lookup"><span data-stu-id="73a6d-256">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-257">VT_R4</span><span class="sxs-lookup"><span data-stu-id="73a6d-257">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-258">VT_R8</span><span class="sxs-lookup"><span data-stu-id="73a6d-258">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-259">VT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="73a6d-259">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-260">VT_DATE</span><span class="sxs-lookup"><span data-stu-id="73a6d-260">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-261">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="73a6d-261">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-262">VT_INT</span><span class="sxs-lookup"><span data-stu-id="73a6d-262">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-263">VT_UINT</span><span class="sxs-lookup"><span data-stu-id="73a6d-263">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-264">**VT_ARRAY** &#124; **VT_** \*</span><span class="sxs-lookup"><span data-stu-id="73a6d-264">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-265">VT_CY</span><span class="sxs-lookup"><span data-stu-id="73a6d-265">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="73a6d-266">VT_RECORD</span><span class="sxs-lookup"><span data-stu-id="73a6d-266">**VT_RECORD**</span></span>|<span data-ttu-id="73a6d-267">对应装箱的值类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-267">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="73a6d-268">VT_VARIANT</span><span class="sxs-lookup"><span data-stu-id="73a6d-268">**VT_VARIANT**</span></span>|<span data-ttu-id="73a6d-269">不支持。</span><span class="sxs-lookup"><span data-stu-id="73a6d-269">Not supported.</span></span>|

<span data-ttu-id="73a6d-270">变体类型从 COM 传递给托管代码、再传回 COM，这样的变体类型在调用期间可能不会保留同一变体类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-270">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="73a6d-271">请考虑将 VT_DISPATCH 类型的变体从 COM 传递到 .NET Framework 时会发生的情况。</span><span class="sxs-lookup"><span data-stu-id="73a6d-271">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="73a6d-272">在封送处理期间，变体转换为 <xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="73a6d-272">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73a6d-273">如果随后对象传回 COM，则将它封送回 VT_UNKNOWN 类型的变体 。</span><span class="sxs-lookup"><span data-stu-id="73a6d-273">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="73a6d-274">将对象从托管代码封送到 COM 时，无法保证产生的变体与最初用于产生该对象的变体为同一类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-274">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="73a6d-275">封送 ByRef 变体</span><span class="sxs-lookup"><span data-stu-id="73a6d-275">Marshaling ByRef Variants</span></span>

<span data-ttu-id="73a6d-276">虽然变体本身可以按值或按引用传递，但 VT_BYREF 标志也可用于任何变体类型，指示变体的内容按引用传递，而不是按值传递。</span><span class="sxs-lookup"><span data-stu-id="73a6d-276">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="73a6d-277">对于按引用封送变体与使用设置的 VT_BYREF 标志封送变体，人们容易混淆这二者之间的差异。</span><span class="sxs-lookup"><span data-stu-id="73a6d-277">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="73a6d-278">下图阐明了这些差异：</span><span class="sxs-lookup"><span data-stu-id="73a6d-278">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="73a6d-279">![显示在堆栈上传递的变量的图表。](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="73a6d-279">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="73a6d-280">按值和按引用传递的变体</span><span class="sxs-lookup"><span data-stu-id="73a6d-280">Variants passed by value and by reference</span></span>

<span data-ttu-id="73a6d-281">**值封送对象和变体的默认行为**</span><span class="sxs-lookup"><span data-stu-id="73a6d-281">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="73a6d-282">将对象从托管代码传递给 COM 时，使用在[将对象封送到变体](#marshaling-object-to-variant)中定义的规则，将对象内容复制到封送拆收器创建的新变体中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-282">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="73a6d-283">对非托管端的变体所做的更改不会在从调用返回时传回起始对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-283">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="73a6d-284">将变体从 COM 传递给托管代码时，使用[将变体封送到对象](#marshaling-variant-to-object)中定义的规则，将变体内容复制到新创建的对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-284">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="73a6d-285">对托管端的对象所做的更改不会在从调用返回时传回起始变体。</span><span class="sxs-lookup"><span data-stu-id="73a6d-285">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="73a6d-286">**按引用封送对象和变体的默认行为**</span><span class="sxs-lookup"><span data-stu-id="73a6d-286">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="73a6d-287">要将更改传回调用方，必须按引用传递参数。</span><span class="sxs-lookup"><span data-stu-id="73a6d-287">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="73a6d-288">例如，可使用 C# 中的 ref 关键字（或 Visual Basic 托管代码中的 ByRef），按引用传递参数 。</span><span class="sxs-lookup"><span data-stu-id="73a6d-288">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="73a6d-289">在 COM 中，使用指针（例如 variant \*）传递引用参数。</span><span class="sxs-lookup"><span data-stu-id="73a6d-289">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="73a6d-290">将对象按引用传递给 COM 时，封送拆收器创建一个新变体，并在调用前将对象引用内容复制到变体中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-290">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="73a6d-291">变体被传递给未托管的函数，用户可在其中随意更改变体的内容。</span><span class="sxs-lookup"><span data-stu-id="73a6d-291">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="73a6d-292">从调用返回时，对非托管端的变体所做的更改会传回起始对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-292">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="73a6d-293">如果变体类型与传递给调用的变体类型不同，则更改会传回另一类型的对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-293">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="73a6d-294">也就是说，传递给调用的对象类型可以不同于从调用返回的对象类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-294">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="73a6d-295">按引用将变体传递给托管代码时，封送拆收器创建一个新对象，并在调用前将变体内容复制到对象中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-295">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="73a6d-296">对对象的引用被传递给托管函数，用户可在其中随意更改该对象。</span><span class="sxs-lookup"><span data-stu-id="73a6d-296">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="73a6d-297">从调用返回时，对引用的对象所做的任何更改都将传回起始变体。</span><span class="sxs-lookup"><span data-stu-id="73a6d-297">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="73a6d-298">如果对象类型与传入调用的对象类型不同，则起始变体的类型发生更改，值传回变体中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-298">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="73a6d-299">同样，传入调用的变体类型可以不同于从调用返回的变体类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-299">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="73a6d-300">**使用设置的 VT_BYREF 标志封送变体的默认行为**</span><span class="sxs-lookup"><span data-stu-id="73a6d-300">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="73a6d-301">按值传递给托管代码的变体可设置 VT_BYREF 标志，用于指示该变体包含引用而不是值。</span><span class="sxs-lookup"><span data-stu-id="73a6d-301">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="73a6d-302">在这种情况下，仍会将变体封送到对象，因为变体是按值传递的。</span><span class="sxs-lookup"><span data-stu-id="73a6d-302">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="73a6d-303">封送拆收器自动取消对变体内容的引用，并在调用前将其复制到新创建的对象中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-303">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="73a6d-304">然后，将对象传入托管函数中；但是，在从调用返回时，不会将该对象传回起始变体中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-304">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="73a6d-305">对托管对象所做的更改丢失。</span><span class="sxs-lookup"><span data-stu-id="73a6d-305">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="73a6d-306">即使变体设置了 VT_BYREF 标志，也无法更改按值传递的变体的值。</span><span class="sxs-lookup"><span data-stu-id="73a6d-306">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="73a6d-307">按引用传递给托管代码的变体也可设置 VT_BYREF 标志，用于指示该变体包含另一个引用。</span><span class="sxs-lookup"><span data-stu-id="73a6d-307">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="73a6d-308">如果采用此做法，则会将该变体封送到 ref 对象，因为变体是按引用传递的。</span><span class="sxs-lookup"><span data-stu-id="73a6d-308">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="73a6d-309">封送拆收器自动取消对变体内容的引用，并在调用前将其复制到新创建的对象中。</span><span class="sxs-lookup"><span data-stu-id="73a6d-309">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="73a6d-310">从调用返回时，仅当对象与传入的对象是同一类型时，才会将对象的值传回起始变体内的引用。</span><span class="sxs-lookup"><span data-stu-id="73a6d-310">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="73a6d-311">也就是说，传播不会更改设置了 VT_BYREF 标志的变体的类型。</span><span class="sxs-lookup"><span data-stu-id="73a6d-311">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="73a6d-312">如果在调用期间对象类型发生变化，则在从调用返回时将发生 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="73a6d-312">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="73a6d-313">下表总结了变体和对象的传播规则。</span><span class="sxs-lookup"><span data-stu-id="73a6d-313">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="73a6d-314">From</span><span class="sxs-lookup"><span data-stu-id="73a6d-314">From</span></span>|<span data-ttu-id="73a6d-315">功能</span><span class="sxs-lookup"><span data-stu-id="73a6d-315">To</span></span>|<span data-ttu-id="73a6d-316">传回的更改</span><span class="sxs-lookup"><span data-stu-id="73a6d-316">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="73a6d-317">变体  v</span><span class="sxs-lookup"><span data-stu-id="73a6d-317">**Variant**  *v*</span></span>|<span data-ttu-id="73a6d-318">对象  o</span><span class="sxs-lookup"><span data-stu-id="73a6d-318">**Object**  *o*</span></span>|<span data-ttu-id="73a6d-319">Never</span><span class="sxs-lookup"><span data-stu-id="73a6d-319">Never</span></span>|
|<span data-ttu-id="73a6d-320">对象  o</span><span class="sxs-lookup"><span data-stu-id="73a6d-320">**Object**  *o*</span></span>|<span data-ttu-id="73a6d-321">变体  v</span><span class="sxs-lookup"><span data-stu-id="73a6d-321">**Variant**  *v*</span></span>|<span data-ttu-id="73a6d-322">Never</span><span class="sxs-lookup"><span data-stu-id="73a6d-322">Never</span></span>|
|<span data-ttu-id="73a6d-323">变体   \*  pv</span><span class="sxs-lookup"><span data-stu-id="73a6d-323">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="73a6d-324">Ref 对象  o</span><span class="sxs-lookup"><span data-stu-id="73a6d-324">**Ref Object**  *o*</span></span>|<span data-ttu-id="73a6d-325">Always</span><span class="sxs-lookup"><span data-stu-id="73a6d-325">Always</span></span>|
|<span data-ttu-id="73a6d-326">Ref 对象  o</span><span class="sxs-lookup"><span data-stu-id="73a6d-326">**Ref object**  *o*</span></span>|<span data-ttu-id="73a6d-327">变体   \*  pv</span><span class="sxs-lookup"><span data-stu-id="73a6d-327">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="73a6d-328">Always</span><span class="sxs-lookup"><span data-stu-id="73a6d-328">Always</span></span>|
|<span data-ttu-id="73a6d-329">变体  v (VT_BYREF &#124; VT_\*)</span><span class="sxs-lookup"><span data-stu-id="73a6d-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="73a6d-330">对象  o</span><span class="sxs-lookup"><span data-stu-id="73a6d-330">**Object**  *o*</span></span>|<span data-ttu-id="73a6d-331">Never</span><span class="sxs-lookup"><span data-stu-id="73a6d-331">Never</span></span>|
|<span data-ttu-id="73a6d-332">变体  v (VT_BYREF &#124; VT_)</span><span class="sxs-lookup"><span data-stu-id="73a6d-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="73a6d-333">Ref 对象  o</span><span class="sxs-lookup"><span data-stu-id="73a6d-333">**Ref Object**  *o*</span></span>|<span data-ttu-id="73a6d-334">仅类型未发生更改时。</span><span class="sxs-lookup"><span data-stu-id="73a6d-334">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="73a6d-335">请参阅</span><span class="sxs-lookup"><span data-stu-id="73a6d-335">See also</span></span>

- [<span data-ttu-id="73a6d-336">默认封送处理行为</span><span class="sxs-lookup"><span data-stu-id="73a6d-336">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="73a6d-337">可直接复制到本机结构中的类型和非直接复制到本机结构中的类型</span><span class="sxs-lookup"><span data-stu-id="73a6d-337">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="73a6d-338">[方向特性](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="73a6d-338">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="73a6d-339">复制和锁定</span><span class="sxs-lookup"><span data-stu-id="73a6d-339">Copying and Pinning</span></span>](copying-and-pinning.md)
