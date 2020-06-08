---
title: CorSymSearchPolicyAttributes 枚举
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 8af71314cf8a24c710d3b8980c082daaf9186715
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501867"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="e5779-102">CorSymSearchPolicyAttributes 枚举</span><span class="sxs-lookup"><span data-stu-id="e5779-102">CorSymSearchPolicyAttributes Enumeration</span></span>
<span data-ttu-id="e5779-103">指定在搜索符号读取器时要使用的策略。</span><span class="sxs-lookup"><span data-stu-id="e5779-103">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="e5779-104">[ISymUnmanagedBinder2：： GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md)和[ISymUnmanagedBinder3：： GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md)方法使用这些常量。</span><span class="sxs-lookup"><span data-stu-id="e5779-104">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e5779-105">打开不受信任的源中的程序数据库（PDB）文件会带来安全风险。</span><span class="sxs-lookup"><span data-stu-id="e5779-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5779-106">语法</span><span class="sxs-lookup"><span data-stu-id="e5779-106">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="e5779-107">成员</span><span class="sxs-lookup"><span data-stu-id="e5779-107">Members</span></span>  
  
|<span data-ttu-id="e5779-108">成员</span><span class="sxs-lookup"><span data-stu-id="e5779-108">Member</span></span>|<span data-ttu-id="e5779-109">描述</span><span class="sxs-lookup"><span data-stu-id="e5779-109">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="e5779-110">在注册表中查询符号搜索路径。</span><span class="sxs-lookup"><span data-stu-id="e5779-110">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="e5779-111">访问符号服务器。</span><span class="sxs-lookup"><span data-stu-id="e5779-111">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="e5779-112">搜索在调试目录中指定的路径。</span><span class="sxs-lookup"><span data-stu-id="e5779-112">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="e5779-113">搜索 .exe 文件所在位置的 PDB。</span><span class="sxs-lookup"><span data-stu-id="e5779-113">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5779-114">要求</span><span class="sxs-lookup"><span data-stu-id="e5779-114">Requirements</span></span>  
 <span data-ttu-id="e5779-115">**标头：** CorSym，CorSym</span><span class="sxs-lookup"><span data-stu-id="e5779-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5779-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5779-116">See also</span></span>

- [<span data-ttu-id="e5779-117">诊断符号存储区枚举</span><span class="sxs-lookup"><span data-stu-id="e5779-117">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
