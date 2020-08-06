---
title: 安全和序列化
description: 阅读安全和序列化。 使用带有指定的 SerializationFormatter 标志的 SecurityPermission 来查看或修改对象实例数据。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 393e334e8165f55812681848070929bdfb03a2a5
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855681"
---
# <a name="security-and-serialization"></a><span data-ttu-id="75cba-104">安全和序列化</span><span class="sxs-lookup"><span data-stu-id="75cba-104">Security and serialization</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="75cba-105">由于序列化可以允许其他代码查看或修改在其他情况下无法访问的对象实例数据，因此执行序列化的代码需要具有特殊的权限：带有指定 <xref:System.Security.Permissions.SecurityPermission> 标志的 <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> 。</span><span class="sxs-lookup"><span data-stu-id="75cba-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="75cba-106">在默认策略下，通过 Internet 下载的代码或 Intranet 代码不会授予该权限；只有本地计算机上的代码才被授予该权限。</span><span class="sxs-lookup"><span data-stu-id="75cba-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="75cba-107">通常，对象实例的所有字段都会被序列化，这意味着数据会被表示为实例的序列化数据。</span><span class="sxs-lookup"><span data-stu-id="75cba-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="75cba-108">能够解释格式的代码有可能能够确定这些数据的值，而不依赖于该成员的可访问性。</span><span class="sxs-lookup"><span data-stu-id="75cba-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="75cba-109">类似地，反序列化从序列化的表示形式中提取数据，并直接设置对象状态，这也与可访问性规则无关。</span><span class="sxs-lookup"><span data-stu-id="75cba-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="75cba-110">对于任何可能包含安全性敏感数据的对象，如果可能，都应该使该对象不可序列化。</span><span class="sxs-lookup"><span data-stu-id="75cba-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="75cba-111">如果它必须为可序列化的，请尝试生成特定字段来保存不可序列化的重要数据。</span><span class="sxs-lookup"><span data-stu-id="75cba-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="75cba-112">如果无法将这些字段不可序列化，则会向有权序列化的任何代码公开敏感数据。</span><span class="sxs-lookup"><span data-stu-id="75cba-112">If those fields cannot be made nonserializable, the sensitive data will be exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="75cba-113">请确保没有任何恶意代码可以获取此权限。</span><span class="sxs-lookup"><span data-stu-id="75cba-113">Make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="75cba-114"><xref:System.Runtime.Serialization.ISerializable> 接口只适合由序列化基础结构使用。</span><span class="sxs-lookup"><span data-stu-id="75cba-114">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="75cba-115">然而，如果该接口未受到保护，则可能会漏露敏感信息。</span><span class="sxs-lookup"><span data-stu-id="75cba-115">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="75cba-116">如果通过实现 **ISerializable**来提供自定义序列化，请确保采取以下预防措施：</span><span class="sxs-lookup"><span data-stu-id="75cba-116">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="75cba-117">应通过如下方法显式保护 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法的安全：要求为 **SecurityPermission** 指定 **SerializationFormatter** 权限，或确保不会在方法输出中泄露敏感信息。</span><span class="sxs-lookup"><span data-stu-id="75cba-117">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="75cba-118">例如：</span><span class="sxs-lookup"><span data-stu-id="75cba-118">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- <span data-ttu-id="75cba-119">用于序列化的特殊构造函数也应当进行彻底的输入验证，并且应当受到保护或者成为私有函数，以帮助防范恶意代码的滥用行为。</span><span class="sxs-lookup"><span data-stu-id="75cba-119">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="75cba-120">构造函数应当实施与通过任何其他方式获取这样的类的实例（例如，通过某种工厂显式创建或间接创建该类）时所需要的相同的安全检查和权限。</span><span class="sxs-lookup"><span data-stu-id="75cba-120">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75cba-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75cba-121">See also</span></span>

- [<span data-ttu-id="75cba-122">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="75cba-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
