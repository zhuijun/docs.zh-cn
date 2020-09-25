---
title: 如何：使用 EdmGen.exe 验证模型和映射文件
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 62a3bde9d2431b9e9e86e2a8d8896520f3456590
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198114"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="1c7b9-102">如何：使用 EdmGen.exe 验证模型和映射文件</span><span class="sxs-lookup"><span data-stu-id="1c7b9-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>

<span data-ttu-id="1c7b9-103">本主题演示如何使用 [EDM 生成器 ( # A0) ](edm-generator-edmgen-exe.md) 工具来验证模型和映射文件。</span><span class="sxs-lookup"><span data-stu-id="1c7b9-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="1c7b9-104">有关详细信息，请参阅 [实体数据模型](../entity-data-model.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7b9-104">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="1c7b9-105">使用 EdmGen.exe 验证 School 模型</span><span class="sxs-lookup"><span data-stu-id="1c7b9-105">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="1c7b9-106">创建 School 数据库。</span><span class="sxs-lookup"><span data-stu-id="1c7b9-106">Create the School database.</span></span> <span data-ttu-id="1c7b9-107">有关详细信息，请参阅 [创建 School 示例数据库](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1c7b9-107">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="1c7b9-108">生成 School 模型。</span><span class="sxs-lookup"><span data-stu-id="1c7b9-108">Generate the School model.</span></span> <span data-ttu-id="1c7b9-109">有关详细信息，请参阅 [如何：使用 EdmGen.exe 生成模型和映射文件](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="1c7b9-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="1c7b9-110">在命令提示符下执行以下命令（无换行符）：</span><span class="sxs-lookup"><span data-stu-id="1c7b9-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1c7b9-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="1c7b9-111">See also</span></span>

- <span data-ttu-id="1c7b9-112">[如何：手动配置实体框架项目](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c7b9-112">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="1c7b9-113">[ADO.NET 实体数据模型工具](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c7b9-113">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="1c7b9-114">[如何：预生成视图以改进查询性能](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c7b9-114">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="1c7b9-115">如何：使用 EdmGen.exe 生成对象层代码</span><span class="sxs-lookup"><span data-stu-id="1c7b9-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
