---
title: ISymUnmanagedBinder2 接口
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501828"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="da994-102">ISymUnmanagedBinder2 接口</span><span class="sxs-lookup"><span data-stu-id="da994-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="da994-103">表示非托管代码的符号联编程序，并扩展[ISymUnmanagedBinder](isymunmanagedbinder-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="da994-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="da994-104">打开不受信任的源中的程序数据库（PDB）文件会带来安全风险。</span><span class="sxs-lookup"><span data-stu-id="da994-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da994-105">方法</span><span class="sxs-lookup"><span data-stu-id="da994-105">Methods</span></span>  
  
|<span data-ttu-id="da994-106">方法</span><span class="sxs-lookup"><span data-stu-id="da994-106">Method</span></span>|<span data-ttu-id="da994-107">说明</span><span class="sxs-lookup"><span data-stu-id="da994-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da994-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="da994-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="da994-109">给定元数据接口和文件名后，将返回正确的[ISymUnmanagedReader](isymunmanagedreader-interface.md)接口，该接口将读取与模块关联的调试符号。</span><span class="sxs-lookup"><span data-stu-id="da994-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="da994-110">与[ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)方法相比，提供的搜索范围更广。</span><span class="sxs-lookup"><span data-stu-id="da994-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da994-111">要求</span><span class="sxs-lookup"><span data-stu-id="da994-111">Requirements</span></span>  
 <span data-ttu-id="da994-112">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="da994-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da994-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da994-113">See also</span></span>

- [<span data-ttu-id="da994-114">诊断符号存储区接口</span><span class="sxs-lookup"><span data-stu-id="da994-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="da994-115">ISymUnmanagedBinder 接口</span><span class="sxs-lookup"><span data-stu-id="da994-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="da994-116">ISymUnmanagedBinder3 接口</span><span class="sxs-lookup"><span data-stu-id="da994-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
