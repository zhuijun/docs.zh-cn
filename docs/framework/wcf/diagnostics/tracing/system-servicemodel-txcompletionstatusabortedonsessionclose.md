---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: c398fc52d5924c033500b95924f9287b43cc9e9d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576598"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
指定的事务被中止，因为当会话被关闭时尚未完成，且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 被设置为 false。  
  
## <a name="description"></a>描述  
 如果当前活动会话已关闭，事务未完成，并且 TransactionAutoCompleteOnSessionClose 设置为 `false`，则进行跟踪。  
  
## <a name="troubleshooting"></a>疑难解答  
 此跟踪指示一个应予调查的潜在应用程序 Bug。  
  
## <a name="see-also"></a>另请参阅

- [跟踪](index.md)
- [使用跟踪来排除应用程序故障](using-tracing-to-troubleshoot-your-application.md)
- [管理和诊断](../index.md)
