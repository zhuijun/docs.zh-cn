---
title: 类型“<typename1>”的值无法转换为“<typename2>”（多个文件引用）
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406581"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>类型“\<typename1>”的值无法转换为“\<typename2>”（多个文件引用）
类型 "" 的值 \<typename1> 无法转换为 " \<typename2> "。 类型不匹配可能是由于将对项目 "" 中 "" 的文件引用 \<filepath1> \<projectname1> 与项目 "" 中 "" 的文件引用混合而造成的 \<filepath2> \<projectname2> 。 如果两个程序集完全相同，请尝试更换这些引用，以确保两个引用都来自相同的位置。  
  
 在项目对一个程序集进行多个文件引用的情况下，编译器无法保证可以将一种类型转换为另一种类型。  
  
 每个文件引用指定项目的输出文件的文件路径和名称（通常为 DLL 文件）。 编译器无法保证输出文件来自相同的源，或它们表示同一程序集的相同版本。 因此，它无法保证不同引用中的类型具有相同的类型，甚至可以将其转换为另一种类型。  
  
 如果知道引用的程序集具有相同的程序集标识，则可以使用单个文件引用。 *程序集标识*包括程序集的名称、版本、公钥（如果有）和区域性。 此信息唯一地标识该程序集。  
  
 **错误 ID：** BC30961  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 如果引用的程序集具有相同的程序集标识，则删除或替换其中一个文件引用，以便只有一个文件引用。  
  
- 如果引用的程序集不具有相同的程序集标识，则更改您的代码，使其不会尝试将一种类型转换为另一种类型。  
  
## <a name="see-also"></a>另请参阅

- [Visual Basic 中的类型转换](../../programming-guide/language-features/data-types/type-conversions.md)
- [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)
