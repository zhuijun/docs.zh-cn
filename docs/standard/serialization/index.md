---
title: 序列化 - .NET
description: 本文介绍有关 .NET 序列化技术的信息，包括二进制序列化、XML 和 SOAP 序列化以及 JSON 序列化。
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "85840270"
---
# <a name="serialization-in-net"></a><span data-ttu-id="f520c-103">.NET 中的序列化</span><span class="sxs-lookup"><span data-stu-id="f520c-103">Serialization in .NET</span></span>

<span data-ttu-id="f520c-104">序列化是将对象状态转换为可保持或传输的形式的过程。</span><span class="sxs-lookup"><span data-stu-id="f520c-104">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="f520c-105">序列化的补集是反序列化，后者将流转换为对象。</span><span class="sxs-lookup"><span data-stu-id="f520c-105">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="f520c-106">这两个过程一起保证能够存储和传输数据。</span><span class="sxs-lookup"><span data-stu-id="f520c-106">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="f520c-107">.NET 具有以下序列化技术：</span><span class="sxs-lookup"><span data-stu-id="f520c-107">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="f520c-108">[二进制序列化](binary-serialization.md)保持类型保真，这对于多次调用应用程序时保持对象状态非常有用。</span><span class="sxs-lookup"><span data-stu-id="f520c-108">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="f520c-109">例如，通过将对象序列化到剪贴板，可在不同的应用程序之间共享对象。</span><span class="sxs-lookup"><span data-stu-id="f520c-109">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="f520c-110">您可以将对象序列化到流、磁盘、内存和网络等。</span><span class="sxs-lookup"><span data-stu-id="f520c-110">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="f520c-111">远程处理使用序列化，“按值”在计算机或应用程序域之间传递对象。</span><span class="sxs-lookup"><span data-stu-id="f520c-111">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="f520c-112">[XML 和 SOAP 序列化](xml-and-soap-serialization.md)只序列化公共属性和字段，并且不保持类型保真。</span><span class="sxs-lookup"><span data-stu-id="f520c-112">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="f520c-113">当您希望提供或使用数据而不限制使用该数据的应用程序时，这一点非常有用。</span><span class="sxs-lookup"><span data-stu-id="f520c-113">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="f520c-114">由于 XML 是开放式的标准，因此它对于通过 Web 共享数据来说是一个理想选择。</span><span class="sxs-lookup"><span data-stu-id="f520c-114">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="f520c-115">SOAP 同样是开放式的标准，这使它也成为一个理想选择。</span><span class="sxs-lookup"><span data-stu-id="f520c-115">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="f520c-116">[JSON 序列化](system-text-json-overview.md)只序列化公共属性，并且不保持类型保真。</span><span class="sxs-lookup"><span data-stu-id="f520c-116">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="f520c-117">JSON 是开放式的标准，对于通过 Web 共享数据来说是一个理想选择。</span><span class="sxs-lookup"><span data-stu-id="f520c-117">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="f520c-118">参考</span><span class="sxs-lookup"><span data-stu-id="f520c-118">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="f520c-119">包含可用于序列化和反序列化对象的类。</span><span class="sxs-lookup"><span data-stu-id="f520c-119">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="f520c-120">包含可用于将对象序列化为 XML 格式的文档或流的类。</span><span class="sxs-lookup"><span data-stu-id="f520c-120">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="f520c-121">包含可用于将对象序列化为 JSON 格式的文档或流的类。</span><span class="sxs-lookup"><span data-stu-id="f520c-121">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
