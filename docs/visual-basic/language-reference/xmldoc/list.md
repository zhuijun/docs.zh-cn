---
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 955c1a4c5c5619f908b8d03dbf12360c23574478
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400081"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
定义列表或表。  
  
## <a name="syntax"></a>语法  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>参数  
 `type`  
 列表的类型。 必须是项目符号列表的 "项目符号"、编号列表的 "数字" 或两列表的 "表"。  
  
 `term`  
 仅当为 "table" 时才使用 `type` 。 要定义的术语，在 description 标记中定义。  
  
 `description`  
 当为 "表" 时，为列表中的项，而 "表" 是的 `type` `description` `type` `description` 定义 `term` 。  
  
## <a name="remarks"></a>备注  
 `<listheader>`块定义表或定义列表的标题。 定义表时，只需为标题中的提供一个条目 `term` 。  
  
 列表中的每一项均使用块来指定 `<item>` 。 创建定义列表时，必须同时指定 `term` 和 `description` 。 但是，对于表、项目符号列表或编号列表，你只需为提供一个条目 `description` 。  
  
 列表或表可以有多个 `<item>` 所需的块。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用 `<list>` 标记在 "备注" 部分中定义项目符号列表。  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>另请参阅

- [XML 注释标记](index.md)
