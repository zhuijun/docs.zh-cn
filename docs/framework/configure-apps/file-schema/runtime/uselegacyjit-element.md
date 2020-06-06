---
title: <useLegacyJit> 元素
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968856"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="f34e4-102">\<useLegacyJit> 元素</span><span class="sxs-lookup"><span data-stu-id="f34e4-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="f34e4-103">确定公共语言运行时是否使用实时编译的旧版 64 位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="f34e4-104">语法</span><span class="sxs-lookup"><span data-stu-id="f34e4-104">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="f34e4-105">元素名称 `useLegacyJit` 区分大小写。</span><span class="sxs-lookup"><span data-stu-id="f34e4-105">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f34e4-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f34e4-106">Attributes and elements</span></span>

<span data-ttu-id="f34e4-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f34e4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f34e4-108">特性</span><span class="sxs-lookup"><span data-stu-id="f34e4-108">Attributes</span></span>  
  
| <span data-ttu-id="f34e4-109">属性</span><span class="sxs-lookup"><span data-stu-id="f34e4-109">Attribute</span></span> | <span data-ttu-id="f34e4-110">说明</span><span class="sxs-lookup"><span data-stu-id="f34e4-110">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="f34e4-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="f34e4-111">Required attribute.</span></span><br><br><span data-ttu-id="f34e4-112">指定运行时是否使用旧版64位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-112">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="f34e4-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="f34e4-113">enabled attribute</span></span>  
  
| <span data-ttu-id="f34e4-114">值</span><span class="sxs-lookup"><span data-stu-id="f34e4-114">Value</span></span> | <span data-ttu-id="f34e4-115">说明</span><span class="sxs-lookup"><span data-stu-id="f34e4-115">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="f34e4-116">0</span><span class="sxs-lookup"><span data-stu-id="f34e4-116">0</span></span>     | <span data-ttu-id="f34e4-117">公共语言运行时使用 .NET Framework 4.6 及更高版本中包含的新64位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-117">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="f34e4-118">1</span><span class="sxs-lookup"><span data-stu-id="f34e4-118">1</span></span>     | <span data-ttu-id="f34e4-119">公共语言运行时使用较旧的64位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-119">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="f34e4-120">子元素</span><span class="sxs-lookup"><span data-stu-id="f34e4-120">Child elements</span></span>

<span data-ttu-id="f34e4-121">无</span><span class="sxs-lookup"><span data-stu-id="f34e4-121">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="f34e4-122">父元素</span><span class="sxs-lookup"><span data-stu-id="f34e4-122">Parent elements</span></span>  
  
| <span data-ttu-id="f34e4-123">元素</span><span class="sxs-lookup"><span data-stu-id="f34e4-123">Element</span></span>         | <span data-ttu-id="f34e4-124">描述</span><span class="sxs-lookup"><span data-stu-id="f34e4-124">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="f34e4-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="f34e4-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="f34e4-126">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="f34e4-126">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="f34e4-127">注解</span><span class="sxs-lookup"><span data-stu-id="f34e4-127">Remarks</span></span>  

<span data-ttu-id="f34e4-128">从 .NET Framework 4.6 开始，默认情况下，公共语言运行时为实时（JIT）编译使用新的64位编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-128">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="f34e4-129">在某些情况下，这可能会导致应用程序代码的行为与以前版本的64位 JIT 编译器进行 JIT 编译的行为不同。</span><span class="sxs-lookup"><span data-stu-id="f34e4-129">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="f34e4-130">通过将 `enabled` 元素的属性设置 `<useLegacyJit>` 为 `1` ，可以禁用新的64位 jit 编译器，而使用旧的64位 jit 编译器编译应用程序。</span><span class="sxs-lookup"><span data-stu-id="f34e4-130">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f34e4-131">`<useLegacyJit>`元素仅影响64位 JIT 编译。</span><span class="sxs-lookup"><span data-stu-id="f34e4-131">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="f34e4-132">与32位 JIT 编译器的编译不受影响。</span><span class="sxs-lookup"><span data-stu-id="f34e4-132">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="f34e4-133">您可以通过两种其他方法启用旧版64位 JIT 编译器，而不是使用配置文件设置：</span><span class="sxs-lookup"><span data-stu-id="f34e4-133">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="f34e4-134">设置环境变量</span><span class="sxs-lookup"><span data-stu-id="f34e4-134">Setting an environment variable</span></span>

  <span data-ttu-id="f34e4-135">将 `COMPLUS_useLegacyJit` 环境变量设置为 `0` （使用新的64位 jit 编译器）或 `1` （使用较旧的64位 jit 编译器）：</span><span class="sxs-lookup"><span data-stu-id="f34e4-135">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="f34e4-136">环境变量具有*全局作用域*，这意味着它会影响计算机上运行的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="f34e4-136">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="f34e4-137">如果已设置，则它可以被应用程序配置文件设置重写。</span><span class="sxs-lookup"><span data-stu-id="f34e4-137">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="f34e4-138">环境变量名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="f34e4-138">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="f34e4-139">添加注册表项</span><span class="sxs-lookup"><span data-stu-id="f34e4-139">Adding a registry key</span></span>

  <span data-ttu-id="f34e4-140">可以通过将 `REG_DWORD` 值添加到 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 注册表中的或键来启用旧的64位 JIT 编译器 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 。</span><span class="sxs-lookup"><span data-stu-id="f34e4-140">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="f34e4-141">此值的名称为 `useLegacyJit` 。</span><span class="sxs-lookup"><span data-stu-id="f34e4-141">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="f34e4-142">如果该值为0，则使用新编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-142">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="f34e4-143">如果值为1，则启用旧版64位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-143">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="f34e4-144">注册表值名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="f34e4-144">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="f34e4-145">将该值添加到 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 密钥会影响计算机上运行的所有应用。</span><span class="sxs-lookup"><span data-stu-id="f34e4-145">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="f34e4-146">将该值添加到 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 密钥会影响当前用户运行的所有应用。</span><span class="sxs-lookup"><span data-stu-id="f34e4-146">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="f34e4-147">如果使用多个用户帐户配置了计算机，则只有当前用户运行的应用才会受到影响，除非还将该值添加到其他用户的注册表项。</span><span class="sxs-lookup"><span data-stu-id="f34e4-147">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="f34e4-148">如果将 `<useLegacyJit>` 元素添加到配置文件中，将重写注册表设置（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="f34e4-148">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f34e4-149">示例</span><span class="sxs-lookup"><span data-stu-id="f34e4-149">Example</span></span>  

<span data-ttu-id="f34e4-150">下面的配置文件使用新的64位 JIT 编译器禁用编译，而改用旧的64位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="f34e4-150">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f34e4-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f34e4-151">See also</span></span>

- [<span data-ttu-id="f34e4-152">\<runtime>Element</span><span class="sxs-lookup"><span data-stu-id="f34e4-152">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="f34e4-153">\<configuration>Element</span><span class="sxs-lookup"><span data-stu-id="f34e4-153">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="f34e4-154">缓解：新的 64 位 JIT 编译器</span><span class="sxs-lookup"><span data-stu-id="f34e4-154">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
