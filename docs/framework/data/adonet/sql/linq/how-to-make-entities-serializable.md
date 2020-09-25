---
title: 如何：使实体可序列化
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: f4528cab21ac678f5d06717d0ce6e7ff7e77d3e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203496"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="c7e32-102">如何：使实体可序列化</span><span class="sxs-lookup"><span data-stu-id="c7e32-102">How to: Make Entities Serializable</span></span>

<span data-ttu-id="c7e32-103">当您生成代码时，可以使实体可序列化。</span><span class="sxs-lookup"><span data-stu-id="c7e32-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="c7e32-104">实体类使用 <xref:System.Runtime.Serialization.DataContractAttribute> 属性修饰，列使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性修饰。</span><span class="sxs-lookup"><span data-stu-id="c7e32-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="c7e32-105">使用 Visual Studio 的开发人员可以使用对象关系设计器来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="c7e32-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="c7e32-106">如果使用 SQLMetal 命令行工具，请将 **/serialization** 选项与参数一起使用 `unidirectional` 。</span><span class="sxs-lookup"><span data-stu-id="c7e32-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="c7e32-107">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e32-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7e32-108">示例</span><span class="sxs-lookup"><span data-stu-id="c7e32-108">Example</span></span>  

 <span data-ttu-id="c7e32-109">以下 SQLMetal 命令行会产生包含可序列化实体的文件。</span><span class="sxs-lookup"><span data-stu-id="c7e32-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7e32-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7e32-110">See also</span></span>

- [<span data-ttu-id="c7e32-111">序列化</span><span class="sxs-lookup"><span data-stu-id="c7e32-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="c7e32-112">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="c7e32-112">Creating the Object Model</span></span>](creating-the-object-model.md)
