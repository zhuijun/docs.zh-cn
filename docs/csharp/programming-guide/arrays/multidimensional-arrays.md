---
title: 多维数组 - C# 编程指南
description: C# 中的数组可具有多个维度。 此示例声明创建一个具有四行两列的二维数组。
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475003"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="6f06a-104">多维数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="6f06a-104">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="6f06a-105">数组可具有多个维度。</span><span class="sxs-lookup"><span data-stu-id="6f06a-105">Arrays can have more than one dimension.</span></span> <span data-ttu-id="6f06a-106">例如，以下声明创建一个具有四行两列的二维数组。</span><span class="sxs-lookup"><span data-stu-id="6f06a-106">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="6f06a-107">以下声明创建一个具有三个维度（4、2 和 3）的数组。</span><span class="sxs-lookup"><span data-stu-id="6f06a-107">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="6f06a-108">数组初始化</span><span class="sxs-lookup"><span data-stu-id="6f06a-108">Array Initialization</span></span>

 <span data-ttu-id="6f06a-109">声明后即可初始化数组，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="6f06a-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="6f06a-110">还可在不指定级别的情况下初始化数组。</span><span class="sxs-lookup"><span data-stu-id="6f06a-110">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="6f06a-111">如果选择在不初始化的情况下声明数组变量，则必须使用 `new` 运算符将数组赋予变量。</span><span class="sxs-lookup"><span data-stu-id="6f06a-111">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="6f06a-112">`new` 的用法如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="6f06a-112">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="6f06a-113">以下示例将值赋予特定的数组元素。</span><span class="sxs-lookup"><span data-stu-id="6f06a-113">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="6f06a-114">同样，以下示例将获取特定数组元素的值并将其赋予变量 `elementValue`。</span><span class="sxs-lookup"><span data-stu-id="6f06a-114">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="6f06a-115">以下代码示例将数组元素初始化为默认值（交错数组除外）。</span><span class="sxs-lookup"><span data-stu-id="6f06a-115">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="6f06a-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f06a-116">See also</span></span>

- [<span data-ttu-id="6f06a-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6f06a-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6f06a-118">数组</span><span class="sxs-lookup"><span data-stu-id="6f06a-118">Arrays</span></span>](./index.md)
- [<span data-ttu-id="6f06a-119">一维数组</span><span class="sxs-lookup"><span data-stu-id="6f06a-119">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="6f06a-120">交错数组</span><span class="sxs-lookup"><span data-stu-id="6f06a-120">Jagged Arrays</span></span>](./jagged-arrays.md)
