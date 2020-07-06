---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617130"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="29e9c-101">EncoderParameter ctor 已过时</span><span class="sxs-lookup"><span data-stu-id="29e9c-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="29e9c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="29e9c-102">Details</span></span>

<span data-ttu-id="29e9c-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 构造函数现已过时，使用它将引发生成警告。</span><span class="sxs-lookup"><span data-stu-id="29e9c-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="29e9c-104">建议</span><span class="sxs-lookup"><span data-stu-id="29e9c-104">Suggestion</span></span>

<span data-ttu-id="29e9c-105">虽然 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 构造函数仍将继续运行，但应改用以下构造函数，以避免在使用 .NET Framework 4.5 工具重新编译代码时出现已过时生成警告：<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>。</span><span class="sxs-lookup"><span data-stu-id="29e9c-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="29e9c-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="29e9c-106">Name</span></span>    | <span data-ttu-id="29e9c-107">“值”</span><span class="sxs-lookup"><span data-stu-id="29e9c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="29e9c-108">范围</span><span class="sxs-lookup"><span data-stu-id="29e9c-108">Scope</span></span>   | <span data-ttu-id="29e9c-109">次要</span><span class="sxs-lookup"><span data-stu-id="29e9c-109">Minor</span></span>       |
| <span data-ttu-id="29e9c-110">Version</span><span class="sxs-lookup"><span data-stu-id="29e9c-110">Version</span></span> | <span data-ttu-id="29e9c-111">4.5</span><span class="sxs-lookup"><span data-stu-id="29e9c-111">4.5</span></span>         |
| <span data-ttu-id="29e9c-112">类型</span><span class="sxs-lookup"><span data-stu-id="29e9c-112">Type</span></span>    | <span data-ttu-id="29e9c-113">重定目标</span><span class="sxs-lookup"><span data-stu-id="29e9c-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="29e9c-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="29e9c-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
