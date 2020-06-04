---
title: 类不支持自动化或不支持所需的接口
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 856c3f5ef503a7e5919e9e602532c56d9557482f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415396"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>类不支持自动化或不支持所需的接口
在 `GetObject` 或 `CreateObject` 函数调用中所指定的类尚未公开可编程接口，或者将项目从 .dll 更改为 .exe 或相反。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1. 检查创建对象的应用程序的相关文档，确定该对象类是否存在使用自动化的限制。  
  
2. 如果将项目从 .dll 更改为 .exe 或者相反，必须手动注销旧的 .dll 或 .exe。  
  
## <a name="see-also"></a>另请参阅

- [错误类型](../../programming-guide/language-features/error-types.md)
- [与我们交流](/visualstudio/ide/feedback-options)
