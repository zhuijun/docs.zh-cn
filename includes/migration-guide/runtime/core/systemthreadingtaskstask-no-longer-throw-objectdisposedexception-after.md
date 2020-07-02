---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619842"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>释放对象后，System.Threading.Tasks.Task 不再引发 ObjectDisposedException

#### <a name="details"></a>详细信息

除 <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> 外，<xref:System.Threading.Tasks.Task?displayProperty=fullName> 方法在处置对象后不再引发 <xref:System.ObjectDisposedException?displayProperty=fullName> 异常。此更改支持使用缓存任务。 例如，方法会返回一个缓存任务来表示已完成的操作，而不是分配新任务。 在以前的 .NET Framework 版本中无法执行此操作，因为任务的任何使用者都可以处置它（呈现为不可用）。

#### <a name="suggestion"></a>建议

请注意，如果释放对象，Task 方法可能不再引发 <xref:System.ObjectDisposedException?displayProperty=fullName>。 如果某个应用依靠此异常了解任务是否已释放，应对其进行更新以使用 <xref:System.Threading.Tasks.Task.Status> 显式检查任务状态。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.5|
|类型|运行时|
