---
title: 执行不区分区域性的大小写更改
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: 6baef7b0a5bbdacd33d84df01b1aa943897a9e3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276811"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="78407-102">执行不区分区域性的大小写更改</span><span class="sxs-lookup"><span data-stu-id="78407-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="78407-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType> 和 <xref:System.Char.ToLower%2A?displayProperty=nameWithType> 方法提供不接受任何参数的重载。</span><span class="sxs-lookup"><span data-stu-id="78407-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="78407-104">默认情况下，这些不带参数的重载根据 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 的值执行大小写更改。</span><span class="sxs-lookup"><span data-stu-id="78407-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78407-105">这样生成的结果（区分大小写）可能会因区域性而异。</span><span class="sxs-lookup"><span data-stu-id="78407-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="78407-106">为了明确希望大小写更改是区域性敏感型，还是非区域性敏感型，应使用这些要求显式指定 `culture` 参数的方法重载。</span><span class="sxs-lookup"><span data-stu-id="78407-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="78407-107">对于区域性敏感型大小写更改，请为 `culture` 参数指定 `CultureInfo.CurrentCulture`。</span><span class="sxs-lookup"><span data-stu-id="78407-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="78407-108">对于非区域性敏感型大小写更改，请为 `culture` 参数指定 `CultureInfo.InvariantCulture`。</span><span class="sxs-lookup"><span data-stu-id="78407-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="78407-109">通常情况下，字符串会转换为标准大小写，以方便稍后查找。</span><span class="sxs-lookup"><span data-stu-id="78407-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="78407-110">如果按这种方式使用字符串，应为 `culture` 参数指定 `CultureInfo.InvariantCulture`，因为 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 的值可能会在大小写更改和执行查找时之间变化。</span><span class="sxs-lookup"><span data-stu-id="78407-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="78407-111">如果安全决策以大小写更改操作为依据，操作应为非区域性敏感型，以确保结果不受 `CultureInfo.CurrentCulture` 值的影响。</span><span class="sxs-lookup"><span data-stu-id="78407-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="78407-112">有关展示了区域性敏感型字符串操作如何产生不一致结果的示例，请参阅[字符串使用最佳做法](../base-types/best-practices-strings.md)的“使用当前区域性的字符串比较”部分。</span><span class="sxs-lookup"><span data-stu-id="78407-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="78407-113">使用 String.ToUpper 和 String.ToLower 方法</span><span class="sxs-lookup"><span data-stu-id="78407-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="78407-114">为了代码清楚起见，建议始终使用 `String.ToUpper` 和 `String.ToLower` 方法重载，以便显式指定 `culture` 参数。</span><span class="sxs-lookup"><span data-stu-id="78407-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="78407-115">例如，下面的代码执行标识符查找。</span><span class="sxs-lookup"><span data-stu-id="78407-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="78407-116">默认情况下，`key.ToLower` 操作为区域性敏感型，但此行为并未通过读取代码明确。</span><span class="sxs-lookup"><span data-stu-id="78407-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="78407-117">示例</span><span class="sxs-lookup"><span data-stu-id="78407-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="78407-118">如果希望 `key.ToLower` 操作为非区域性敏感型，应按照以下所述更改上一示例，以便在更改大小写时显式使用 `CultureInfo.InvariantCulture`。</span><span class="sxs-lookup"><span data-stu-id="78407-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="78407-119">使用 Char.ToUpper 和 Char.ToLower 方法</span><span class="sxs-lookup"><span data-stu-id="78407-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="78407-120">尽管 `Char.ToUpper` 和 `Char.ToLower` 方法的特性与 `String.ToUpper` 和 `String.ToLower` 方法相同，但受影响的区域性只有土尔其语（土尔其）和阿塞拜疆语（拉丁，阿塞拜疆）。</span><span class="sxs-lookup"><span data-stu-id="78407-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="78407-121">这些是唯一两个存在单字符大小写差异的区域性。</span><span class="sxs-lookup"><span data-stu-id="78407-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="78407-122">有关此唯一大小写映射的详细信息，请参阅 <xref:System.String> 类主题中的“大小写”部分。</span><span class="sxs-lookup"><span data-stu-id="78407-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="78407-123">为了代码清楚起见，并确保结果一致，建议始终使用这些方法重载，以便显式指定 `culture` 参数。</span><span class="sxs-lookup"><span data-stu-id="78407-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78407-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78407-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="78407-125">执行不区分区域性的字符串操作</span><span class="sxs-lookup"><span data-stu-id="78407-125">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
