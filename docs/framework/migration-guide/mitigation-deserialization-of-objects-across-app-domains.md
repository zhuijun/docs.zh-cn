---
title: 缓解：跨应用程序域的对象的反序列化
description: 了解如何诊断和缓解尝试跨应用域反序列化逻辑调用上下文中的对象时引发异常的问题。
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: 20ea0f2f0b49000b7d1993adb583a803d9f5be6c
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475237"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="632a7-103">缓解：跨应用程序域的对象反序列化</span><span class="sxs-lookup"><span data-stu-id="632a7-103">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="632a7-104">有时，当一个应用程序使用具有不同应用程序基的两个或多个应用程序域时，如果尝试跨应用程序域在逻辑调用上下文中反序列化对象，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="632a7-104">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="632a7-105">诊断问题</span><span class="sxs-lookup"><span data-stu-id="632a7-105">Diagnosing the issue</span></span>  
 <span data-ttu-id="632a7-106">以下情况将会引发这一问题：</span><span class="sxs-lookup"><span data-stu-id="632a7-106">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="632a7-107">一个应用程序使用具有不同应用程序基的两个或多个应用程序域。</span><span class="sxs-lookup"><span data-stu-id="632a7-107">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="632a7-108">通过调用 <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> 或 <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> 等方法将某些类型明确添加到 <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="632a7-108">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="632a7-109">这些类型未标记为可序列化并且未存储在全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="632a7-109">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="632a7-110">之后，在非默认应用程序域中运行的代码尝试从配置文件中读取值，或者使用 XML 来反序列化对象。</span><span class="sxs-lookup"><span data-stu-id="632a7-110">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="632a7-111">为了从配置文件中读取值或反序列化对象，<xref:System.Xml.XmlReader> 对象尝试访问配置系统。</span><span class="sxs-lookup"><span data-stu-id="632a7-111">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="632a7-112">如果配置系统尚未初始化，则必须完成其初始化。</span><span class="sxs-lookup"><span data-stu-id="632a7-112">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="632a7-113">这意味着，运行时环境还必须为配置系统创建稳定的路径，它的作用如下：</span><span class="sxs-lookup"><span data-stu-id="632a7-113">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1. <span data-ttu-id="632a7-114">查找非默认应用程序域的证据。</span><span class="sxs-lookup"><span data-stu-id="632a7-114">It looks for evidence for the non-default app domain.</span></span>  
  
    2. <span data-ttu-id="632a7-115">尝试根据默认应用程序域计算非默认应用程序域的证据。</span><span class="sxs-lookup"><span data-stu-id="632a7-115">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3. <span data-ttu-id="632a7-116">为获取默认应用程序域证据而进行的调用，会触发从非默认应用程序域到默认应用程序域的跨应用程序域调用。</span><span class="sxs-lookup"><span data-stu-id="632a7-116">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4. <span data-ttu-id="632a7-117">作为 .NET Framework 中跨应用程序域协定的一部分，逻辑调用上下文的内容必须跨应用程序域边界进行封送。</span><span class="sxs-lookup"><span data-stu-id="632a7-117">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="632a7-118">由于逻辑调用上下文中的类型不能在默认应用程序域中解析，因此将会引发异常。</span><span class="sxs-lookup"><span data-stu-id="632a7-118">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="632a7-119">缓解</span><span class="sxs-lookup"><span data-stu-id="632a7-119">Mitigation</span></span>  
 <span data-ttu-id="632a7-120">若要解决此问题，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="632a7-120">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="632a7-121">当引发异常时，查找调用堆栈中对 `get_Evidence` 的调用。</span><span class="sxs-lookup"><span data-stu-id="632a7-121">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="632a7-122">这个异常可以是异常集中的任何一个大子集，包括 <xref:System.IO.FileNotFoundException> 和 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="632a7-122">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="632a7-123">识别应用程序中没有向逻辑调用上下文添加应用程序的位置，然后添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="632a7-123">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a><span data-ttu-id="632a7-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="632a7-124">See also</span></span>

- [<span data-ttu-id="632a7-125">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="632a7-125">Application compatibility</span></span>](application-compatibility.md)
