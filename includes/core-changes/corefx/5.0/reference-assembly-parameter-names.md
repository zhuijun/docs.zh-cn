---
ms.openlocfilehash: abcab63b5a90a70cc9dfabb031e94ce379e5471b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720175"
---
### <a name="parameter-names-changed-in-reference-assemblies"></a><span data-ttu-id="e544c-101">引用程序集中的参数名称已更改</span><span class="sxs-lookup"><span data-stu-id="e544c-101">Parameter names changed in reference assemblies</span></span>

<span data-ttu-id="e544c-102">某些引用程序集参数名称已更改以匹配实现程序集中的参数名称。</span><span class="sxs-lookup"><span data-stu-id="e544c-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e544c-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="e544c-103">Change description</span></span>

<span data-ttu-id="e544c-104">在以前的 .NET 版本中，某些[引用程序集](../../../../docs/standard/assembly/reference-assemblies.md)参数名称与实现程序集中的对应参数不同。</span><span class="sxs-lookup"><span data-stu-id="e544c-104">In previous .NET versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="e544c-105">使用命名参数和反射时，这可能会导致出现问题。</span><span class="sxs-lookup"><span data-stu-id="e544c-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="e544c-106">在 .NET 5.0 中，这些不匹配的参数名称在引用程序集中已更新，以与实现程序集中的相应参数名完全匹配。</span><span class="sxs-lookup"><span data-stu-id="e544c-106">In .NET 5.0, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="e544c-107">下表显示了更改的 API 和参数名称。</span><span class="sxs-lookup"><span data-stu-id="e544c-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="e544c-108">API</span><span class="sxs-lookup"><span data-stu-id="e544c-108">API</span></span> | <span data-ttu-id="e544c-109">旧参数名称</span><span class="sxs-lookup"><span data-stu-id="e544c-109">Old parameter name</span></span> | <span data-ttu-id="e544c-110">新参数名称</span><span class="sxs-lookup"><span data-stu-id="e544c-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=nameWithType> | `stms` | `stmts` |
| <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | `si` |
| <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=nameWithType> | `ipString` | `ipSpan` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=nameWithType> | `buffer` | `array` |
| <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=nameWithType> | `authType` | `authenticationType` |
| <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=nameWithType> | `o` | `obj` |
| <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=nameWithType> | `value` | `obj` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)> | `fNeedFileInfo` | `needFileInfo` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=nameWithType> | `value` | `strInput` |
| <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=nameWithType> | `value` | `strInput` |

#### <a name="reason-for-change"></a><span data-ttu-id="e544c-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="e544c-111">Reason for change</span></span>

<span data-ttu-id="e544c-112">更改参数名称以保持一致性，避免在使用命名参数和反射时出现故障。</span><span class="sxs-lookup"><span data-stu-id="e544c-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e544c-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e544c-113">Version introduced</span></span>

<span data-ttu-id="e544c-114">5.0</span><span class="sxs-lookup"><span data-stu-id="e544c-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e544c-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="e544c-115">Recommended action</span></span>

<span data-ttu-id="e544c-116">如果由于参数名称更改而遇到编译器错误，请相应地更新参数名称。</span><span class="sxs-lookup"><span data-stu-id="e544c-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="e544c-117">类别</span><span class="sxs-lookup"><span data-stu-id="e544c-117">Category</span></span>

<span data-ttu-id="e544c-118">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="e544c-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e544c-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e544c-119">Affected APIs</span></span>

- <xref:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)?displayProperty=fullName>
- <xref:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)?displayProperty=fullName>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackFrame.%23ctor(System.Int32,System.Boolean)>
- <xref:System.Drawing.Icon.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.Drawing.Image.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})?displayProperty=fullName>
- <xref:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)?displayProperty=fullName>
- <xref:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.IsNormalized(System.String)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)?displayProperty=fullName>
- <xref:System.StringNormalizationExtensions.Normalize(System.String)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.CodeDom.Compiler.CodeGenerator.GenerateStatements(System.CodeDom.CodeStatementCollection)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Boolean)`
- `M:System.Diagnostics.StackFrame.#ctor(System.Int32,System.Boolean)`
- `M:System.Net.NetworkCredential.GetCredential(System.String,System.Int32,System.String)`
- `M:System.Net.IPAddress.Parse(System.ReadOnlySpan{System.Char})`
- `M:System.Net.IPAddress.TryParse(System.ReadOnlySpan{System.Char},System.Net.IPAddress@)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.IsNormalized(System.String)`
- `M:System.StringNormalizationExtensions.Normalize(System.String,System.Text.NormalizationForm)`
- `M:System.StringNormalizationExtensions.Normalize(System.String)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.IsolatedStorage.IsolatedStorageFileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.ComponentModel.ParenthesizePropertyNameAttribute.Equals(System.Object)`
- `M:System.ComponentModel.RefreshPropertiesAttribute.Equals(System.Object)`
- `M:System.Drawing.Icon.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Drawing.Image.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`

-->
