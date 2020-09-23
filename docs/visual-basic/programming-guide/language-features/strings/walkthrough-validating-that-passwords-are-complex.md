---
title: 验证密码复杂性
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 9597d7a9d6b68b8c91f32d97da3532f181585cf6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072348"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="03db1-102">演练：验证密码是否复杂 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03db1-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>

<span data-ttu-id="03db1-103">此方法检查某些强密码特性，并使用有关检查密码失败的信息更新字符串参数。</span><span class="sxs-lookup"><span data-stu-id="03db1-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="03db1-104">密码可在安全系统中用于向用户授权。</span><span class="sxs-lookup"><span data-stu-id="03db1-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="03db1-105">但是，密码必须难以被未经授权的用户猜出。</span><span class="sxs-lookup"><span data-stu-id="03db1-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="03db1-106">攻击者可以使用 *字典攻击* 程序，该程序可循环访问字典中的所有单词 (或不同语言的多个字典) 并测试任何词是否作为用户密码使用。</span><span class="sxs-lookup"><span data-stu-id="03db1-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="03db1-107">弱密码（如 "Yankees" 或 "Mustang"）很快就会被猜出。</span><span class="sxs-lookup"><span data-stu-id="03db1-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="03db1-108">更强的密码，例如 "？您的 " L1N3vaFiNdMeyeP@sSWerd ！" 不太可能被猜出。</span><span class="sxs-lookup"><span data-stu-id="03db1-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="03db1-109">受密码保护的系统应确保用户选择强密码。</span><span class="sxs-lookup"><span data-stu-id="03db1-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="03db1-110">强密码 (包含大写字母、小写字母、数字和特殊字符的组合) ，而不是单词。</span><span class="sxs-lookup"><span data-stu-id="03db1-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="03db1-111">此示例演示如何验证复杂性。</span><span class="sxs-lookup"><span data-stu-id="03db1-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03db1-112">示例</span><span class="sxs-lookup"><span data-stu-id="03db1-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="03db1-113">代码</span><span class="sxs-lookup"><span data-stu-id="03db1-113">Code</span></span>  

 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="03db1-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="03db1-114">Compile the code</span></span>  

 <span data-ttu-id="03db1-115">通过传递包含该密码的字符串来调用此方法。</span><span class="sxs-lookup"><span data-stu-id="03db1-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="03db1-116">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="03db1-116">This example requires:</span></span>  
  
- <span data-ttu-id="03db1-117">对 <xref:System.Text.RegularExpressions> 命名空间成员的访问权限。</span><span class="sxs-lookup"><span data-stu-id="03db1-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="03db1-118">如果未在代码中完全限定成员名称，则添加 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="03db1-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="03db1-119">有关详细信息，请参阅 [Imports 语句（.NET 命名空间和类型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="03db1-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="03db1-120">安全性</span><span class="sxs-lookup"><span data-stu-id="03db1-120">Security</span></span>  

 <span data-ttu-id="03db1-121">如果要在网络中移动密码，则需要使用安全方法来传输数据。</span><span class="sxs-lookup"><span data-stu-id="03db1-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="03db1-122">有关详细信息，请参阅 [ASP.NET Web 应用程序安全性](/previous-versions/aspnet/330a99hc(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="03db1-122">For more information, see [ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="03db1-123">可以 `ValidatePassword` 通过添加更多的复杂性检查来提高函数的准确性：</span><span class="sxs-lookup"><span data-stu-id="03db1-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="03db1-124">对照用户的名称、用户标识符和应用程序定义的字典比较密码及其子字符串。</span><span class="sxs-lookup"><span data-stu-id="03db1-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="03db1-125">此外，在执行比较时，将视觉上相似的字符视为等效字符。</span><span class="sxs-lookup"><span data-stu-id="03db1-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="03db1-126">例如，将字母 "l" 和 "e" 视为等效于数字 "1" 和 "3"。</span><span class="sxs-lookup"><span data-stu-id="03db1-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="03db1-127">如果只有一个大写字符，请确保它不是密码的第一个字符。</span><span class="sxs-lookup"><span data-stu-id="03db1-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="03db1-128">请确保密码的最后两个字符是字母字符。</span><span class="sxs-lookup"><span data-stu-id="03db1-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="03db1-129">不允许从键盘最上面的行输入所有符号的密码。</span><span class="sxs-lookup"><span data-stu-id="03db1-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03db1-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="03db1-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="03db1-131">[ASP.NET Web 应用程序安全性](/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="03db1-131">[ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
