---
title: 编译项目中的 XML 架构时发生错误
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 919c6873ba63addb776d756a58c44a3fe3f0ec3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409618"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>编译项目中的 XML 架构时发生错误
编译项目中的 XML 架构时发生错误。 因此，XML IntelliSense 不可用。  
  
 项目中包含的 XML 架构定义（XSD）架构中存在错误。 添加与项目的现有 XSD 架构集冲突的 XSD 架构（.xsd）文件时会发生此错误。  
  
 **错误 ID：** BC36810  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 双击 "**错误列表**" 窗口中的警告。 Visual Basic 将转到 XSD 文件中作为警告源的位置。 更正 XSD 架构中的错误。  
  
- 确保所有必需的 XSD 架构（.xsd）文件都包含在项目中。 可能需要在 "**项目**" 菜单上单击 "**显示所有文件**" 才能在**解决方案资源管理器**中查看 .xsd 文件。 右键单击 .xsd 文件，然后单击 "**包括在项目中**" 以在项目中包含该文件。  
  
- 如果你使用的是 XML 到架构向导，则如果你从同一源推导多个架构，则可能会发生此错误。 在这种情况下，您可以从项目中删除现有的 XSD 架构文件，添加一个新的 XML 到架构项模板，然后提供项目的所有适用 XML 源的 XML 到架构向导。  
  
- 如果 XSD 架构中未发现任何错误，则 XML 编译器可能没有足够的信息来提供详细的错误消息。 如果确保你的项目中包含的 .xsd 文件的 XML 命名空间与在 Visual Studio 中为 XML 架构集标识的 XML 命名空间相匹配，则你可能能够获取更详细的错误信息。  
  
## <a name="see-also"></a>另请参阅

- [错误列表窗口](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)
