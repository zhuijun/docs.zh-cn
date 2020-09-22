---
title: 错误的记录长度
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869264"
---
# <a name="bad-record-length"></a><span data-ttu-id="86caa-102">错误的记录长度</span><span class="sxs-lookup"><span data-stu-id="86caa-102">Bad record length</span></span>

<span data-ttu-id="86caa-103">此错误的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="86caa-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="86caa-104">、或语句中指定的记录变量的 `FileGet` 长度 `FileGetObject` `FilePut` `FilePutObject` 与相应语句中指定的长度不同 `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="86caa-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="86caa-105">或语句中的 `FilePut` 变量 `FilePutObject` 为或包含可变长度字符串。</span><span class="sxs-lookup"><span data-stu-id="86caa-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="86caa-106">或中的变量 `FilePut` `FilePutObject` 为或包含 `Variant` 类型。</span><span class="sxs-lookup"><span data-stu-id="86caa-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86caa-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="86caa-107">To correct this error</span></span>  
  
1. <span data-ttu-id="86caa-108">请确保定义记录变量类型的用户定义类型中的固定长度变量大小的总和与语句的子句中所述的值相同 `FileOpen` `Len` 。</span><span class="sxs-lookup"><span data-stu-id="86caa-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="86caa-109">如果或语句中的 `FilePut` 变量 `FilePutObject` 为或包含可变长度字符串，请确保可变长度字符串至少比语句的子句中指定的记录长度少2个字符 `Len` `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="86caa-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="86caa-110">如果或中的变量 `FilePut` `FilePutObject` 为或包含， `Variant` 请确保长度可变的字符串至少比语句的子句中指定的记录长度少4个字节 `Len` `FileOpen` 。</span><span class="sxs-lookup"><span data-stu-id="86caa-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86caa-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86caa-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
