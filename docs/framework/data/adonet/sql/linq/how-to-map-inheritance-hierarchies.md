---
title: 如何：映射继承层次结构
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: c0709fde96a5d2f39f04a08ccd24ddf90c782f30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166412"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="a378d-102">如何：映射继承层次结构</span><span class="sxs-lookup"><span data-stu-id="a378d-102">How to: Map Inheritance Hierarchies</span></span>

<span data-ttu-id="a378d-103">若要在 LINQ 中实现继承映射，必须按照以下步骤中所述，在继承层次结构的根类上指定属性和特性属性。</span><span class="sxs-lookup"><span data-stu-id="a378d-103">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="a378d-104">使用 Visual Studio 的开发人员可以使用对象关系设计器来映射继承层次结构。</span><span class="sxs-lookup"><span data-stu-id="a378d-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="a378d-105">请参阅 [如何：使用 O/R 设计器配置继承](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)。</span><span class="sxs-lookup"><span data-stu-id="a378d-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a378d-106">子类中不需要具有特殊属性 (Attribute) 或属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a378d-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="a378d-107">请特别注意，子类不具有 <xref:System.Data.Linq.Mapping.TableAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="a378d-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="a378d-108">映射继承层次结构</span><span class="sxs-lookup"><span data-stu-id="a378d-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="a378d-109">向根类添加 <xref:System.Data.Linq.Mapping.TableAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="a378d-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="a378d-110">为层次结构中的每个类添加 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性，同样是添加到根类中。</span><span class="sxs-lookup"><span data-stu-id="a378d-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="a378d-111">为每个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性 (Attribute)，定义一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a378d-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="a378d-112">此属性 (Property) 保存一个值，该值显示在数据库表的 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 列中，用来指示该行数据所属的类或子类。</span><span class="sxs-lookup"><span data-stu-id="a378d-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="a378d-113">为每个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性 (Attribute)，也添加一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> 属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a378d-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="a378d-114">此属性 (Property) 保存一个值，此值指定键值所表示的类或子类。</span><span class="sxs-lookup"><span data-stu-id="a378d-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="a378d-115">仅在其中一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性 (Attribute) 上，添加一个 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> 属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a378d-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="a378d-116">当数据库表中的鉴别器值与继承映射中的任何值都不匹配时，此属性用于指定 *回退* 映射 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a378d-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="a378d-117">为 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 属性 (Attribute) 添加一个 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a378d-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="a378d-118">此属性 (Property) 表示这是保存 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 值的列。</span><span class="sxs-lookup"><span data-stu-id="a378d-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a378d-119">示例</span><span class="sxs-lookup"><span data-stu-id="a378d-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a378d-120">如果使用的是 Visual Studio，则可以使用对象关系设计器来配置继承。</span><span class="sxs-lookup"><span data-stu-id="a378d-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="a378d-121">请参阅 [如何：使用 O/R 设计器配置继承](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="a378d-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="a378d-122">在下面的代码示例中， `Vehicle` 将定义为根类，并已实现前面的步骤来描述 LINQ 的层次结构。</span><span class="sxs-lookup"><span data-stu-id="a378d-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a378d-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="a378d-123">See also</span></span>

- [<span data-ttu-id="a378d-124">层次结构支持</span><span class="sxs-lookup"><span data-stu-id="a378d-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="a378d-125">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="a378d-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
