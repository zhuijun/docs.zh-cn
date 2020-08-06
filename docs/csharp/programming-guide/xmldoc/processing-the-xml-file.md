---
title: 处理 XML 文件 - C# 编程指南
description: 了解如何在 C# 编程中处理 XML 文件。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 6f8a278ed842cd9c4176f3efff423ee048f7e9b9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381536"
---
# <a name="process-the-xml-file-c-programming-guide"></a><span data-ttu-id="817d0-104">处理 XML 文件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="817d0-104">Process the XML file (C# programming guide)</span></span>

<span data-ttu-id="817d0-105">编译器为代码（已标记以生成文档）中的每个构造生成一个 ID 字符串。</span><span class="sxs-lookup"><span data-stu-id="817d0-105">The compiler generates an ID string for each construct in your code that's tagged to generate documentation.</span></span> <span data-ttu-id="817d0-106">（有关如何标记代码的信息，请参阅[文档注释的建议标记](./recommended-tags-for-documentation-comments.md)。）ID 字符串唯一标识构造。</span><span class="sxs-lookup"><span data-stu-id="817d0-106">(For information about how to tag your code, see [Recommended Tags for Documentation Comments](./recommended-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="817d0-107">处理 XML 文件的程序可以使用 ID 字符串来标识文档应用于的相应 .NET 元数据或反射项目。</span><span class="sxs-lookup"><span data-stu-id="817d0-107">Programs that process the XML file can use the ID string to identify the corresponding .NET metadata or reflection item that the documentation applies to.</span></span>

## <a name="id-strings"></a><span data-ttu-id="817d0-108">ID 字符串</span><span class="sxs-lookup"><span data-stu-id="817d0-108">ID strings</span></span>

<span data-ttu-id="817d0-109">XML 文件不是代码的层次结构表示形式。</span><span class="sxs-lookup"><span data-stu-id="817d0-109">The XML file is not a hierarchical representation of your code.</span></span> <span data-ttu-id="817d0-110">它是一个简单列表，其中每个元素都有一个生成 ID。</span><span class="sxs-lookup"><span data-stu-id="817d0-110">It's a flat list that has a generated ID for each element.</span></span>

<span data-ttu-id="817d0-111">编译器在生成 ID 字符串时应遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="817d0-111">The compiler observes the following rules when it generates the ID strings:</span></span>

- <span data-ttu-id="817d0-112">字符串不得包含空白符。</span><span class="sxs-lookup"><span data-stu-id="817d0-112">No white space is in the string.</span></span>

- <span data-ttu-id="817d0-113">该字符串的第一部分使用单个字符后跟冒号来标识成员类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-113">The first part of the string identifies the kind of member using a single character followed by a colon.</span></span> <span data-ttu-id="817d0-114">使用下面的成员类型：</span><span class="sxs-lookup"><span data-stu-id="817d0-114">The following member types are used:</span></span>

    |<span data-ttu-id="817d0-115">字符</span><span class="sxs-lookup"><span data-stu-id="817d0-115">Character</span></span>|<span data-ttu-id="817d0-116">成员类型</span><span class="sxs-lookup"><span data-stu-id="817d0-116">Member type</span></span>|<span data-ttu-id="817d0-117">说明</span><span class="sxs-lookup"><span data-stu-id="817d0-117">Notes</span></span>|
    |---------------|-----------------|-|
    |<span data-ttu-id="817d0-118">N</span><span class="sxs-lookup"><span data-stu-id="817d0-118">N</span></span>|<span data-ttu-id="817d0-119">namespace</span><span class="sxs-lookup"><span data-stu-id="817d0-119">namespace</span></span>|<span data-ttu-id="817d0-120">无法将文档注释添加到命名空间中，但可以在支持的情况下对它们进行 cref 引用。</span><span class="sxs-lookup"><span data-stu-id="817d0-120">You cannot add documentation comments to a namespace, but you can make cref references to them, where supported.</span></span>|
    |<span data-ttu-id="817d0-121">T</span><span class="sxs-lookup"><span data-stu-id="817d0-121">T</span></span>|<span data-ttu-id="817d0-122">type</span><span class="sxs-lookup"><span data-stu-id="817d0-122">type</span></span>|<span data-ttu-id="817d0-123">类型可能是类、接口、结构、枚举或委托。</span><span class="sxs-lookup"><span data-stu-id="817d0-123">A type can be a class, interface, struct, enum, or delegate.</span></span>|
    |<span data-ttu-id="817d0-124">F</span><span class="sxs-lookup"><span data-stu-id="817d0-124">F</span></span>|<span data-ttu-id="817d0-125">Field — 字段</span><span class="sxs-lookup"><span data-stu-id="817d0-125">field</span></span>|
    |<span data-ttu-id="817d0-126">P</span><span class="sxs-lookup"><span data-stu-id="817d0-126">P</span></span>|<span data-ttu-id="817d0-127">property</span><span class="sxs-lookup"><span data-stu-id="817d0-127">property</span></span>|<span data-ttu-id="817d0-128">包括索引器或其他索引属性。</span><span class="sxs-lookup"><span data-stu-id="817d0-128">Includes indexers or other indexed properties.</span></span>|
    |<span data-ttu-id="817d0-129">M</span><span class="sxs-lookup"><span data-stu-id="817d0-129">M</span></span>|<span data-ttu-id="817d0-130">method</span><span class="sxs-lookup"><span data-stu-id="817d0-130">method</span></span>|<span data-ttu-id="817d0-131">包括特殊方法，如构造函数和运算符。</span><span class="sxs-lookup"><span data-stu-id="817d0-131">Includes special methods, such as constructors and operators.</span></span>|
    |<span data-ttu-id="817d0-132">E</span><span class="sxs-lookup"><span data-stu-id="817d0-132">E</span></span>|<span data-ttu-id="817d0-133">event</span><span class="sxs-lookup"><span data-stu-id="817d0-133">event</span></span>|
    |<span data-ttu-id="817d0-134">!</span><span class="sxs-lookup"><span data-stu-id="817d0-134">!</span></span>|<span data-ttu-id="817d0-135">错误字符串</span><span class="sxs-lookup"><span data-stu-id="817d0-135">error string</span></span>|<span data-ttu-id="817d0-136">字符串的其余部分提供有关错误的信息。</span><span class="sxs-lookup"><span data-stu-id="817d0-136">The rest of the string provides information about the error.</span></span> <span data-ttu-id="817d0-137">C# 编译器将生成无法解析的链接的错误信息。</span><span class="sxs-lookup"><span data-stu-id="817d0-137">The C# compiler generates error information for links that cannot be resolved.</span></span>|

- <span data-ttu-id="817d0-138">该字符串的第二部分是项目的完全限定名称，从命名空间的根开始。</span><span class="sxs-lookup"><span data-stu-id="817d0-138">The second part of the string is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="817d0-139">用句点分隔项目名称、其封闭类型和命名空间。</span><span class="sxs-lookup"><span data-stu-id="817d0-139">The name of the item, its enclosing type(s), and namespace are separated by periods.</span></span> <span data-ttu-id="817d0-140">如果项目名称本身包含句点，会将其替换为哈希符号 ('#')。</span><span class="sxs-lookup"><span data-stu-id="817d0-140">If the name of the item itself has periods, they are replaced by the hash-sign ('#').</span></span> <span data-ttu-id="817d0-141">假定没有名称中恰好包含哈希符号的项目。</span><span class="sxs-lookup"><span data-stu-id="817d0-141">It's assumed that no item has a hash-sign directly in its name.</span></span> <span data-ttu-id="817d0-142">例如，String 构造函数的完全限定名称是“System.String.#ctor”。</span><span class="sxs-lookup"><span data-stu-id="817d0-142">For example, the fully qualified name of the String constructor is "System.String.#ctor".</span></span>

- <span data-ttu-id="817d0-143">对于属性和方法，括号内的参数列表如下。</span><span class="sxs-lookup"><span data-stu-id="817d0-143">For properties and methods, the parameter list enclosed in parentheses follows.</span></span> <span data-ttu-id="817d0-144">如果没有任何参数，则不会出现括号。</span><span class="sxs-lookup"><span data-stu-id="817d0-144">If there are no parameters, no parentheses are present.</span></span> <span data-ttu-id="817d0-145">这些参数以逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="817d0-145">The parameters are separated by commas.</span></span> <span data-ttu-id="817d0-146">每个参数的编码直接遵循它在 .NET 签名中的编码方式：</span><span class="sxs-lookup"><span data-stu-id="817d0-146">The encoding of each parameter follows directly how it's encoded in a .NET signature:</span></span>

  - <span data-ttu-id="817d0-147">基类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-147">Base types.</span></span> <span data-ttu-id="817d0-148">常规的类型（ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE）表示为该类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="817d0-148">Regular types (ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE) are represented as the fully qualified name of the type.</span></span>

  - <span data-ttu-id="817d0-149">内部类型（例如，ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF 和 ELEMENT_TYPE_VOID）表示为相应完整类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="817d0-149">Intrinsic types (for example, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF, and ELEMENT_TYPE_VOID) are represented as the fully qualified name of the corresponding full type.</span></span> <span data-ttu-id="817d0-150">例如，System.Int32 或 System.TypedReference。</span><span class="sxs-lookup"><span data-stu-id="817d0-150">For example, System.Int32 or System.TypedReference.</span></span>

  - <span data-ttu-id="817d0-151">ELEMENT_TYPE_PTR 表示为修改类型之后的“\*”。</span><span class="sxs-lookup"><span data-stu-id="817d0-151">ELEMENT_TYPE_PTR is represented as a '\*' following the modified type.</span></span>

  - <span data-ttu-id="817d0-152">ELEMENT_TYPE_BYREF 表示为修改类型之后的“\@”。</span><span class="sxs-lookup"><span data-stu-id="817d0-152">ELEMENT_TYPE_BYREF is represented as a '\@' following the modified type.</span></span>

  - <span data-ttu-id="817d0-153">ELEMENT_TYPE_PINNED 表示为修改类型之后的“^”。</span><span class="sxs-lookup"><span data-stu-id="817d0-153">ELEMENT_TYPE_PINNED is represented as a '^' following the modified type.</span></span> <span data-ttu-id="817d0-154">C# 编译器不会生成此类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-154">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="817d0-155">ELEMENT_TYPE_CMOD_REQ 表示为“&#124;”和修饰符类的完全限定名称，前面是修改类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-155">ELEMENT_TYPE_CMOD_REQ is represented as a '&#124;' and the fully qualified name of the modifier class, following the modified type.</span></span> <span data-ttu-id="817d0-156">C# 编译器不会生成此类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-156">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="817d0-157">ELEMENT_TYPE_CMOD_OPT 表示为“!”和修饰符类的完全限定名称，前面是修改类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-157">ELEMENT_TYPE_CMOD_OPT is represented as a '!' and the fully qualified name of the modifier class, following the modified type.</span></span>

  - <span data-ttu-id="817d0-158">ELEMENT_TYPE_SZARRAY 表示为“[]”，前面是数组的元素类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-158">ELEMENT_TYPE_SZARRAY is represented as "[]" following the element type of the array.</span></span>

  - <span data-ttu-id="817d0-159">ELEMENT_TYPE_GENERICARRAY 表示为“[?]”，前面是数组的元素类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-159">ELEMENT_TYPE_GENERICARRAY is represented as "[?]" following the element type of the array.</span></span> <span data-ttu-id="817d0-160">C# 编译器不会生成此类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-160">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="817d0-161">ELEMENT_TYPE_ARRAY 表示为 [*lowerbound*:`size`,*lowerbound*:`size`]，其中逗号的数量是秩 - 1，每个维度的下限和大小（如果已知）以十进制形式表示。</span><span class="sxs-lookup"><span data-stu-id="817d0-161">ELEMENT_TYPE_ARRAY is represented as [*lowerbound*:`size`,*lowerbound*:`size`] where the number of commas is the rank - 1, and the lower bounds and size of each dimension, if known, are represented in decimal.</span></span> <span data-ttu-id="817d0-162">如果未指定下限或大小，则将其省略。</span><span class="sxs-lookup"><span data-stu-id="817d0-162">If a lower bound or size is not specified, it's omitted.</span></span> <span data-ttu-id="817d0-163">如果省略某个特定维度的下限和大小，也会省略“:”。</span><span class="sxs-lookup"><span data-stu-id="817d0-163">If the lower bound and size for a particular dimension are omitted, the ':' is omitted as well.</span></span> <span data-ttu-id="817d0-164">例如，以 1 作为下限并且未指定大小的二维数组是 [1:,1:]。</span><span class="sxs-lookup"><span data-stu-id="817d0-164">For example, a 2-dimensional array with 1 as the lower bounds and unspecified sizes is [1:,1:].</span></span>

  - <span data-ttu-id="817d0-165">ELEMENT_TYPE_FNPTR 表示为“=FUNC:`type`(*signature*)”，其中 `type` 是返回类型，*signature* 是方法的自变量。</span><span class="sxs-lookup"><span data-stu-id="817d0-165">ELEMENT_TYPE_FNPTR is represented as "=FUNC:`type`(*signature*)", where `type` is the return type, and *signature* is the arguments of the method.</span></span> <span data-ttu-id="817d0-166">如果没有任何自变量，则省略括号。</span><span class="sxs-lookup"><span data-stu-id="817d0-166">If there are no arguments, the parentheses are omitted.</span></span> <span data-ttu-id="817d0-167">C# 编译器不会生成此类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-167">The C# compiler never generates this.</span></span>

  <span data-ttu-id="817d0-168">不表示下列签名组件，因为它们不会用于区分重载方法：</span><span class="sxs-lookup"><span data-stu-id="817d0-168">The following signature components aren't represented because they aren't used to differentiate overloaded methods:</span></span>

  - <span data-ttu-id="817d0-169">调用约定</span><span class="sxs-lookup"><span data-stu-id="817d0-169">calling convention</span></span>

  - <span data-ttu-id="817d0-170">返回类型</span><span class="sxs-lookup"><span data-stu-id="817d0-170">return type</span></span>

  - <span data-ttu-id="817d0-171">ELEMENT_TYPE_SENTINEL</span><span class="sxs-lookup"><span data-stu-id="817d0-171">ELEMENT_TYPE_SENTINEL</span></span>

- <span data-ttu-id="817d0-172">仅针对转换运算符（`op_Implicit` 和 `op_Explicit`），该方法的返回值被编码为“~”，后面是返回类型。</span><span class="sxs-lookup"><span data-stu-id="817d0-172">For conversion operators only (`op_Implicit` and `op_Explicit`), the return value of the method is encoded as a '~' followed by the return type.</span></span>

- <span data-ttu-id="817d0-173">对于泛型类型，类型名称后跟反引号，然后是指示泛型类型参数数量的一个数字。</span><span class="sxs-lookup"><span data-stu-id="817d0-173">For generic types, the name of the type is followed by a backtick and then a number that indicates the number of generic type parameters.</span></span> <span data-ttu-id="817d0-174">例如：</span><span class="sxs-lookup"><span data-stu-id="817d0-174">For example:</span></span>

     <span data-ttu-id="817d0-175">``<member name="T:SampleClass`2">`` 是定义为 `public class SampleClass<T, U>` 的类型的标记。</span><span class="sxs-lookup"><span data-stu-id="817d0-175">``<member name="T:SampleClass`2">`` is the tag for a type that is defined as `public class SampleClass<T, U>`.</span></span>

     <span data-ttu-id="817d0-176">对于将泛型类型用作参数的方法，泛型类型参数被指定为前面加上反引号的数字（例如 \`0、\`1）。</span><span class="sxs-lookup"><span data-stu-id="817d0-176">For methods that take generic types as parameters, the generic type parameters are specified as numbers prefaced with backticks (for example \`0,\`1).</span></span> <span data-ttu-id="817d0-177">每个数字表示该类型的泛型参数的从零开始的数组表示法。</span><span class="sxs-lookup"><span data-stu-id="817d0-177">Each number represents a zero-based array notation for the type's generic parameters.</span></span>

## <a name="examples"></a><span data-ttu-id="817d0-178">示例</span><span class="sxs-lookup"><span data-stu-id="817d0-178">Examples</span></span>

<span data-ttu-id="817d0-179">下面的示例演示如何为类及其成员生成 ID 字符串：</span><span class="sxs-lookup"><span data-stu-id="817d0-179">The following examples show how the ID strings for a class and its members are generated:</span></span>

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a><span data-ttu-id="817d0-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="817d0-180">See also</span></span>

- [<span data-ttu-id="817d0-181">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="817d0-181">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="817d0-182">-doc（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="817d0-182">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="817d0-183">XML 文档注释</span><span class="sxs-lookup"><span data-stu-id="817d0-183">XML documentation comments</span></span>](./index.md)
