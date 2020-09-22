---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679993"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="a1bfc-101">SignalR：HandshakeProtocol.SuccessHandshakeData 已替换</span><span class="sxs-lookup"><span data-stu-id="a1bfc-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="a1bfc-102">已删除 [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) 字段，并将其替换为一个 Helper 方法，该方法根据特定 `IHubProtocol` 生成成功的握手响应。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a1bfc-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="a1bfc-103">Version introduced</span></span>

<span data-ttu-id="a1bfc-104">3.0</span><span class="sxs-lookup"><span data-stu-id="a1bfc-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a1bfc-105">旧行为</span><span class="sxs-lookup"><span data-stu-id="a1bfc-105">Old behavior</span></span>

<span data-ttu-id="a1bfc-106">`HandshakeProtocol.SuccessHandshakeData` 是 `public static ReadOnlyMemory<byte>` 字段。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a1bfc-107">新行为</span><span class="sxs-lookup"><span data-stu-id="a1bfc-107">New behavior</span></span>

<span data-ttu-id="a1bfc-108">`HandshakeProtocol.SuccessHandshakeData` 已被 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 方法替换，该方法根据指定的协议返回 `ReadOnlyMemory<byte>`。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a1bfc-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="a1bfc-109">Reason for change</span></span>

<span data-ttu-id="a1bfc-110">握手响应  中添加了其他字段，这些字段是非常量，并会根据所选协议的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a1bfc-111">建议操作</span><span class="sxs-lookup"><span data-stu-id="a1bfc-111">Recommended action</span></span>

<span data-ttu-id="a1bfc-112">无。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-112">None.</span></span> <span data-ttu-id="a1bfc-113">此类型不适用于从用户代码使用。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="a1bfc-114">它是 `public` 类型，因此可以在 SignalR 服务器和客户端之间共享。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="a1bfc-115">它还可以由以 .NET 编写的客户 SignalR 客户端使用。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="a1bfc-116">SignalR 用户不应受此更改的影响  。</span><span class="sxs-lookup"><span data-stu-id="a1bfc-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="a1bfc-117">类别</span><span class="sxs-lookup"><span data-stu-id="a1bfc-117">Category</span></span>

<span data-ttu-id="a1bfc-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a1bfc-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a1bfc-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a1bfc-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
