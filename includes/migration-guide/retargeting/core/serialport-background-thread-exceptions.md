---
ms.openlocfilehash: e66a5c2a33a4ab5cf35013c1843936ffd01f90a2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614359"
---
### <a name="serialport-background-thread-exceptions"></a><span data-ttu-id="9042d-101">SerialPort 后台线程异常</span><span class="sxs-lookup"><span data-stu-id="9042d-101">SerialPort background thread exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="9042d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9042d-102">Details</span></span>

<span data-ttu-id="9042d-103">使用 <xref:System.IO.Ports.SerialPort> 流创建的后台线程不再在引发 OS 异常时终止进程。</span><span class="sxs-lookup"><span data-stu-id="9042d-103">Background threads created with <xref:System.IO.Ports.SerialPort> streams no longer terminate the process when OS exceptions are thrown.</span></span> <br/><span data-ttu-id="9042d-104">在面向 .NET Framework 4.7 及更早版本的应用程序中，使用 <xref:System.IO.Ports.SerialPort> 流创建的后台线程上引发操作系统异常时，会终止进程。</span><span class="sxs-lookup"><span data-stu-id="9042d-104">In applications that target the .NET Framework 4.7 and earlier versions, a process is terminated when an operating system exception is thrown on a background thread created with a <xref:System.IO.Ports.SerialPort> stream.</span></span> <br/><span data-ttu-id="9042d-105">在面向 .NET Framework 4.7.1 或更高版本的应用程序中，后台线程等待与活动串行端口相关的 OS 事件，在某些情况下（例如突然删除串行端口）也可能崩溃。</span><span class="sxs-lookup"><span data-stu-id="9042d-105">In applications that target the .NET Framework 4.7.1 or a later version, background threads wait for OS events related to the active serial port and could crash in some cases, such as sudden removal of the serial port.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9042d-106">建议</span><span class="sxs-lookup"><span data-stu-id="9042d-106">Suggestion</span></span>

<span data-ttu-id="9042d-107">对于面向 .NET Framework 4.7.1 的应用，如果无需异常处理，可通过将以下内容添加到 `app.config` 文件的 `<runtime>` 部分，从而选择不用异常处理：</span><span class="sxs-lookup"><span data-stu-id="9042d-107">For apps that target the .NET Framework 4.7.1, you can opt out of the exception handling if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true" />
</runtime>
```

<span data-ttu-id="9042d-108">对于面向旧版 .NET Framework，但在 .NET Framework 4.7.1 或更高版本上运行的应用，可通过将以下内容添加到 `app.config` 文件的 `<runtime>` 部分来选择使用异常处理：</span><span class="sxs-lookup"><span data-stu-id="9042d-108">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.1 or later, you can opt in to the exception handling by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false" />
</runtime>
```

| <span data-ttu-id="9042d-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="9042d-109">Name</span></span>    | <span data-ttu-id="9042d-110">值</span><span class="sxs-lookup"><span data-stu-id="9042d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9042d-111">范围</span><span class="sxs-lookup"><span data-stu-id="9042d-111">Scope</span></span>   | <span data-ttu-id="9042d-112">次要</span><span class="sxs-lookup"><span data-stu-id="9042d-112">Minor</span></span>       |
| <span data-ttu-id="9042d-113">Version</span><span class="sxs-lookup"><span data-stu-id="9042d-113">Version</span></span> | <span data-ttu-id="9042d-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="9042d-114">4.7.1</span></span>       |
| <span data-ttu-id="9042d-115">类型</span><span class="sxs-lookup"><span data-stu-id="9042d-115">Type</span></span>    | <span data-ttu-id="9042d-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="9042d-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="9042d-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9042d-117">Affected APIs</span></span>

- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
