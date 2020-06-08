---
title: My.Forms 和 My.WebServices 提供的默认对象实例
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 847724450ee2bc8bc591371f71171e8ba4ed9337
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411735"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="57e76-102">My.Forms 和 My.WebServices 提供的默认对象实例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57e76-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="57e76-103">[My.Forms](../../language-reference/objects/my-forms-object.md) 和 [My.WebServices](../../language-reference/objects/my-webservices-object.md) 对象提供对应用程序使用的窗体、数据源和 XML Web Service 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="57e76-103">The [My.Forms](../../language-reference/objects/my-forms-object.md) and [My.WebServices](../../language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="57e76-104">它们通过提供其中每个对象的默认实例  的集合来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="57e76-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="57e76-105">默认实例</span><span class="sxs-lookup"><span data-stu-id="57e76-105">Default Instances</span></span>  

 <span data-ttu-id="57e76-106">默认实例是由运行时提供的类的实例，无需使用 `Dim` 和 `New` 语句进行声明和实例化。</span><span class="sxs-lookup"><span data-stu-id="57e76-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="57e76-107">下面的示例演示如何声明和实例化名为 `Form1` 的 <xref:System.Windows.Forms.Form> 类的实例，以及现在如何能够通过 `My.Forms` 获取此 <xref:System.Windows.Forms.Form> 类的默认实例。</span><span class="sxs-lookup"><span data-stu-id="57e76-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="57e76-108">`My.Forms` 对象会为项目中存在的每个 `Form` 类返回默认实例的集合。</span><span class="sxs-lookup"><span data-stu-id="57e76-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="57e76-109">同样，`My.WebServices` 为在应用程序中创建了其引用的每个 Web 服务提供代理类的默认实例。</span><span class="sxs-lookup"><span data-stu-id="57e76-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e76-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="57e76-110">See also</span></span>

- [<span data-ttu-id="57e76-111">My.Forms 对象</span><span class="sxs-lookup"><span data-stu-id="57e76-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="57e76-112">My.WebServices 对象</span><span class="sxs-lookup"><span data-stu-id="57e76-112">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="57e76-113">My 对项目类型的依赖方式</span><span class="sxs-lookup"><span data-stu-id="57e76-113">How My Depends on Project Type</span></span>](how-my-depends-on-project-type.md)
