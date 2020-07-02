---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619856"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="f6869-101">MEF 目录实现 IEnumerable，因此不能再用于创建序列化程序</span><span class="sxs-lookup"><span data-stu-id="f6869-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="f6869-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f6869-102">Details</span></span>

<span data-ttu-id="f6869-103">从 .NET Framework 4.5 开始，MEF 目录实现 IEnumerable，因此不能再用于创建序列化程序（<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 对象）。</span><span class="sxs-lookup"><span data-stu-id="f6869-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="f6869-104">尝试对 MEF 目录进行序列化会引发异常。</span><span class="sxs-lookup"><span data-stu-id="f6869-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f6869-105">建议</span><span class="sxs-lookup"><span data-stu-id="f6869-105">Suggestion</span></span>

<span data-ttu-id="f6869-106">不能再使用 MEF 创建序列化程序</span><span class="sxs-lookup"><span data-stu-id="f6869-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="f6869-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="f6869-107">Name</span></span>    | <span data-ttu-id="f6869-108">“值”</span><span class="sxs-lookup"><span data-stu-id="f6869-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f6869-109">范围</span><span class="sxs-lookup"><span data-stu-id="f6869-109">Scope</span></span>   |<span data-ttu-id="f6869-110">主要</span><span class="sxs-lookup"><span data-stu-id="f6869-110">Major</span></span>|
|<span data-ttu-id="f6869-111">Version</span><span class="sxs-lookup"><span data-stu-id="f6869-111">Version</span></span>|<span data-ttu-id="f6869-112">4.5</span><span class="sxs-lookup"><span data-stu-id="f6869-112">4.5</span></span>|
|<span data-ttu-id="f6869-113">类型</span><span class="sxs-lookup"><span data-stu-id="f6869-113">Type</span></span>|<span data-ttu-id="f6869-114">运行时</span><span class="sxs-lookup"><span data-stu-id="f6869-114">Runtime</span></span>|
