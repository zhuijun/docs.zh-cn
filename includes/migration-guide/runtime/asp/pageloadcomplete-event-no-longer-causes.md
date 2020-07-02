---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619821"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Page.LoadComplete 事件不再导致 System.Web.UI.WebControls.EntityDataSource 控件调用数据绑定

#### <a name="details"></a>详细信息

<xref:System.Web.UI.Page.LoadComplete> 事件不再导致 <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控件针对 create/update/delete 参数的更改来调用数据绑定。 此更改消除到数据库的外来行程，防止重置控件的值，并生成与其他数据控件一致的行为，例如 <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> 和 <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>。 在应用程序依赖于在 <xref:System.Web.UI.Page.LoadComplete> 事件中调用数据绑定的极少数情况下，此更改会产生不同的行为。

#### <a name="suggestion"></a>建议

如果需要数据绑定，请在回发之前的事件中手动调用数据绑定。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时|
