---
title: 处理 .xml 文件
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 81d2c8d305e828b2963a0af9d97ec35b1745197a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398326"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="e6061-102">处理 XML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6061-102">Processing the XML File (Visual Basic)</span></span>
<span data-ttu-id="e6061-103">编译器为代码（已标记以生成文档）中的每个构造生成一个 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="e6061-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="e6061-104">（有关如何标记代码的信息，请参阅[XML 注释标记](../../language-reference/xmldoc/index.md)。）ID 字符串唯一地标识构造。</span><span class="sxs-lookup"><span data-stu-id="e6061-104">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="e6061-105">处理 XML 文件的程序可以使用 ID 字符串来标识相应的 .NET Framework 元数据/反射项。</span><span class="sxs-lookup"><span data-stu-id="e6061-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="e6061-106">XML 文件不是代码的层次结构表示形式;它是一个平面列表，其中每个元素都有一个生成的 ID。</span><span class="sxs-lookup"><span data-stu-id="e6061-106">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="e6061-107">编译器在生成 ID 字符串时应遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="e6061-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="e6061-108">字符串不得包含空格。</span><span class="sxs-lookup"><span data-stu-id="e6061-108">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="e6061-109">ID 字符串的第一部分标识被标识的成员类型，单个字符后跟一个冒号。</span><span class="sxs-lookup"><span data-stu-id="e6061-109">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="e6061-110">使用以下成员类型。</span><span class="sxs-lookup"><span data-stu-id="e6061-110">The following member types are used.</span></span>  
  
|<span data-ttu-id="e6061-111">字符</span><span class="sxs-lookup"><span data-stu-id="e6061-111">Character</span></span>|<span data-ttu-id="e6061-112">描述</span><span class="sxs-lookup"><span data-stu-id="e6061-112">Description</span></span>|  
|---|---|  
|<span data-ttu-id="e6061-113">N</span><span class="sxs-lookup"><span data-stu-id="e6061-113">N</span></span>|<span data-ttu-id="e6061-114">namespace</span><span class="sxs-lookup"><span data-stu-id="e6061-114">namespace</span></span><br /><br /> <span data-ttu-id="e6061-115">不能将文档注释添加到命名空间，但可以对其进行 CREF 引用（如果支持）。</span><span class="sxs-lookup"><span data-stu-id="e6061-115">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="e6061-116">T</span><span class="sxs-lookup"><span data-stu-id="e6061-116">T</span></span>|<span data-ttu-id="e6061-117">类型： `Class` 、 `Module` 、 `Interface` 、 `Structure` 、 `Enum` 、`Delegate`</span><span class="sxs-lookup"><span data-stu-id="e6061-117">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="e6061-118">F</span><span class="sxs-lookup"><span data-stu-id="e6061-118">F</span></span>|<span data-ttu-id="e6061-119">定义域`Dim`</span><span class="sxs-lookup"><span data-stu-id="e6061-119">field: `Dim`</span></span>|  
|<span data-ttu-id="e6061-120">P</span><span class="sxs-lookup"><span data-stu-id="e6061-120">P</span></span>|<span data-ttu-id="e6061-121">属性： `Property` （包括默认属性）</span><span class="sxs-lookup"><span data-stu-id="e6061-121">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="e6061-122">M</span><span class="sxs-lookup"><span data-stu-id="e6061-122">M</span></span>|<span data-ttu-id="e6061-123">方法： `Sub` 、 `Function` 、 `Declare` 、`Operator`</span><span class="sxs-lookup"><span data-stu-id="e6061-123">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="e6061-124">E</span><span class="sxs-lookup"><span data-stu-id="e6061-124">E</span></span>|<span data-ttu-id="e6061-125">引发`Event`</span><span class="sxs-lookup"><span data-stu-id="e6061-125">event: `Event`</span></span>|  
|<span data-ttu-id="e6061-126">!</span><span class="sxs-lookup"><span data-stu-id="e6061-126">!</span></span>|<span data-ttu-id="e6061-127">错误字符串</span><span class="sxs-lookup"><span data-stu-id="e6061-127">error string</span></span><br /><br /> <span data-ttu-id="e6061-128">字符串的其余部分提供有关错误的信息。</span><span class="sxs-lookup"><span data-stu-id="e6061-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="e6061-129">Visual Basic 编译器将为无法解析的链接生成错误信息。</span><span class="sxs-lookup"><span data-stu-id="e6061-129">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="e6061-130">的第二部分 `String` 是项的完全限定名，从命名空间的根开始。</span><span class="sxs-lookup"><span data-stu-id="e6061-130">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="e6061-131">项的名称、其封闭类型和命名空间用句点分隔。</span><span class="sxs-lookup"><span data-stu-id="e6061-131">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="e6061-132">如果项本身的名称包含句点，则将其替换为数字符号（#）。</span><span class="sxs-lookup"><span data-stu-id="e6061-132">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="e6061-133">假定没有任何项在其名称中直接具有数字符号。</span><span class="sxs-lookup"><span data-stu-id="e6061-133">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="e6061-134">例如，构造函数的完全限定名称将 `String` 为 `System.String.#ctor` 。</span><span class="sxs-lookup"><span data-stu-id="e6061-134">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="e6061-135">对于属性和方法，如果方法带有自变量，则后跟用括号括起来的自变量列表。</span><span class="sxs-lookup"><span data-stu-id="e6061-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="e6061-136">如果没有任何自变量，则不会出现括号。</span><span class="sxs-lookup"><span data-stu-id="e6061-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="e6061-137">确保自变量之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="e6061-137">The arguments are separated by commas.</span></span> <span data-ttu-id="e6061-138">每个参数的编码会直接在 .NET Framework 签名中对其进行编码。</span><span class="sxs-lookup"><span data-stu-id="e6061-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6061-139">示例</span><span class="sxs-lookup"><span data-stu-id="e6061-139">Example</span></span>  
 <span data-ttu-id="e6061-140">下面的代码演示如何生成类及其成员的 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="e6061-140">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e6061-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6061-141">See also</span></span>

- [<span data-ttu-id="e6061-142">-doc</span><span class="sxs-lookup"><span data-stu-id="e6061-142">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="e6061-143">如何：创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="e6061-143">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
