---
title: 异常处理 - C# 编程指南
description: 了解异常处理。 请参阅 try-catch、try-finally 和 try-catch-finally 语句的示例。
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 8e55b44573c40f594e567fc5a4501689e66c7af4
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302030"
---
# <a name="exception-handling-c-programming-guide"></a>异常处理（C# 编程指南）
C# 程序员使用 [try](../../language-reference/keywords/try-catch.md) 块来对可能受异常影响的代码进行分区。 关联的 [catch](../../language-reference/keywords/try-catch.md) 块用于处理生成的任何异常。 [finally](../../language-reference/keywords/try-finally.md) 块包含无论 `try` 块中是否引发异常都会运行的代码，如发布 `try` 块中分配的资源。 `try` 块需要一个或多个关联的 `catch` 块或一个 `finally` 块，或两者皆之。  
  
 下面的示例演示 `try-catch` 语句、`try-finally` 语句和 `try-catch-finally` 语句。  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 一个不具有 `catch` 或 `finally` 块的 `try` 块会导致编译器错误。  
  
## <a name="catch-blocks"></a>catch 块  
 `catch` 块可以指定要捕获的异常的类型。 该类型规范称为异常筛选器。 异常类型应派生自 <xref:System.Exception>。 一般情况下，不要将 <xref:System.Exception> 指定为异常筛选器，除非了解如何处理可能在 `try` 块中引发的所有异常，或者已在 `catch` 块的末尾处包括了 [throw](../../language-reference/keywords/throw.md) 语句。  
  
 可将具有不同异常筛选器的多个 `catch` 块链接在一起。 代码中 `catch` 块的计算顺序为从上到下，但针对引发的每个异常，仅执行一个 `catch` 块。 将执行指定所引发的异常的确切类型或基类的第一个 `catch` 块。 如果没有 `catch` 块指定匹配的异常筛选器，则将选择不具有筛选器的 `catch` 块（如果语句中存在）。 务必首先定位具有最具体的（即，最底层派生的）异常类型的 `catch` 块。  
  
 应当会在下列条件为 true 时捕获到异常：  
  
- 能够很好地理解可能会引发异常的原因，并且可以实现特定的恢复，例如捕获 <xref:System.IO.FileNotFoundException> 对象时提示用户输入新文件名。  
  
- 可以创建和引发一个新的、更具体的异常。  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- 想要先对异常进行部分处理，然后再将其传递以进行额外处理。 在下面的示例中，`catch` 块用于在重新引发异常之前将条目添加到错误日志。  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Finally 块  
 `finally` 块让你可以清理在 `try` 块中所执行的操作。 如果存在 `finally` 块，将在执行 `try` 块和任何匹配的 `catch` 块之后，最后执行它。 无论是否会引发异常或找到匹配异常类型的 `catch` 块，`finally` 块都将始终运行。  
  
 `finally` 块可用于发布资源（如文件流、数据库连接和图形句柄）而无需等待运行时中的垃圾回收器来完成对象。 有关详细信息，请参阅 [using 语句](../../language-reference/keywords/using-statement.md)。  
  
 在下面的示例中，`finally` 块用于关闭在 `try` 块中打开的文件。 请注意，在关闭文件之前，将检查文件句柄的状态。 如果 `try` 块不能打开文件，则文件句柄仍将具有值 `null` 且 `finally` 块不会尝试将其关闭。 或者，如果在 `try` 块中成功打开文件，则 `finally` 块将关闭打开的文件。  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>C# 语言规范  

有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[异常](~/_csharplang/spec/exceptions.md)和 [try 语句](~/_csharplang/spec/statements.md#the-try-statement)。 该语言规范是 C# 语法和用法的权威资料。
  
## <a name="see-also"></a>请参阅

- [C# 参考](../../language-reference/index.md)
- [C# 编程指南](../index.md)
- [异常和异常处理](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using 语句](../../language-reference/keywords/using-statement.md)
