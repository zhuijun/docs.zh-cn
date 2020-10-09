---
ms.openlocfilehash: 8693c1fdef5fa194b16127d4f1dd87e23ad68f2d
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438038"
---
### <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="403a1-101">将 RCW 强制转换为 `InterfaceIsIInspectable` 接口会引发 PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="403a1-101">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="403a1-102">将运行时可调用包装器 (RCW) 强制转换为标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的接口现在会引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="403a1-102">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="403a1-103">此更改是[从 .NET 删除 WinRT 支持](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)的后续操作。</span><span class="sxs-lookup"><span data-stu-id="403a1-103">This change is a follow up to the [removal of WinRT support from .NET](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="403a1-104">引入的版本</span><span class="sxs-lookup"><span data-stu-id="403a1-104">Version introduced</span></span>

<span data-ttu-id="403a1-105">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="403a1-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="403a1-106">更改描述</span><span class="sxs-lookup"><span data-stu-id="403a1-106">Change description</span></span>

<span data-ttu-id="403a1-107">在 .NET 5.0 预览版 6 之前的 .NET 版本中，将 RCW 强制转换为标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的接口的行为符合预期。</span><span class="sxs-lookup"><span data-stu-id="403a1-107">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="403a1-108">在 .NET 5.0 预览版 6-8 和 RC1 中，可以将 RCW 成功转换为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 接口。</span><span class="sxs-lookup"><span data-stu-id="403a1-108">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="403a1-109">但是，对接口执行方法时，可能会出现访问冲突，因为[已在 .NET 5.0 预览版 6 中删除](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)运行时中的基础支持。</span><span class="sxs-lookup"><span data-stu-id="403a1-109">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span>

<span data-ttu-id="403a1-110">在 .NET 5.0 RC2 和更高版本中，将 RCW 强制转换为标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的接口将在转换时引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="403a1-110">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="403a1-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="403a1-111">Reason for change</span></span>

<span data-ttu-id="403a1-112">在[以前的 .NET 5.0 预览版](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net)中删除了对 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 的支持。</span><span class="sxs-lookup"><span data-stu-id="403a1-112">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](../../../../docs/core/compatibility/interop.md#built-in-support-for-winrt-is-removed-from-net).</span></span> <span data-ttu-id="403a1-113">但是，意外忽视了强制转换到 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 接口的操作。</span><span class="sxs-lookup"><span data-stu-id="403a1-113">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="403a1-114">由于运行时中的基础支持不再存在，引发 <xref:System.PlatformNotSupportedException> 会启用正常故障路径。</span><span class="sxs-lookup"><span data-stu-id="403a1-114">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="403a1-115">引发异常还让你更容易发现已不再支持此功能。</span><span class="sxs-lookup"><span data-stu-id="403a1-115">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="403a1-116">建议的操作</span><span class="sxs-lookup"><span data-stu-id="403a1-116">Recommended action</span></span>

- <span data-ttu-id="403a1-117">如果可以在 Windows 运行时元数据 (WinMD) 文件中定义接口，请改用 C#/WinRT 工具。</span><span class="sxs-lookup"><span data-stu-id="403a1-117">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="403a1-118">否则，请将接口标记为 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> 而不是 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>，并向 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 方法接口的开头添加三个虚拟条目。</span><span class="sxs-lookup"><span data-stu-id="403a1-118">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="403a1-119">以下代码片段演示了一个示例。</span><span class="sxs-lookup"><span data-stu-id="403a1-119">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

#### <a name="category"></a><span data-ttu-id="403a1-120">类别</span><span class="sxs-lookup"><span data-stu-id="403a1-120">Category</span></span>

<span data-ttu-id="403a1-121">Interop</span><span class="sxs-lookup"><span data-stu-id="403a1-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="403a1-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="403a1-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

-->
