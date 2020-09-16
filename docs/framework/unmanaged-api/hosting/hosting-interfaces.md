---
title: 承载接口
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: b1459bf78276abe0daefd7a7ee814841f3c65dfb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550659"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="53097-102">承载接口</span><span class="sxs-lookup"><span data-stu-id="53097-102">Hosting Interfaces</span></span>
<span data-ttu-id="53097-103">本部分介绍了非托管主机可用于将公共语言运行时 (CLR) 集成到其应用程序的接口。</span><span class="sxs-lookup"><span data-stu-id="53097-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="53097-104">.NET Framework 版本2.0 宿主接口取代了 .NET Framework 版本1.0 和1.1 接口。</span><span class="sxs-lookup"><span data-stu-id="53097-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="53097-105">两组接口之间存在重大差异。</span><span class="sxs-lookup"><span data-stu-id="53097-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="53097-106">混合它们可能会导致意外的行为，因此不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="53097-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="53097-107">.NET Framework 版本3.0 和3.5 使用 .NET Framework 版本2.0 承载接口，不会引入任何承载功能。</span><span class="sxs-lookup"><span data-stu-id="53097-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="53097-108">.NET Framework 4 宿主接口取代了 .NET Framework 2.0 接口。</span><span class="sxs-lookup"><span data-stu-id="53097-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="53097-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="53097-109">In This Section</span></span>  
 [<span data-ttu-id="53097-110">弃用的 CLR 承载接口和 Coclass</span><span class="sxs-lookup"><span data-stu-id="53097-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="53097-111">介绍 .NET Framework 版本1.0 和1.1 中引入的托管接口。</span><span class="sxs-lookup"><span data-stu-id="53097-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="53097-112">CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="53097-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="53097-113">介绍 .NET Framework 版本2.0 中引入的托管接口。</span><span class="sxs-lookup"><span data-stu-id="53097-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="53097-114">.NET Framework 4 和 4.5 中添加的 CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="53097-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="53097-115">介绍 .NET Framework 4 中引入的托管接口。</span><span class="sxs-lookup"><span data-stu-id="53097-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53097-116">相关章节</span><span class="sxs-lookup"><span data-stu-id="53097-116">Related Sections</span></span>  
 [<span data-ttu-id="53097-117">承载组件类</span><span class="sxs-lookup"><span data-stu-id="53097-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="53097-118">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="53097-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="53097-119">承载枚举</span><span class="sxs-lookup"><span data-stu-id="53097-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="53097-120">承载结构</span><span class="sxs-lookup"><span data-stu-id="53097-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="53097-121">承载</span><span class="sxs-lookup"><span data-stu-id="53097-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="53097-122">[运行时主机](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53097-122">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
