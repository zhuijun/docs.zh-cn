---
title: 创建加密方案
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288415"
---
# <a name="creating-a-cryptographic-scheme"></a>创建加密方案
可结合使用 .NET Framework 的加密组件来创建不同的方案，以加密和解密数据。  
  
 用于加密和解密数据的简单加密方案可能指定以下步骤：  
  
1. 每个参与方均生成一个公钥/私钥对。  
  
2. 双方交换各自的公钥。  
  
3. 例如，每个参与方均生成一个用于加密 TripleDES 的密钥，并使用对方的公钥对新创建的密钥进行加密。  
  
4. 每个参与方都将数据发送给另一方，并以特定的顺序将对方的密钥与自身的密钥相结合，以创建新密钥。  
  
5. 然后，双方使用对称加密启动一个对话。  
  
 创建加密方案是一项重要任务。
  
## <a name="see-also"></a>另请参阅

- [加密服务](cryptographic-services.md)
