---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615616"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="19df1-101">XmlWriter 引发无效的代理项对</span><span class="sxs-lookup"><span data-stu-id="19df1-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="19df1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="19df1-102">Details</span></span>

<span data-ttu-id="19df1-103">对于面向 .NET Framework 4.5.2 或以前的版本的应用程序，使用异常回退处理编写无效的代理项对并不会总是引发异常。</span><span class="sxs-lookup"><span data-stu-id="19df1-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="19df1-104">对于面向 .NET Framework 4.6 的应用，尝试编写无效的代理项对会引发 <xref:System.ArgumentException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="19df1-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="19df1-105">建议</span><span class="sxs-lookup"><span data-stu-id="19df1-105">Suggestion</span></span>

<span data-ttu-id="19df1-106">如有必要，可通过面向 .NET Framework 4.5.2 或更早版本来避免此中断。</span><span class="sxs-lookup"><span data-stu-id="19df1-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="19df1-107">或者，可在编写无效的代理项对前将其预处理为有效的 XML。</span><span class="sxs-lookup"><span data-stu-id="19df1-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="19df1-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="19df1-108">Name</span></span>    | <span data-ttu-id="19df1-109">“值”</span><span class="sxs-lookup"><span data-stu-id="19df1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="19df1-110">范围</span><span class="sxs-lookup"><span data-stu-id="19df1-110">Scope</span></span>   | <span data-ttu-id="19df1-111">边缘</span><span class="sxs-lookup"><span data-stu-id="19df1-111">Edge</span></span>        |
| <span data-ttu-id="19df1-112">Version</span><span class="sxs-lookup"><span data-stu-id="19df1-112">Version</span></span> | <span data-ttu-id="19df1-113">4.6</span><span class="sxs-lookup"><span data-stu-id="19df1-113">4.6</span></span>         |
| <span data-ttu-id="19df1-114">类型</span><span class="sxs-lookup"><span data-stu-id="19df1-114">Type</span></span>    | <span data-ttu-id="19df1-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="19df1-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="19df1-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="19df1-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
