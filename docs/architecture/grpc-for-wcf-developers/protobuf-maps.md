---
title: 用于字典的 Protobuf 映射-适用于 WCF 开发人员的 gRPC
description: 了解如何使用 Protobuf 映射来表示 .NET 中的字典类型。
ms.date: 09/09/2019
ms.openlocfilehash: 2c2ae76d47b2309227d22235b5acbe2afa794158
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867460"
---
# <a name="protobuf-maps-for-dictionaries"></a>词典的 Protobuf 映射

可以在消息中表示命名值的任意集合，这一点很重要。 在 .NET 中，这通常通过字典类型来处理。 协议缓冲区中的 .NET 类型的等效项 <xref:System.Collections.Generic.IDictionary%602> (Protobuf) 为 `map<key_type, value_type>` 类型。 本部分演示如何 `map` 在 Protobuf 中声明类型，以及如何使用生成的代码。

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

在生成的代码中， `map` 字段由类型的只读属性表示 [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] 。 此类型实现标准 .NET 集合接口，包括 <xref:System.Collections.Generic.IDictionary%602> 。

映射字段不能直接在消息定义中重复。 但你可以创建一个包含映射的嵌套消息，并 `repeated` 在消息类型上使用，如以下示例中所示：

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>在代码中使用 MapField 属性

`MapField`从字段生成的 `map` 属性是只读的，并且永远不会是 `null` 。 若要设置地图属性，请对 `Add(IDictionary<TKey,TValue> values)` 空属性使用方法 `MapField` 以从任何 .net 字典复制值。

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>延伸阅读

有关 Protobuf 的详细信息，请参阅官方 [Protobuf 文档](https://developers.google.com/protocol-buffers/docs/overview)。

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
>[上一页](protobuf-enums.md)
>[下一页](wcf-services-to-grpc-comparison.md)
