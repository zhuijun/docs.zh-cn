---
title: Azure Active Directory
description: 构建适用于 Azure 的云本机 .NET 应用 |Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 55787f3565fc15bb25cf1a101aa5c1e3ddefe5e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161108"
---
# <a name="azure-active-directory"></a><span data-ttu-id="e9386-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e9386-103">Azure Active Directory</span></span>

<span data-ttu-id="e9386-104">Microsoft Azure Active Directory (Azure AD) 以服务形式提供身份标识和访问管理。</span><span class="sxs-lookup"><span data-stu-id="e9386-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="e9386-105">客户使用它来配置和维护用户是谁、存储他们的信息、谁可以访问该信息、谁可以管理该信息以及哪些应用程序可以访问它。</span><span class="sxs-lookup"><span data-stu-id="e9386-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="e9386-106">AAD 可以对配置为使用的应用程序的用户进行身份验证，并提供单一登录 (SSO) 体验。</span><span class="sxs-lookup"><span data-stu-id="e9386-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="e9386-107">它可以单独使用，也可以与在本地运行的 Windows AD 集成。</span><span class="sxs-lookup"><span data-stu-id="e9386-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="e9386-108">为云构建 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="e9386-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="e9386-109">它确实是一种云本机标识解决方案，它使用基于 REST 的图形 API 和 OData 语法进行查询，这与使用 LDAP 的 Windows AD 不同。</span><span class="sxs-lookup"><span data-stu-id="e9386-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="e9386-110">本地 Active Directory 可以使用标识同步服务将用户属性同步到云，允许在云中使用 Azure AD 进行所有身份验证。</span><span class="sxs-lookup"><span data-stu-id="e9386-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="e9386-111">或者，可以通过 "连接" 配置身份验证，通过 ADFS 传递回本地 Active Directory 以通过 Windows AD 本地完成。</span><span class="sxs-lookup"><span data-stu-id="e9386-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="e9386-112">Azure AD 支持公司品牌的登录屏幕、多工厂身份验证以及用于为本地托管的应用程序提供 SSO 的基于云的应用程序代理。</span><span class="sxs-lookup"><span data-stu-id="e9386-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="e9386-113">它提供不同类型的安全报告和警报功能。</span><span class="sxs-lookup"><span data-stu-id="e9386-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="e9386-114">参考</span><span class="sxs-lookup"><span data-stu-id="e9386-114">References</span></span>

- [<span data-ttu-id="e9386-115">Microsoft 标识平台</span><span class="sxs-lookup"><span data-stu-id="e9386-115">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="e9386-116">[上一页](authentication-authorization.md)
>[下一页](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="e9386-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
