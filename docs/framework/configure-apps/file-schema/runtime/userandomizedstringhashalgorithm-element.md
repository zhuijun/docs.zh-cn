---
title: <UseRandomizedStringHashAlgorithm> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153772"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="d2fce-102">\<UseRandomizedStringHashAlgorithm> 元素</span><span class="sxs-lookup"><span data-stu-id="d2fce-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="d2fce-103">确定公共语言运行时是否按应用程序域计算字符串的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a><span data-ttu-id="d2fce-104">语法</span><span class="sxs-lookup"><span data-stu-id="d2fce-104">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2fce-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d2fce-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d2fce-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d2fce-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2fce-107">特性</span><span class="sxs-lookup"><span data-stu-id="d2fce-107">Attributes</span></span>  
  
|<span data-ttu-id="d2fce-108">属性</span><span class="sxs-lookup"><span data-stu-id="d2fce-108">Attribute</span></span>|<span data-ttu-id="d2fce-109">说明</span><span class="sxs-lookup"><span data-stu-id="d2fce-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d2fce-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="d2fce-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d2fce-111">指定是否基于每个应用程序域计算字符串的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-111">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d2fce-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="d2fce-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="d2fce-113">值</span><span class="sxs-lookup"><span data-stu-id="d2fce-113">Value</span></span>|<span data-ttu-id="d2fce-114">说明</span><span class="sxs-lookup"><span data-stu-id="d2fce-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="d2fce-115">公共语言运行时不会为每个应用程序域计算字符串的哈希代码;单个算法用于计算字符串哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-115">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="d2fce-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="d2fce-116">This is the default.</span></span>|  
|`1`|<span data-ttu-id="d2fce-117">公共语言运行时基于每个应用程序域计算字符串的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-117">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="d2fce-118">不同应用程序域和不同进程中的相同字符串具有不同的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-118">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2fce-119">子元素</span><span class="sxs-lookup"><span data-stu-id="d2fce-119">Child Elements</span></span>  
 <span data-ttu-id="d2fce-120">无。</span><span class="sxs-lookup"><span data-stu-id="d2fce-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2fce-121">父元素</span><span class="sxs-lookup"><span data-stu-id="d2fce-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d2fce-122">元素</span><span class="sxs-lookup"><span data-stu-id="d2fce-122">Element</span></span>|<span data-ttu-id="d2fce-123">描述</span><span class="sxs-lookup"><span data-stu-id="d2fce-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d2fce-124">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="d2fce-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d2fce-125">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="d2fce-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2fce-126">注解</span><span class="sxs-lookup"><span data-stu-id="d2fce-126">Remarks</span></span>  
 <span data-ttu-id="d2fce-127">默认情况下， <xref:System.StringComparer> 类和 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 方法使用单个哈希算法，该算法可跨应用程序域生成一致的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-127">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="d2fce-128">这等效于将元素的 `enabled` 特性设置 `<UseRandomizedStringHashAlgorithm>` 为 `0` 。</span><span class="sxs-lookup"><span data-stu-id="d2fce-128">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="d2fce-129">这是 .NET Framework 4 中使用的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="d2fce-129">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="d2fce-130"><xref:System.StringComparer>类和 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 方法也可以使用不同的哈希算法来计算每个应用程序域的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="d2fce-130">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="d2fce-131">因此，相同字符串的哈希代码将在应用程序域之间有所不同。</span><span class="sxs-lookup"><span data-stu-id="d2fce-131">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="d2fce-132">这是一项可选功能;若要利用它，必须将 `enabled` 元素的属性设置 `<UseRandomizedStringHashAlgorithm>` 为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="d2fce-132">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="d2fce-133">哈希表中的字符串查找通常为 O （1）操作。</span><span class="sxs-lookup"><span data-stu-id="d2fce-133">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="d2fce-134">但是，当发生大量冲突时，查找可能会成为 O （n<sup>2</sup>）操作。</span><span class="sxs-lookup"><span data-stu-id="d2fce-134">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="d2fce-135">您可以使用 `<UseRandomizedStringHashAlgorithm>` configuration 元素为每个应用程序域生成随机哈希算法，这反过来会限制潜在冲突的数目，特别是当从中计算哈希代码的键基于用户输入的数据时。</span><span class="sxs-lookup"><span data-stu-id="d2fce-135">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2fce-136">示例</span><span class="sxs-lookup"><span data-stu-id="d2fce-136">Example</span></span>  
 <span data-ttu-id="d2fce-137">下面的示例定义了一个 `DisplayString` 类，该类包含一个私有字符串常量， `s` 其值为 "This is a string"。</span><span class="sxs-lookup"><span data-stu-id="d2fce-137">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="d2fce-138">它还包括显示字符串值及其哈希代码的 `ShowStringHashCode` 方法以及该方法在其中执行的应用程序域的名称。</span><span class="sxs-lookup"><span data-stu-id="d2fce-138">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="d2fce-139">当您在未提供配置文件的情况下运行该示例时，它会显示类似下面的输出。</span><span class="sxs-lookup"><span data-stu-id="d2fce-139">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="d2fce-140">请注意，字符串的散列码在两个应用程序域中是相同的。</span><span class="sxs-lookup"><span data-stu-id="d2fce-140">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="d2fce-141">但是，如果将以下配置文件添加到示例目录，然后运行该示例，则同一个字符串的哈希代码将通过应用程序域进行区分。</span><span class="sxs-lookup"><span data-stu-id="d2fce-141">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d2fce-142">存在配置文件时，示例会显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="d2fce-142">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2fce-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2fce-143">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
