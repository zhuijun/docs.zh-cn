---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: 99f2eb9447bdf43cb57cfe86f35d2c09044ed470
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69947617"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="9d130-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="9d130-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="9d130-103">创建 VisualStudio 的实例。 [ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)类的实例。</span><span class="sxs-lookup"><span data-stu-id="9d130-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d130-104">语法</span><span class="sxs-lookup"><span data-stu-id="9d130-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d130-105">参数</span><span class="sxs-lookup"><span data-stu-id="9d130-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="9d130-106">参数值</span><span class="sxs-lookup"><span data-stu-id="9d130-106">Parameter Values</span></span>  
 <span data-ttu-id="9d130-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="9d130-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="9d130-108">描述要在生成的工作流活动中执行的操作，包括操作名称、返回类型和参数信息。</span><span class="sxs-lookup"><span data-stu-id="9d130-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="9d130-109">此参数的值不得为**null**。</span><span class="sxs-lookup"><span data-stu-id="9d130-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="9d130-110">它应描述使用消息协定并且取得具有一个消息的参数的同步操作。</span><span class="sxs-lookup"><span data-stu-id="9d130-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="9d130-111">如果不满足这些条件，则使用此类的构造函数和其他方法的运行时结果未被定义。</span><span class="sxs-lookup"><span data-stu-id="9d130-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="9d130-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="9d130-112">*configurationName*</span></span>  
  
 <span data-ttu-id="9d130-113">指定终结点配置名称。</span><span class="sxs-lookup"><span data-stu-id="9d130-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="9d130-114">此参数的值不能为**null**或为空。</span><span class="sxs-lookup"><span data-stu-id="9d130-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="9d130-115">如果不满足这些条件，则使用此类的构造函数和其他方法的运行时结果未被定义。</span><span class="sxs-lookup"><span data-stu-id="9d130-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="9d130-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="9d130-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="9d130-117">指定操作的服务命名空间。</span><span class="sxs-lookup"><span data-stu-id="9d130-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="9d130-118">此参数的值不能为**null**或为空。</span><span class="sxs-lookup"><span data-stu-id="9d130-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="9d130-119">如果不满足这些条件，则使用此类的构造函数和其他方法的运行时结果未被定义。</span><span class="sxs-lookup"><span data-stu-id="9d130-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d130-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d130-120">See also</span></span>

- [<span data-ttu-id="9d130-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="9d130-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
