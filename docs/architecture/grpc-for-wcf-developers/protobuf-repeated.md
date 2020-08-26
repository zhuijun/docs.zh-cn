---
title: 列表和数组的重复字段-gRPC for WCF 开发人员
description: 了解 Protobuf 如何处理集合及其与 .NET 集合之间的关系。
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867498"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="c8bb0-103">列表和数组的重复字段</span><span class="sxs-lookup"><span data-stu-id="c8bb0-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="c8bb0-104">使用 prefix 关键字在协议缓冲区 (Protobuf) 中指定列表 `repeated` 。</span><span class="sxs-lookup"><span data-stu-id="c8bb0-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="c8bb0-105">下面的示例演示如何创建列表：</span><span class="sxs-lookup"><span data-stu-id="c8bb0-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="c8bb0-106">在生成的代码中， `repeated` 字段由类型的只读属性 [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] （而不是任何内置 .net 集合类型）表示。</span><span class="sxs-lookup"><span data-stu-id="c8bb0-106">In the generated code, `repeated` fields are represented by read-only properties of the [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="c8bb0-107">此类型实现所有标准 .NET 集合接口，例如 <xref:System.Collections.Generic.IList%601> 和 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="c8bb0-107">This type implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="c8bb0-108">因此，您可以使用 LINQ 查询或轻松地将其转换为数组或列表。</span><span class="sxs-lookup"><span data-stu-id="c8bb0-108">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

<span data-ttu-id="c8bb0-109">`RepeatedField<T>`类型包括将列表序列化和反序列化为二进制线路格式所需的代码。</span><span class="sxs-lookup"><span data-stu-id="c8bb0-109">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span>

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
><span data-ttu-id="c8bb0-110">[上一页](protobuf-nested-types.md)
>[下一页](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="c8bb0-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
