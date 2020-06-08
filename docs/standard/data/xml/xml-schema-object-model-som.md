---
title: XML 架构对象模型 (SOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: 1de9fdf9950ba3ae356779ca802afb71f24a345e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290313"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="dea34-102">XML 架构对象模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="dea34-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="dea34-103">XML 架构是用于在符合该架构的 XML 文档中创建和验证结构的强大而复杂的工具。</span><span class="sxs-lookup"><span data-stu-id="dea34-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="dea34-104">与关系数据库中的数据建模类似，架构提供一种定义 XML 文档结构的方法，这种方法是指定可在文档中使用的元素，同时还要指定这些元素必须遵循的结构和类型，以便这些元素对于该特定架构来说是有效的。</span><span class="sxs-lookup"><span data-stu-id="dea34-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="dea34-105">架构对象模型 (SOM) 在 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中提供一组类，用于从文件读取架构或通过编程创建内存中架构。</span><span class="sxs-lookup"><span data-stu-id="dea34-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="dea34-106">然后，架构可以遍历、编辑、编译、验证或写入文件。</span><span class="sxs-lookup"><span data-stu-id="dea34-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dea34-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="dea34-107">In This Section</span></span>  
 [<span data-ttu-id="dea34-108">XML 架构对象模型概述</span><span class="sxs-lookup"><span data-stu-id="dea34-108">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)  
 <span data-ttu-id="dea34-109">描述架构对象模型 (SOM) 以及它提供的功能和类。</span><span class="sxs-lookup"><span data-stu-id="dea34-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="dea34-110">读取和编写 XML 架构</span><span class="sxs-lookup"><span data-stu-id="dea34-110">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="dea34-111">描述如何从文件或其他源读取和写入 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="dea34-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="dea34-112">生成 XML 架构</span><span class="sxs-lookup"><span data-stu-id="dea34-112">Building XML Schemas</span></span>](building-xml-schemas.md)  
 <span data-ttu-id="dea34-113">描述如何使用 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的类来生成内存中 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="dea34-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="dea34-114">遍历 XML 架构</span><span class="sxs-lookup"><span data-stu-id="dea34-114">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)  
 <span data-ttu-id="dea34-115">描述如何遍历 XML 架构以访问 SOM 中存储的元素、属性和类型。</span><span class="sxs-lookup"><span data-stu-id="dea34-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="dea34-116">编辑 XML 架构</span><span class="sxs-lookup"><span data-stu-id="dea34-116">Editing XML Schemas</span></span>](editing-xml-schemas.md)  
 <span data-ttu-id="dea34-117">描述如何编辑 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="dea34-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="dea34-118">包含或导入 XML 架构</span><span class="sxs-lookup"><span data-stu-id="dea34-118">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)  
 <span data-ttu-id="dea34-119">描述如何包括或导入其他 XML 架构来补充包括或导入这些架构的架构的结构。</span><span class="sxs-lookup"><span data-stu-id="dea34-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>
