---
title: 在查询中使用批注
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 728408e744bc1eca62158fab1a7a17e985fe3b6c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69947289"
---
# <a name="using-annotation-in-queries"></a>在查询中使用批注
通过批注，可以使用可在生成时后配置的某个值任意标记跟踪记录。 例如，您可能希望多个工作流的多个跟踪记录都用 "Mail Server" = = "Mail Server1" 标记。 这样便于在以后查询跟踪记录时查找带有此标记的所有记录。  
  
## <a name="adding-annotations"></a>添加批注  
 可将批注添加到跟踪查询中，如下例所示。  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
> 可以使用这些跟踪查询元素创建跟踪配置文件。 可以通过配置或使用代码来创建跟踪配置文件。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [工作流跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)
