---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617131"
---
### <a name="workflow-30-types-are-obsolete"></a>WorkFlow 3.0 类型已过时

#### <a name="details"></a>详细信息

Windows Workflow Foundation (WWF) 3.0 API（来自于 System.Workflow 命名空间）现已过时。

#### <a name="suggestion"></a>建议

应改用新的 WWF 4.0 API（在 System.Activities 中）。 可在[此处](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的示例，[此处](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5)还提供更深入的指导。 或者，由于仍然支持 WWF 3.0 API，因此可能会使用它们，通过禁止显示生成时警告或使用较旧的编译器可以避免出现该警告。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   | 主要       |
| Version | 4.5         |
| 类型    | 重定目标 |
