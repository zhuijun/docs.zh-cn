---
title: 有选择的序列化
description: 本文介绍如何用 NonSerialized 属性标记字段，这会阻止字段被序列化。
ms.date: 08/07/2017
dev_langs:
- CSharp
helpviewer_keywords:
- serialization, selective serialization
- binary serialization, selective serialization
ms.assetid: 39c56635-95d2-4afd-aff1-b022e7649bb3
ms.openlocfilehash: c7203c4ea13c65f8d88c55de96988d3b1d9e9611
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379166"
---
# <a name="selective-serialization"></a><span data-ttu-id="a0d4d-103">有选择的序列化</span><span class="sxs-lookup"><span data-stu-id="a0d4d-103">Selective serialization</span></span>
<span data-ttu-id="a0d4d-104">类通常包含不应进行序列化的字段。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-104">A class often contains fields that shouldn't be serialized.</span></span> <span data-ttu-id="a0d4d-105">例如，假定类将线程 ID 存储在成员变量中。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-105">For example, assume a class stores a thread ID in a member variable.</span></span> <span data-ttu-id="a0d4d-106">如果反序列化该类，而在对该类进行序列化时，存储了该 ID 的线程可能不再运行。因此，序列化该值毫无意义。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-106">When the class is deserialized, the thread stored the ID for when the class was serialized might no longer be running; so serializing this value doesn't make sense.</span></span> <span data-ttu-id="a0d4d-107">按如下方法使用 [NonSerialized](xref:System.NonSerializedAttribute) 属性标记成员变量，可防止其被序列化。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-107">You can prevent member variables from being serialized by marking them with the [NonSerialized](xref:System.NonSerializedAttribute) attribute as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject
{  
  public int n1;  
  [NonSerialized] public int n2;  
  public String str;  
}  
```

<span data-ttu-id="a0d4d-108">如有可能，应使可能包含安全敏感数据的对象不可序列化。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-108">If possible, make an object that could contain security-sensitive data nonserializable.</span></span> <span data-ttu-id="a0d4d-109">如果必须序列化该对象，则可将 `NonSerialized` 属性应用于存储敏感数据的特定字段。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-109">If the object must be serialized, apply the `NonSerialized` attribute to specific fields that store sensitive data.</span></span> <span data-ttu-id="a0d4d-110">如果没有将这些字段排除在序列化之外，应该注意字段存储的数据会向有权序列化的所有代码公开。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-110">If you don't exclude these fields from serialization, be aware that the data they store are exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="a0d4d-111">有关编写安全的序列化代码的详细信息，请参阅[安全和序列化](../../../docs/framework/misc/security-and-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d4d-111">For more information about writing secure serialization code, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="a0d4d-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="a0d4d-112">See also</span></span>

- [<span data-ttu-id="a0d4d-113">二进制序列化</span><span class="sxs-lookup"><span data-stu-id="a0d4d-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="a0d4d-114">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="a0d4d-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="a0d4d-115">安全性和序列化</span><span class="sxs-lookup"><span data-stu-id="a0d4d-115">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
