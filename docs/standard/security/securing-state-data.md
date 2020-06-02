---
title: 保护状态数据
description: 将状态数据声明为私有或内部变量，以限制对其的访问。 此类数据仍可通过反射、序列化和调试进行访问。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: b7fcb520fe6fa28cc098c4e1cbb56ce7da759c11
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291040"
---
# <a name="securing-state-data"></a>保护状态数据
处理敏感数据或做出任何种类的安全决策的应用程序需要将相关数据保持在自己的控制之下，而不允许其他可能的恶意代码直接访问这些数据。 保护内存中的数据的最好方法就是，将数据声明为私有或内部（范围限定为相同的程序集内）变量。 然而，即使这些数据受到访问权制约，你也应当注意：  
  
- 通过使用反射机制，那些能够引用你的对象的、高度受信任的代码可以获取和设置私有成员。  
  
- 使用序列化时，如果高度受信任的代码可以访问序列化形式的对象中的相应数据，那么它就可以有效地获取和设置私有成员。  
  
- 调试时，可以读取这些数据。  
  
 千万不要让你自己的任何方法或属性在无意中公开这些值。  
  
## <a name="see-also"></a>另请参阅

- [代码安全维护指南](secure-coding-guidelines.md)
