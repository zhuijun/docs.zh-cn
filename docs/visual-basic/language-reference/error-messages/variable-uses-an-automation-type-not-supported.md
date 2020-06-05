---
title: 变量使用了不支持的自动化类型
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 7d52189e31823b63547c757434847c0e1717aada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406542"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="815a3-102">变量使用了 Visual Basic 不支持的自动化类型</span><span class="sxs-lookup"><span data-stu-id="815a3-102">Variable uses an Automation type not supported in Visual Basic</span></span>

<span data-ttu-id="815a3-103">尝试使用类型库或对象库中定义的变量，该变量的数据类型不受 Visual Basic 支持。</span><span class="sxs-lookup"><span data-stu-id="815a3-103">You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="815a3-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="815a3-104">To correct this error</span></span>

- <span data-ttu-id="815a3-105">使用 Visual Basic 可识别的类型的变量。</span><span class="sxs-lookup"><span data-stu-id="815a3-105">Use a variable of a type recognized by Visual Basic.</span></span>

     <span data-ttu-id="815a3-106">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="815a3-106">-or-</span></span>

- <span data-ttu-id="815a3-107">如果你在使用或时遇到此错误 `FileGet` `FileGetObject` ，请确保你尝试使用的文件已使用 `FilePut` 或写入 `FilePutObject` 。</span><span class="sxs-lookup"><span data-stu-id="815a3-107">If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>

## <a name="see-also"></a><span data-ttu-id="815a3-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="815a3-108">See also</span></span>

- [<span data-ttu-id="815a3-109">数据类型</span><span class="sxs-lookup"><span data-stu-id="815a3-109">Data Types</span></span>](../data-types/index.md)
