---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400068"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)
指定将内容的格式设置为段落。  
  
## <a name="syntax"></a>语法  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>参数  
 `content`  
 段落文本。  
  
## <a name="remarks"></a>备注  
 `<para>`标记用于标记内（如 [\<summary>](summary.md) 、 [\<remarks>](remarks.md) 或 [\<returns>](returns.md) ），并允许向文本中添加结构。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 进行编译以便将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用 `<para>` 标记将方法的 "备注" 部分拆分为 `UpdateRecord` 两个段落。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另请参阅

- [XML 注释标记](index.md)
