---
title: 标识
description: 构建适用于 Azure 的云本机 .NET 应用 |标识
ms.date: 05/13/2020
ms.openlocfilehash: 66ff29947093d7c4fe57b11039190836dc37db08
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163747"
---
# <a name="identity"></a><span data-ttu-id="bb06e-103">标识</span><span class="sxs-lookup"><span data-stu-id="bb06e-103">Identity</span></span>

<span data-ttu-id="bb06e-104">大多数软件应用程序都需要对调用它们的用户或进程有一定的了解。</span><span class="sxs-lookup"><span data-stu-id="bb06e-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="bb06e-105">与应用程序交互的用户或进程称为 "安全主体"，并对这些主体进行身份验证和授权的过程称为 "标识管理" 或简称为 " *标识*"。</span><span class="sxs-lookup"><span data-stu-id="bb06e-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="bb06e-106">简单的应用程序可能会在应用程序中包含它们的所有标识管理，但这种方法并不能很好地适应许多应用程序以及许多类型的安全主体。</span><span class="sxs-lookup"><span data-stu-id="bb06e-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="bb06e-107">Windows 支持使用 Active Directory 来提供集中式身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="bb06e-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="bb06e-108">虽然此解决方案在企业网络中有效，但它不是由 AD 域之外的用户或应用程序使用的。</span><span class="sxs-lookup"><span data-stu-id="bb06e-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="bb06e-109">随着基于 Internet 的应用程序和云本机应用程序的增长，安全模式也在不断发展。</span><span class="sxs-lookup"><span data-stu-id="bb06e-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="bb06e-110">在当今的云本机标识模型中，体系结构假定为已分发。</span><span class="sxs-lookup"><span data-stu-id="bb06e-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="bb06e-111">应用可在任何位置进行部署，并且可以在任何位置与其他应用进行通信。</span><span class="sxs-lookup"><span data-stu-id="bb06e-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="bb06e-112">客户端可以从任何位置与这些应用程序进行通信，实际上，客户端可能包含平台和设备的任意组合。</span><span class="sxs-lookup"><span data-stu-id="bb06e-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="bb06e-113">云本机标识解决方案利用开放标准来实现客户端的安全应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="bb06e-113">Cloud-native identity solutions leverage open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="bb06e-114">这些客户端范围从电脑或手机上的用户用户，到在世界各地托管的其他应用程序，再到在世界各地运行任何软件平台的机顶盒和 IOT 设备。</span><span class="sxs-lookup"><span data-stu-id="bb06e-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="bb06e-115">新式云本机标识解决方案通常利用由安全令牌服务/服务器 (STS) 在确定其标识后颁发给安全主体的访问令牌。</span><span class="sxs-lookup"><span data-stu-id="bb06e-115">Modern cloud-native identity solutions typically leverage access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="bb06e-116"> (JWT) 的访问令牌（通常为 JSON Web 令牌）包含有关安全主体的 *声明* 。</span><span class="sxs-lookup"><span data-stu-id="bb06e-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="bb06e-117">这些声明将最少包括用户的标识，但也可能包括其他声明，应用程序可以使用这些声明来确定授予主体的访问权限级别。</span><span class="sxs-lookup"><span data-stu-id="bb06e-117">These claims will minimally include the user's identity but may also include additional claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="bb06e-118">通常，STS 只负责对主体进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="bb06e-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="bb06e-119">确定其对资源的访问级别是否留给了应用程序的其他部分。</span><span class="sxs-lookup"><span data-stu-id="bb06e-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="bb06e-120">参考</span><span class="sxs-lookup"><span data-stu-id="bb06e-120">References</span></span>

- [<span data-ttu-id="bb06e-121">Microsoft 标识平台</span><span class="sxs-lookup"><span data-stu-id="bb06e-121">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="bb06e-122">[上一页](azure-monitor.md)
>[下一页](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="bb06e-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>
