---
ms.openlocfilehash: 4fb1ffed97a5b7f906bed13a69f1e71563d11dae
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556129"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="0ebe2-101">已从一些 Windows 窗体类型中删除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="0ebe2-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="0ebe2-102">已从一些没有已知二进制序列化方案的 Windows 窗体类中删除 <xref:System.SerializableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0ebe2-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="0ebe2-103">Change description</span></span>

<span data-ttu-id="0ebe2-104">下列类型在 .NET Framework 中以 <xref:System.SerializableAttribute> 进行修饰，但该属性已在 .NET Core 中删除：</span><span class="sxs-lookup"><span data-stu-id="0ebe2-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="0ebe2-105">从历史记录来看，此序列化机制存在严重的维护和安全性问题。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="0ebe2-106">保证类型上持续具有 `SerializableAttribute` 意味着必须针对版本间的序列化更改以及可能出现的框架间序列化更改测试这些类型。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="0ebe2-107">这使得很难发展这些类型且维护成本昂贵。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="0ebe2-108">这些类型没有已知的二进制序列化方案，这在最大限度上消除了删除该属性带来的影响。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="0ebe2-109">有关详细信息，请参阅[二进制序列化](~/docs/standard/serialization/binary-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0ebe2-110">引入的版本</span><span class="sxs-lookup"><span data-stu-id="0ebe2-110">Version introduced</span></span>

<span data-ttu-id="0ebe2-111">3.0</span><span class="sxs-lookup"><span data-stu-id="0ebe2-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0ebe2-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="0ebe2-112">Recommended action</span></span>

<span data-ttu-id="0ebe2-113">对于要标记为“可序列化”的类型，更新可能依赖它们的所有代码。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="0ebe2-114">类别</span><span class="sxs-lookup"><span data-stu-id="0ebe2-114">Category</span></span>

<span data-ttu-id="0ebe2-115">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="0ebe2-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0ebe2-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0ebe2-116">Affected APIs</span></span>

- <span data-ttu-id="0ebe2-117">无</span><span class="sxs-lookup"><span data-stu-id="0ebe2-117">None</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
