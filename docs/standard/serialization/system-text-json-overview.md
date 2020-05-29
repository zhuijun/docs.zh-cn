---
title: 使用 C# 对 JSON 进行序列化和反序列化 - .NET
description: 本概述介绍了在 .NET 中对 JSON 进行序列化和反序列化的 System.Text.Json 命名空间功能。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380128"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="a5cd7-103">.NET 中的 JSON 序列化和反序列化（封送和拆收）- 概述</span><span class="sxs-lookup"><span data-stu-id="a5cd7-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="a5cd7-104">`System.Text.Json` 命名空间提供用于序列化和反序列化 JavaScript 对象表示法 (JSON) 的功能。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="a5cd7-105">库的设计强调对广泛的功能集实现高性能和低内存分配。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="a5cd7-106">内置的 UTF-8 支持可优化读写以 UTF-8 编码的 JSON 文本的过程，UTF-8 编码是针对 Web 上的数据和磁盘上的文件的最普遍的编码方式。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="a5cd7-107">库还提供了用于处理内存中文档对象模型 (DOM) 的类。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="a5cd7-108">此功能允许对 JSON 文件或字符串中的元素进行随机只读访问。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="a5cd7-109">如何获取库</span><span class="sxs-lookup"><span data-stu-id="a5cd7-109">How to get the library</span></span>

* <span data-ttu-id="a5cd7-110">该库是作为 [.NET Core 3.0](https://aka.ms/netcore3download) 共享框架的一部分内置的。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-110">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="a5cd7-111">对于其他目标框架，请安装 [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="a5cd7-111">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="a5cd7-112">包支持以下框架：</span><span class="sxs-lookup"><span data-stu-id="a5cd7-112">The package supports:</span></span>
  * <span data-ttu-id="a5cd7-113">.NET Standard 2.0 及更高版本</span><span class="sxs-lookup"><span data-stu-id="a5cd7-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="a5cd7-114">.NET Framework 4.7.2 及更高版本</span><span class="sxs-lookup"><span data-stu-id="a5cd7-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="a5cd7-115">.NET Core 2.0、2.1 和 2.2</span><span class="sxs-lookup"><span data-stu-id="a5cd7-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a5cd7-116">其他资源</span><span class="sxs-lookup"><span data-stu-id="a5cd7-116">Additional resources</span></span>

* [<span data-ttu-id="a5cd7-117">如何使用库</span><span class="sxs-lookup"><span data-stu-id="a5cd7-117">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="a5cd7-118">[如何从 Newtonsoft.Json 迁移](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="a5cd7-118">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="a5cd7-119">如何编写转换器</span><span class="sxs-lookup"><span data-stu-id="a5cd7-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="a5cd7-120">[System.Text.Json 源代码](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a5cd7-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="a5cd7-121">[System.Text.Json API 参考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a5cd7-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="a5cd7-122">[System.Text.Json.Serialization API 参考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="a5cd7-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
