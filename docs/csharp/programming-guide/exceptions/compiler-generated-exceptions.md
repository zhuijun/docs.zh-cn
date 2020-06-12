---
title: 编译器生成的异常 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 1d2d561df3e496893657b050fa93b44c56542d97
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240722"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>编译器生成的异常（C# 编程指南）

当基本操作失败时，.NET 运行时会自动引发一些异常。 这些异常及其错误条件在下表中列出。  
  
|例外|描述|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|算术运算期间出现的异常的基类，例如 <xref:System.DivideByZeroException> 和 <xref:System.OverflowException>。|  
|<xref:System.ArrayTypeMismatchException>|由于元素的实际类型与数组的实际类型不兼容而导致数组无法存储给定元素时引发。|  
|<xref:System.DivideByZeroException>|尝试将整数值除以零时引发。|  
|<xref:System.IndexOutOfRangeException>|索引小于零或超出数组边界时，尝试对数组编制索引时引发。|  
|<xref:System.InvalidCastException>|从基类型显式转换为接口或派生类型在运行时失败时引发。|  
|<xref:System.NullReferenceException>|尝试引用值为 [null](../../language-reference/keywords/null.md) 的对象时引发。|  
|<xref:System.OutOfMemoryException>|尝试使用[新](../../language-reference/operators/new-operator.md)运算符分配内存失败时引发。 这表示可用于公共语言运行时的内存已用尽。|  
|<xref:System.OverflowException>|`checked` 上下文中的算术运算溢出时引发。|  
|<xref:System.StackOverflowException>|执行堆栈由于有过多挂起的方法调用而用尽时引发；通常表示非常深的递归或无限递归。|  
|<xref:System.TypeInitializationException>|静态构造函数引发异常并且没有兼容的 `catch` 子句来捕获异常时引发。|  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [异常和异常处理](./index.md)
- [异常处理](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
