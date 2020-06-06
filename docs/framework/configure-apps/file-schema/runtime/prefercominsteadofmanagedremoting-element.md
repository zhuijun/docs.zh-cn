---
title: <PreferComInsteadOfManagedRemoting> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452248"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="0c8a9-102">\<PreferComInsteadOfManagedRemoting> 元素</span><span class="sxs-lookup"><span data-stu-id="0c8a9-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="0c8a9-103">指定运行时是否将对跨应用程序域边界的所有调用使用 COM 互操作而不是远程处理。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="0c8a9-104">语法</span><span class="sxs-lookup"><span data-stu-id="0c8a9-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c8a9-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0c8a9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0c8a9-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c8a9-107">特性</span><span class="sxs-lookup"><span data-stu-id="0c8a9-107">Attributes</span></span>  
  
|<span data-ttu-id="0c8a9-108">属性</span><span class="sxs-lookup"><span data-stu-id="0c8a9-108">Attribute</span></span>|<span data-ttu-id="0c8a9-109">说明</span><span class="sxs-lookup"><span data-stu-id="0c8a9-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0c8a9-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c8a9-111">指示运行时是否将使用 COM 互操作，而不是跨应用程序域边界进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0c8a9-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="0c8a9-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="0c8a9-113">值</span><span class="sxs-lookup"><span data-stu-id="0c8a9-113">Value</span></span>|<span data-ttu-id="0c8a9-114">说明</span><span class="sxs-lookup"><span data-stu-id="0c8a9-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0c8a9-115">运行时将跨应用程序域边界使用远程处理。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="0c8a9-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0c8a9-117">运行时将跨应用程序域边界使用 COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c8a9-118">子元素</span><span class="sxs-lookup"><span data-stu-id="0c8a9-118">Child Elements</span></span>  
 <span data-ttu-id="0c8a9-119">无。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c8a9-120">父元素</span><span class="sxs-lookup"><span data-stu-id="0c8a9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0c8a9-121">元素</span><span class="sxs-lookup"><span data-stu-id="0c8a9-121">Element</span></span>|<span data-ttu-id="0c8a9-122">描述</span><span class="sxs-lookup"><span data-stu-id="0c8a9-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0c8a9-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0c8a9-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8a9-125">注解</span><span class="sxs-lookup"><span data-stu-id="0c8a9-125">Remarks</span></span>  
 <span data-ttu-id="0c8a9-126">将 `enabled` 属性设置为时 `true` ，运行时的行为如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c8a9-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="0c8a9-127">当[iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)接口通过 COM 接口进入域时，运行时不为[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)接口调用[iunknown：： QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="0c8a9-128">相反，它会在对象周围构造一个[运行时可调用包装](../../../../standard/native-interop/runtime-callable-wrapper.md)器（RCW）。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="0c8a9-129">运行时在接收到已 `QueryInterface` 在此域中创建的任何 COM 可[调用包装](../../../../standard/native-interop/com-callable-wrapper.md)器（CCW）的[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)接口调用时返回 E_NOINTERFACE。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="0c8a9-130">这两个行为确保跨应用程序域边界在托管对象之间对 COM 接口进行的所有调用均使用 COM 和 COM 互操作，而不是远程处理。</span><span class="sxs-lookup"><span data-stu-id="0c8a9-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c8a9-131">示例</span><span class="sxs-lookup"><span data-stu-id="0c8a9-131">Example</span></span>  
 <span data-ttu-id="0c8a9-132">下面的示例演示如何指定运行时应跨隔离边界使用 COM 互操作：</span><span class="sxs-lookup"><span data-stu-id="0c8a9-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c8a9-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c8a9-133">See also</span></span>

- [<span data-ttu-id="0c8a9-134">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="0c8a9-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0c8a9-135">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="0c8a9-135">Configuration File Schema</span></span>](../index.md)
