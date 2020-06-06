---
title: <Event>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181041"
---
# <a name="event-element-net-native"></a><span data-ttu-id="e910a-102">\<Event>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e910a-102">\<Event> Element (.NET Native)</span></span>
<span data-ttu-id="e910a-103">将运行时反射策略应用到一个事件。</span><span class="sxs-lookup"><span data-stu-id="e910a-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e910a-104">语法</span><span class="sxs-lookup"><span data-stu-id="e910a-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e910a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e910a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e910a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e910a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e910a-107">特性</span><span class="sxs-lookup"><span data-stu-id="e910a-107">Attributes</span></span>  
  
|<span data-ttu-id="e910a-108">属性</span><span class="sxs-lookup"><span data-stu-id="e910a-108">Attribute</span></span>|<span data-ttu-id="e910a-109">属性类型</span><span class="sxs-lookup"><span data-stu-id="e910a-109">Attribute type</span></span>|<span data-ttu-id="e910a-110">说明</span><span class="sxs-lookup"><span data-stu-id="e910a-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e910a-111">常规</span><span class="sxs-lookup"><span data-stu-id="e910a-111">General</span></span>|<span data-ttu-id="e910a-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="e910a-112">Required attribute.</span></span> <span data-ttu-id="e910a-113">指定事件名称。</span><span class="sxs-lookup"><span data-stu-id="e910a-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="e910a-114">反射</span><span class="sxs-lookup"><span data-stu-id="e910a-114">Reflection</span></span>|<span data-ttu-id="e910a-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="e910a-115">Optional attribute.</span></span> <span data-ttu-id="e910a-116">控制对该事件信息的查询或列举该事件，但并不在运行时间启用任何动态访问。</span><span class="sxs-lookup"><span data-stu-id="e910a-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e910a-117">反射</span><span class="sxs-lookup"><span data-stu-id="e910a-117">Reflection</span></span>|<span data-ttu-id="e910a-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="e910a-118">Optional attribute.</span></span> <span data-ttu-id="e910a-119">控制运行时对该事件的访问，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="e910a-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="e910a-120">该策略确保一个事件可在运行时间内得到处理。</span><span class="sxs-lookup"><span data-stu-id="e910a-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e910a-121">Name 特性</span><span class="sxs-lookup"><span data-stu-id="e910a-121">Name attribute</span></span>  
  
|<span data-ttu-id="e910a-122">值</span><span class="sxs-lookup"><span data-stu-id="e910a-122">Value</span></span>|<span data-ttu-id="e910a-123">说明</span><span class="sxs-lookup"><span data-stu-id="e910a-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e910a-124">method_name\*\*</span><span class="sxs-lookup"><span data-stu-id="e910a-124">*method_name*</span></span>|<span data-ttu-id="e910a-125">事件名称。</span><span class="sxs-lookup"><span data-stu-id="e910a-125">The event name.</span></span> <span data-ttu-id="e910a-126">事件的类型由父级 [\<Type>](type-element-net-native.md) 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素定义。</span><span class="sxs-lookup"><span data-stu-id="e910a-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e910a-127">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="e910a-127">All other attributes</span></span>  
  
|<span data-ttu-id="e910a-128">值</span><span class="sxs-lookup"><span data-stu-id="e910a-128">Value</span></span>|<span data-ttu-id="e910a-129">说明</span><span class="sxs-lookup"><span data-stu-id="e910a-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e910a-130">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="e910a-130">*policy_setting*</span></span>|<span data-ttu-id="e910a-131">该设置将应用到这个事件的策略类型。</span><span class="sxs-lookup"><span data-stu-id="e910a-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="e910a-132">可能值为 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="e910a-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e910a-133">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e910a-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e910a-134">子元素</span><span class="sxs-lookup"><span data-stu-id="e910a-134">Child Elements</span></span>  
 <span data-ttu-id="e910a-135">无。</span><span class="sxs-lookup"><span data-stu-id="e910a-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e910a-136">父元素</span><span class="sxs-lookup"><span data-stu-id="e910a-136">Parent Elements</span></span>  
  
|<span data-ttu-id="e910a-137">元素</span><span class="sxs-lookup"><span data-stu-id="e910a-137">Element</span></span>|<span data-ttu-id="e910a-138">说明</span><span class="sxs-lookup"><span data-stu-id="e910a-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="e910a-139">将反射策略应用到一种类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="e910a-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="e910a-140">将反射策略应用到一种构造泛型类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="e910a-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e910a-141">注解</span><span class="sxs-lookup"><span data-stu-id="e910a-141">Remarks</span></span>  
 <span data-ttu-id="e910a-142">如果一个事件的策略没有得到显式定义，它将继承其父元素的运行时策略。</span><span class="sxs-lookup"><span data-stu-id="e910a-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e910a-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e910a-143">See also</span></span>

- [<span data-ttu-id="e910a-144">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="e910a-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e910a-145">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="e910a-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="e910a-146">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="e910a-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
