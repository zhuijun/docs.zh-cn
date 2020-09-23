---
title: 如何：确定与枚举值关联的字符串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4138759bfbb049b77406fc536219b40d3ed9e2a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058764"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="87e4c-102">如何：确定与枚举值关联的字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87e4c-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="87e4c-103"><xref:System.Enum.GetValues%2A>和 <xref:System.Enum.GetNames%2A> 方法允许您确定与枚举成员关联的字符串和值。</span><span class="sxs-lookup"><span data-stu-id="87e4c-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="87e4c-104">确定与枚举关联的字符串</span><span class="sxs-lookup"><span data-stu-id="87e4c-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="87e4c-105">使用 <xref:System.Enum.GetNames%2A> 方法检索与枚举成员关联的字符串。</span><span class="sxs-lookup"><span data-stu-id="87e4c-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="87e4c-106">此示例声明一个枚举， `flavorEnum` 然后使用 <xref:System.Enum.GetNames%2A> 方法显示与每个成员关联的字符串。</span><span class="sxs-lookup"><span data-stu-id="87e4c-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="87e4c-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="87e4c-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="87e4c-108">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="87e4c-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="87e4c-109">如何：引用枚举成员</span><span class="sxs-lookup"><span data-stu-id="87e4c-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="87e4c-110">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="87e4c-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="87e4c-111">如何：在 Visual Basic 中循环访问枚举</span><span class="sxs-lookup"><span data-stu-id="87e4c-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="87e4c-112">何时使用枚举</span><span class="sxs-lookup"><span data-stu-id="87e4c-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="87e4c-113">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="87e4c-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
