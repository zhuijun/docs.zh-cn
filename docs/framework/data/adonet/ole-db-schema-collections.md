---
title: OLE DB 架构集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 90899a123b3dafcd47a50ef8f6eb003938b22a03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186934"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="eebb3-102">OLE DB 架构集合</span><span class="sxs-lookup"><span data-stu-id="eebb3-102">OLE DB Schema Collections</span></span>

<span data-ttu-id="eebb3-103">本节讨论对适用于 Microsoft SQL Server、Oracle 和 Microsoft Jet 的 OLE DB 提供程序的架构集合支持</span><span class="sxs-lookup"><span data-stu-id="eebb3-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="eebb3-104">Microsoft SQL Server OLE DB 提供程序</span><span class="sxs-lookup"><span data-stu-id="eebb3-104">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="eebb3-105">除了通用架构集合之外，Microsoft SQL Server OLE DB 驱动程序还支持下列特定的架构集合：</span><span class="sxs-lookup"><span data-stu-id="eebb3-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="eebb3-106">表</span><span class="sxs-lookup"><span data-stu-id="eebb3-106">Tables</span></span>  
  
- <span data-ttu-id="eebb3-107">列</span><span class="sxs-lookup"><span data-stu-id="eebb3-107">Columns</span></span>  
  
- <span data-ttu-id="eebb3-108">过程</span><span class="sxs-lookup"><span data-stu-id="eebb3-108">Procedures</span></span>  
  
- <span data-ttu-id="eebb3-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="eebb3-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="eebb3-110">目录</span><span class="sxs-lookup"><span data-stu-id="eebb3-110">Catalog</span></span>  
  
- <span data-ttu-id="eebb3-111">索引</span><span class="sxs-lookup"><span data-stu-id="eebb3-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="eebb3-112">表</span><span class="sxs-lookup"><span data-stu-id="eebb3-112">Tables</span></span>  
  
|<span data-ttu-id="eebb3-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-113">ColumnName</span></span>|<span data-ttu-id="eebb3-114">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-115">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-116">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-116">String</span></span>|  
|<span data-ttu-id="eebb3-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-118">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-118">String</span></span>|  
|<span data-ttu-id="eebb3-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-119">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-120">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-120">String</span></span>|  
|<span data-ttu-id="eebb3-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-121">TABLE_TYPE</span></span>|<span data-ttu-id="eebb3-122">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-122">String</span></span>|  
|<span data-ttu-id="eebb3-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-123">TABLE_GUID</span></span>|<span data-ttu-id="eebb3-124">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-124">Guid</span></span>|  
|<span data-ttu-id="eebb3-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-125">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-126">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-126">String</span></span>|  
|<span data-ttu-id="eebb3-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-127">TABLE_PROPID</span></span>|<span data-ttu-id="eebb3-128">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-128">Int64</span></span>|  
|<span data-ttu-id="eebb3-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-129">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-130">DateTime</span></span>|  
|<span data-ttu-id="eebb3-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-131">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="eebb3-133">列</span><span class="sxs-lookup"><span data-stu-id="eebb3-133">Columns</span></span>  
  
|<span data-ttu-id="eebb3-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-134">ColumnName</span></span>|<span data-ttu-id="eebb3-135">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-136">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-137">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-137">String</span></span>|  
|<span data-ttu-id="eebb3-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-139">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-139">String</span></span>|  
|<span data-ttu-id="eebb3-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-140">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-141">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-141">String</span></span>|  
|<span data-ttu-id="eebb3-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-142">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-143">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-143">String</span></span>|  
|<span data-ttu-id="eebb3-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-144">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-145">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-145">Guid</span></span>|  
|<span data-ttu-id="eebb3-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-146">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-147">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-147">Int64</span></span>|  
|<span data-ttu-id="eebb3-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-149">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-149">Int64</span></span>|  
|<span data-ttu-id="eebb3-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="eebb3-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-151">Boolean</span></span>|  
|<span data-ttu-id="eebb3-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="eebb3-153">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-153">String</span></span>|  
|<span data-ttu-id="eebb3-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="eebb3-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="eebb3-155">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-155">Int64</span></span>|  
|<span data-ttu-id="eebb3-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-156">IS_NULLABLE</span></span>|<span data-ttu-id="eebb3-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-157">Boolean</span></span>|  
|<span data-ttu-id="eebb3-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-158">DATA_TYPE</span></span>|<span data-ttu-id="eebb3-159">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-159">Int32</span></span>|  
|<span data-ttu-id="eebb3-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-160">TYPE_GUID</span></span>|<span data-ttu-id="eebb3-161">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-161">Guid</span></span>|  
|<span data-ttu-id="eebb3-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="eebb3-163">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-163">Int64</span></span>|  
|<span data-ttu-id="eebb3-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="eebb3-165">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-165">Int64</span></span>|  
|<span data-ttu-id="eebb3-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="eebb3-167">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-167">Int32</span></span>|  
|<span data-ttu-id="eebb3-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="eebb3-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="eebb3-169">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-169">Int16</span></span>|  
|<span data-ttu-id="eebb3-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="eebb3-171">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-171">Int64</span></span>|  
|<span data-ttu-id="eebb3-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="eebb3-173">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-173">String</span></span>|  
|<span data-ttu-id="eebb3-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="eebb3-175">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-175">String</span></span>|  
|<span data-ttu-id="eebb3-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="eebb3-177">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-177">String</span></span>|  
|<span data-ttu-id="eebb3-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="eebb3-179">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-179">String</span></span>|  
|<span data-ttu-id="eebb3-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="eebb3-181">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-181">String</span></span>|  
|<span data-ttu-id="eebb3-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-182">COLLATION_NAME</span></span>|<span data-ttu-id="eebb3-183">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-183">String</span></span>|  
|<span data-ttu-id="eebb3-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="eebb3-185">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-185">String</span></span>|  
|<span data-ttu-id="eebb3-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="eebb3-187">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-187">String</span></span>|  
|<span data-ttu-id="eebb3-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-188">DOMAIN_NAME</span></span>|<span data-ttu-id="eebb3-189">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-189">String</span></span>|  
|<span data-ttu-id="eebb3-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-190">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-191">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-191">String</span></span>|  
|<span data-ttu-id="eebb3-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="eebb3-192">COLUMN_LCID</span></span>|<span data-ttu-id="eebb3-193">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-193">Int32</span></span>|  
|<span data-ttu-id="eebb3-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="eebb3-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="eebb3-195">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-195">Int32</span></span>|  
|<span data-ttu-id="eebb3-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="eebb3-196">COLUMN_SORTID</span></span>|<span data-ttu-id="eebb3-197">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-197">Int32</span></span>|  
|<span data-ttu-id="eebb3-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="eebb3-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="eebb3-199">Byte[]</span></span>|  
|<span data-ttu-id="eebb3-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="eebb3-200">IS_COMPUTED</span></span>|<span data-ttu-id="eebb3-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="eebb3-202">过程</span><span class="sxs-lookup"><span data-stu-id="eebb3-202">Procedures</span></span>  
  
|<span data-ttu-id="eebb3-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-203">ColumnName</span></span>|<span data-ttu-id="eebb3-204">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="eebb3-206">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-206">String</span></span>|  
|<span data-ttu-id="eebb3-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="eebb3-208">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-208">String</span></span>|  
|<span data-ttu-id="eebb3-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="eebb3-210">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-210">String</span></span>|  
|<span data-ttu-id="eebb3-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="eebb3-212">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-212">Int16</span></span>|  
|<span data-ttu-id="eebb3-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="eebb3-214">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-214">String</span></span>|  
|<span data-ttu-id="eebb3-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-215">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-216">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-216">String</span></span>|  
|<span data-ttu-id="eebb3-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-217">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-218">DateTime</span></span>|  
|<span data-ttu-id="eebb3-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-219">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="eebb3-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="eebb3-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="eebb3-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-222">ColumnName</span></span>|<span data-ttu-id="eebb3-223">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="eebb3-225">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-225">String</span></span>|  
|<span data-ttu-id="eebb3-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="eebb3-227">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-227">String</span></span>|  
|<span data-ttu-id="eebb3-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="eebb3-229">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-229">String</span></span>|  
|<span data-ttu-id="eebb3-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-230">PARAMETER_NAME</span></span>|<span data-ttu-id="eebb3-231">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-231">String</span></span>|  
|<span data-ttu-id="eebb3-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-233">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-233">Int32</span></span>|  
|<span data-ttu-id="eebb3-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="eebb3-235">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-235">Int32</span></span>|  
|<span data-ttu-id="eebb3-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="eebb3-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-237">Boolean</span></span>|  
|<span data-ttu-id="eebb3-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="eebb3-239">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-239">String</span></span>|  
|<span data-ttu-id="eebb3-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-240">IS_NULLABLE</span></span>|<span data-ttu-id="eebb3-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-241">Boolean</span></span>|  
|<span data-ttu-id="eebb3-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-242">DATA_TYPE</span></span>|<span data-ttu-id="eebb3-243">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-243">Int32</span></span>|  
|<span data-ttu-id="eebb3-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="eebb3-245">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-245">Int64</span></span>|  
|<span data-ttu-id="eebb3-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="eebb3-247">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-247">Int64</span></span>|  
|<span data-ttu-id="eebb3-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="eebb3-249">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-249">Int32</span></span>|  
|<span data-ttu-id="eebb3-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="eebb3-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="eebb3-251">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-251">Int16</span></span>|  
|<span data-ttu-id="eebb3-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-252">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-253">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-253">String</span></span>|  
|<span data-ttu-id="eebb3-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-254">TYPE_NAME</span></span>|<span data-ttu-id="eebb3-255">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-255">String</span></span>|  
|<span data-ttu-id="eebb3-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="eebb3-257">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="eebb3-258">目录</span><span class="sxs-lookup"><span data-stu-id="eebb3-258">Catalog</span></span>  
  
|<span data-ttu-id="eebb3-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-259">ColumnName</span></span>|<span data-ttu-id="eebb3-260">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-261">CATALOG_NAME</span></span>|<span data-ttu-id="eebb3-262">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-262">String</span></span>|  
|<span data-ttu-id="eebb3-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-263">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-264">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="eebb3-265">索引</span><span class="sxs-lookup"><span data-stu-id="eebb3-265">Indexes</span></span>  
  
|<span data-ttu-id="eebb3-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-266">ColumnName</span></span>|<span data-ttu-id="eebb3-267">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-268">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-269">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-269">String</span></span>|  
|<span data-ttu-id="eebb3-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-271">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-271">String</span></span>|  
|<span data-ttu-id="eebb3-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-272">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-273">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-273">String</span></span>|  
|<span data-ttu-id="eebb3-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-274">INDEX_CATALOG</span></span>|<span data-ttu-id="eebb3-275">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-275">String</span></span>|  
|<span data-ttu-id="eebb3-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="eebb3-277">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-277">String</span></span>|  
|<span data-ttu-id="eebb3-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-278">INDEX_NAME</span></span>|<span data-ttu-id="eebb3-279">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-279">String</span></span>|  
|<span data-ttu-id="eebb3-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="eebb3-280">PRIMARY_KEY</span></span>|<span data-ttu-id="eebb3-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-281">Boolean</span></span>|  
|<span data-ttu-id="eebb3-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="eebb3-282">UNIQUE</span></span>|<span data-ttu-id="eebb3-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-283">Boolean</span></span>|  
|<span data-ttu-id="eebb3-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="eebb3-284">CLUSTERED</span></span>|<span data-ttu-id="eebb3-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-285">Boolean</span></span>|  
|<span data-ttu-id="eebb3-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-286">TYPE</span></span>|<span data-ttu-id="eebb3-287">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-287">Int32</span></span>|  
|<span data-ttu-id="eebb3-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="eebb3-288">FILL_FACTOR</span></span>|<span data-ttu-id="eebb3-289">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-289">Int32</span></span>|  
|<span data-ttu-id="eebb3-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="eebb3-290">INITIAL_SIZE</span></span>|<span data-ttu-id="eebb3-291">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-291">Int32</span></span>|  
|<span data-ttu-id="eebb3-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="eebb3-292">NULLS</span></span>|<span data-ttu-id="eebb3-293">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-293">Int32</span></span>|  
|<span data-ttu-id="eebb3-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="eebb3-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="eebb3-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-295">Boolean</span></span>|  
|<span data-ttu-id="eebb3-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="eebb3-296">AUTO_UPDATE</span></span>|<span data-ttu-id="eebb3-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-297">Boolean</span></span>|  
|<span data-ttu-id="eebb3-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-298">NULL_COLLATION</span></span>|<span data-ttu-id="eebb3-299">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-299">Int32</span></span>|  
|<span data-ttu-id="eebb3-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-301">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-301">Int64</span></span>|  
|<span data-ttu-id="eebb3-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-302">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-303">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-303">String</span></span>|  
|<span data-ttu-id="eebb3-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-304">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-305">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-305">Guid</span></span>|  
|<span data-ttu-id="eebb3-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-306">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-307">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-307">Int64</span></span>|  
|<span data-ttu-id="eebb3-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-308">COLLATION</span></span>|<span data-ttu-id="eebb3-309">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-309">Int16</span></span>|  
|<span data-ttu-id="eebb3-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="eebb3-310">CARDINALITY</span></span>|<span data-ttu-id="eebb3-311">小数</span><span class="sxs-lookup"><span data-stu-id="eebb3-311">Decimal</span></span>|  
|<span data-ttu-id="eebb3-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="eebb3-312">PAGES</span></span>|<span data-ttu-id="eebb3-313">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-313">Int32</span></span>|  
|<span data-ttu-id="eebb3-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-314">FILTER_CONDITION</span></span>|<span data-ttu-id="eebb3-315">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-315">String</span></span>|  
|<span data-ttu-id="eebb3-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-316">INTEGRATED</span></span>|<span data-ttu-id="eebb3-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="eebb3-318">Microsoft Oracle OLE DB 提供程序</span><span class="sxs-lookup"><span data-stu-id="eebb3-318">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="eebb3-319">除了通用架构集合之外，Microsoft Oracle OLE DB 驱动程序还支持下列特定的架构集合：</span><span class="sxs-lookup"><span data-stu-id="eebb3-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="eebb3-320">表</span><span class="sxs-lookup"><span data-stu-id="eebb3-320">Tables</span></span>  
  
- <span data-ttu-id="eebb3-321">列</span><span class="sxs-lookup"><span data-stu-id="eebb3-321">Columns</span></span>  
  
- <span data-ttu-id="eebb3-322">过程</span><span class="sxs-lookup"><span data-stu-id="eebb3-322">Procedures</span></span>  
  
- <span data-ttu-id="eebb3-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="eebb3-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="eebb3-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="eebb3-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="eebb3-325">视图</span><span class="sxs-lookup"><span data-stu-id="eebb3-325">Views</span></span>  
  
- <span data-ttu-id="eebb3-326">索引</span><span class="sxs-lookup"><span data-stu-id="eebb3-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="eebb3-327">表</span><span class="sxs-lookup"><span data-stu-id="eebb3-327">Tables</span></span>  
  
|<span data-ttu-id="eebb3-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-328">ColumnName</span></span>|<span data-ttu-id="eebb3-329">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-330">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-331">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-331">String</span></span>|  
|<span data-ttu-id="eebb3-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-333">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-333">String</span></span>|  
|<span data-ttu-id="eebb3-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-334">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-335">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-335">String</span></span>|  
|<span data-ttu-id="eebb3-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-336">TABLE_TYPE</span></span>|<span data-ttu-id="eebb3-337">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-337">String</span></span>|  
|<span data-ttu-id="eebb3-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-338">TABLE_GUID</span></span>|<span data-ttu-id="eebb3-339">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-339">Guid</span></span>|  
|<span data-ttu-id="eebb3-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-340">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-341">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-341">String</span></span>|  
|<span data-ttu-id="eebb3-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-342">TABLE_PROPID</span></span>|<span data-ttu-id="eebb3-343">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-343">Int64</span></span>|  
|<span data-ttu-id="eebb3-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-344">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-345">DateTime</span></span>|  
|<span data-ttu-id="eebb3-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-346">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="eebb3-348">列</span><span class="sxs-lookup"><span data-stu-id="eebb3-348">Columns</span></span>  
  
|<span data-ttu-id="eebb3-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-349">ColumnName</span></span>|<span data-ttu-id="eebb3-350">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-351">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-352">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-352">String</span></span>|  
|<span data-ttu-id="eebb3-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-354">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-354">String</span></span>|  
|<span data-ttu-id="eebb3-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-355">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-356">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-356">String</span></span>|  
|<span data-ttu-id="eebb3-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-357">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-358">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-358">String</span></span>|  
|<span data-ttu-id="eebb3-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-359">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-360">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-360">Guid</span></span>|  
|<span data-ttu-id="eebb3-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-361">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-362">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-362">Int64</span></span>|  
|<span data-ttu-id="eebb3-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-364">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-364">Int64</span></span>|  
|<span data-ttu-id="eebb3-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="eebb3-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-366">Boolean</span></span>|  
|<span data-ttu-id="eebb3-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="eebb3-368">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-368">String</span></span>|  
|<span data-ttu-id="eebb3-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="eebb3-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="eebb3-370">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-370">Int64</span></span>|  
|<span data-ttu-id="eebb3-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-371">IS_NULLABLE</span></span>|<span data-ttu-id="eebb3-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-372">Boolean</span></span>|  
|<span data-ttu-id="eebb3-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-373">DATA_TYPE</span></span>|<span data-ttu-id="eebb3-374">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-374">Int32</span></span>|  
|<span data-ttu-id="eebb3-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-375">TYPE_GUID</span></span>|<span data-ttu-id="eebb3-376">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-376">Guid</span></span>|  
|<span data-ttu-id="eebb3-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="eebb3-378">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-378">Int64</span></span>|  
|<span data-ttu-id="eebb3-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="eebb3-380">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-380">Int64</span></span>|  
|<span data-ttu-id="eebb3-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="eebb3-382">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-382">Int32</span></span>|  
|<span data-ttu-id="eebb3-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="eebb3-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="eebb3-384">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-384">Int16</span></span>|  
|<span data-ttu-id="eebb3-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="eebb3-386">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-386">Int64</span></span>|  
|<span data-ttu-id="eebb3-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="eebb3-388">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-388">String</span></span>|  
|<span data-ttu-id="eebb3-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="eebb3-390">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-390">String</span></span>|  
|<span data-ttu-id="eebb3-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="eebb3-392">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-392">String</span></span>|  
|<span data-ttu-id="eebb3-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="eebb3-394">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-394">String</span></span>|  
|<span data-ttu-id="eebb3-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="eebb3-396">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-396">String</span></span>|  
|<span data-ttu-id="eebb3-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-397">COLLATION_NAME</span></span>|<span data-ttu-id="eebb3-398">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-398">String</span></span>|  
|<span data-ttu-id="eebb3-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="eebb3-400">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-400">String</span></span>|  
|<span data-ttu-id="eebb3-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="eebb3-402">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-402">String</span></span>|  
|<span data-ttu-id="eebb3-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-403">DOMAIN_NAME</span></span>|<span data-ttu-id="eebb3-404">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-404">String</span></span>|  
|<span data-ttu-id="eebb3-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-405">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-406">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="eebb3-407">过程</span><span class="sxs-lookup"><span data-stu-id="eebb3-407">Procedures</span></span>  
  
|<span data-ttu-id="eebb3-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-408">ColumnName</span></span>|<span data-ttu-id="eebb3-409">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="eebb3-411">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-411">String</span></span>|  
|<span data-ttu-id="eebb3-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="eebb3-413">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-413">String</span></span>|  
|<span data-ttu-id="eebb3-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="eebb3-415">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-415">String</span></span>|  
|<span data-ttu-id="eebb3-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="eebb3-417">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-417">Int16</span></span>|  
|<span data-ttu-id="eebb3-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="eebb3-419">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-419">String</span></span>|  
|<span data-ttu-id="eebb3-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-420">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-421">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-421">String</span></span>|  
|<span data-ttu-id="eebb3-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-422">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-423">DateTime</span></span>|  
|<span data-ttu-id="eebb3-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-424">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="eebb3-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="eebb3-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="eebb3-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-427">ColumnName</span></span>|<span data-ttu-id="eebb3-428">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="eebb3-430">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-430">String</span></span>|  
|<span data-ttu-id="eebb3-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="eebb3-432">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-432">String</span></span>|  
|<span data-ttu-id="eebb3-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="eebb3-434">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-434">String</span></span>|  
|<span data-ttu-id="eebb3-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-435">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-436">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-436">String</span></span>|  
|<span data-ttu-id="eebb3-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-437">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-438">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-438">Guid</span></span>|  
|<span data-ttu-id="eebb3-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-439">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-440">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-440">Int64</span></span>|  
|<span data-ttu-id="eebb3-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="eebb3-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="eebb3-442">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-442">Int64</span></span>|  
|<span data-ttu-id="eebb3-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-444">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-444">Int64</span></span>|  
|<span data-ttu-id="eebb3-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-445">IS_NULLABLE</span></span>|<span data-ttu-id="eebb3-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-446">Boolean</span></span>|  
|<span data-ttu-id="eebb3-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-447">DATA_TYPE</span></span>|<span data-ttu-id="eebb3-448">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-448">Int32</span></span>|  
|<span data-ttu-id="eebb3-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-449">TYPE_GUID</span></span>|<span data-ttu-id="eebb3-450">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-450">Guid</span></span>|  
|<span data-ttu-id="eebb3-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="eebb3-452">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-452">Int64</span></span>|  
|<span data-ttu-id="eebb3-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="eebb3-454">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-454">Int64</span></span>|  
|<span data-ttu-id="eebb3-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="eebb3-456">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-456">Int32</span></span>|  
|<span data-ttu-id="eebb3-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="eebb3-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="eebb3-458">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-458">Int16</span></span>|  
|<span data-ttu-id="eebb3-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-459">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-460">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-460">String</span></span>|  
|<span data-ttu-id="eebb3-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="eebb3-461">OVERLOAD</span></span>|<span data-ttu-id="eebb3-462">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="eebb3-463">视图</span><span class="sxs-lookup"><span data-stu-id="eebb3-463">Views</span></span>  
  
|<span data-ttu-id="eebb3-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-464">ColumnName</span></span>|<span data-ttu-id="eebb3-465">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-466">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-467">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-467">String</span></span>|  
|<span data-ttu-id="eebb3-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-469">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-469">String</span></span>|  
|<span data-ttu-id="eebb3-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-470">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-471">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-471">String</span></span>|  
|<span data-ttu-id="eebb3-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="eebb3-473">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-473">String</span></span>|  
|<span data-ttu-id="eebb3-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-474">CHECK_OPTION</span></span>|<span data-ttu-id="eebb3-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-475">Boolean</span></span>|  
|<span data-ttu-id="eebb3-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-476">IS_UPDATABLE</span></span>|<span data-ttu-id="eebb3-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-477">Boolean</span></span>|  
|<span data-ttu-id="eebb3-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-478">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-479">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-479">String</span></span>|  
|<span data-ttu-id="eebb3-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-480">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-481">DateTime</span></span>|  
|<span data-ttu-id="eebb3-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-482">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="eebb3-484">索引</span><span class="sxs-lookup"><span data-stu-id="eebb3-484">Indexes</span></span>  
  
|<span data-ttu-id="eebb3-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-485">ColumnName</span></span>|<span data-ttu-id="eebb3-486">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-487">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-488">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-488">String</span></span>|  
|<span data-ttu-id="eebb3-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-490">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-490">String</span></span>|  
|<span data-ttu-id="eebb3-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-491">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-492">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-492">String</span></span>|  
|<span data-ttu-id="eebb3-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-493">INDEX_CATALOG</span></span>|<span data-ttu-id="eebb3-494">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-494">String</span></span>|  
|<span data-ttu-id="eebb3-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="eebb3-496">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-496">String</span></span>|  
|<span data-ttu-id="eebb3-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-497">INDEX_NAME</span></span>|<span data-ttu-id="eebb3-498">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-498">String</span></span>|  
|<span data-ttu-id="eebb3-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="eebb3-499">PRIMARY_KEY</span></span>|<span data-ttu-id="eebb3-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-500">Boolean</span></span>|  
|<span data-ttu-id="eebb3-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="eebb3-501">UNIQUE</span></span>|<span data-ttu-id="eebb3-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-502">Boolean</span></span>|  
|<span data-ttu-id="eebb3-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="eebb3-503">CLUSTERED</span></span>|<span data-ttu-id="eebb3-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-504">Boolean</span></span>|  
|<span data-ttu-id="eebb3-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-505">TYPE</span></span>|<span data-ttu-id="eebb3-506">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-506">Int32</span></span>|  
|<span data-ttu-id="eebb3-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="eebb3-507">FILL_FACTOR</span></span>|<span data-ttu-id="eebb3-508">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-508">Int32</span></span>|  
|<span data-ttu-id="eebb3-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="eebb3-509">INITIAL_SIZE</span></span>|<span data-ttu-id="eebb3-510">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-510">Int32</span></span>|  
|<span data-ttu-id="eebb3-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="eebb3-511">NULLS</span></span>|<span data-ttu-id="eebb3-512">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-512">Int32</span></span>|  
|<span data-ttu-id="eebb3-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="eebb3-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="eebb3-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-514">Boolean</span></span>|  
|<span data-ttu-id="eebb3-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="eebb3-515">AUTO_UPDATE</span></span>|<span data-ttu-id="eebb3-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-516">Boolean</span></span>|  
|<span data-ttu-id="eebb3-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-517">NULL_COLLATION</span></span>|<span data-ttu-id="eebb3-518">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-518">Int32</span></span>|  
|<span data-ttu-id="eebb3-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-520">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-520">Int64</span></span>|  
|<span data-ttu-id="eebb3-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-521">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-522">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-522">String</span></span>|  
|<span data-ttu-id="eebb3-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-523">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-524">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-524">Guid</span></span>|  
|<span data-ttu-id="eebb3-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-525">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-526">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-526">Int64</span></span>|  
|<span data-ttu-id="eebb3-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-527">COLLATION</span></span>|<span data-ttu-id="eebb3-528">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-528">Int16</span></span>|  
|<span data-ttu-id="eebb3-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="eebb3-529">CARDINALITY</span></span>|<span data-ttu-id="eebb3-530">小数</span><span class="sxs-lookup"><span data-stu-id="eebb3-530">Decimal</span></span>|  
|<span data-ttu-id="eebb3-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="eebb3-531">PAGES</span></span>|<span data-ttu-id="eebb3-532">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-532">Int32</span></span>|  
|<span data-ttu-id="eebb3-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-533">FILTER_CONDITION</span></span>|<span data-ttu-id="eebb3-534">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-534">String</span></span>|  
|<span data-ttu-id="eebb3-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-535">INTEGRATED</span></span>|<span data-ttu-id="eebb3-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="eebb3-537">Microsoft Jet OLE DB     </span><span class="sxs-lookup"><span data-stu-id="eebb3-537">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="eebb3-538">除了通用架构集合之外，Microsoft Jet OLE DB 驱动程序还支持下列特定的架构集合：</span><span class="sxs-lookup"><span data-stu-id="eebb3-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="eebb3-539">表</span><span class="sxs-lookup"><span data-stu-id="eebb3-539">Tables</span></span>  
  
- <span data-ttu-id="eebb3-540">列</span><span class="sxs-lookup"><span data-stu-id="eebb3-540">Columns</span></span>  
  
- <span data-ttu-id="eebb3-541">过程</span><span class="sxs-lookup"><span data-stu-id="eebb3-541">Procedures</span></span>  
  
- <span data-ttu-id="eebb3-542">视图</span><span class="sxs-lookup"><span data-stu-id="eebb3-542">Views</span></span>  
  
- <span data-ttu-id="eebb3-543">索引</span><span class="sxs-lookup"><span data-stu-id="eebb3-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="eebb3-544">表</span><span class="sxs-lookup"><span data-stu-id="eebb3-544">Tables</span></span>  
  
|<span data-ttu-id="eebb3-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-545">ColumnName</span></span>|<span data-ttu-id="eebb3-546">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-547">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-548">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-548">String</span></span>|  
|<span data-ttu-id="eebb3-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-550">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-550">String</span></span>|  
|<span data-ttu-id="eebb3-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-551">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-552">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-552">String</span></span>|  
|<span data-ttu-id="eebb3-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-553">TABLE_TYPE</span></span>|<span data-ttu-id="eebb3-554">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-554">String</span></span>|  
|<span data-ttu-id="eebb3-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-555">TABLE_GUID</span></span>|<span data-ttu-id="eebb3-556">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-556">Guid</span></span>|  
|<span data-ttu-id="eebb3-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-557">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-558">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-558">String</span></span>|  
|<span data-ttu-id="eebb3-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-559">TABLE_PROPID</span></span>|<span data-ttu-id="eebb3-560">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-560">Int64</span></span>|  
|<span data-ttu-id="eebb3-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-561">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-562">DateTime</span></span>|  
|<span data-ttu-id="eebb3-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-563">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="eebb3-565">列</span><span class="sxs-lookup"><span data-stu-id="eebb3-565">Columns</span></span>  
  
|<span data-ttu-id="eebb3-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-566">ColumnName</span></span>|<span data-ttu-id="eebb3-567">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-568">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-569">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-569">String</span></span>|  
|<span data-ttu-id="eebb3-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-571">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-571">String</span></span>|  
|<span data-ttu-id="eebb3-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-572">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-573">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-573">String</span></span>|  
|<span data-ttu-id="eebb3-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-574">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-575">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-575">String</span></span>|  
|<span data-ttu-id="eebb3-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-576">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-577">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-577">Guid</span></span>|  
|<span data-ttu-id="eebb3-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-578">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-579">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-579">Int64</span></span>|  
|<span data-ttu-id="eebb3-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-581">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-581">Int64</span></span>|  
|<span data-ttu-id="eebb3-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="eebb3-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-583">Boolean</span></span>|  
|<span data-ttu-id="eebb3-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="eebb3-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="eebb3-585">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-585">String</span></span>|  
|<span data-ttu-id="eebb3-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="eebb3-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="eebb3-587">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-587">Int64</span></span>|  
|<span data-ttu-id="eebb3-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-588">IS_NULLABLE</span></span>|<span data-ttu-id="eebb3-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-589">Boolean</span></span>|  
|<span data-ttu-id="eebb3-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-590">DATA_TYPE</span></span>|<span data-ttu-id="eebb3-591">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-591">Int32</span></span>|  
|<span data-ttu-id="eebb3-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-592">TYPE_GUID</span></span>|<span data-ttu-id="eebb3-593">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-593">Guid</span></span>|  
|<span data-ttu-id="eebb3-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="eebb3-595">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-595">Int64</span></span>|  
|<span data-ttu-id="eebb3-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="eebb3-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="eebb3-597">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-597">Int64</span></span>|  
|<span data-ttu-id="eebb3-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="eebb3-599">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-599">Int32</span></span>|  
|<span data-ttu-id="eebb3-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="eebb3-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="eebb3-601">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-601">Int16</span></span>|  
|<span data-ttu-id="eebb3-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="eebb3-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="eebb3-603">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-603">Int64</span></span>|  
|<span data-ttu-id="eebb3-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="eebb3-605">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-605">String</span></span>|  
|<span data-ttu-id="eebb3-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="eebb3-607">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-607">String</span></span>|  
|<span data-ttu-id="eebb3-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="eebb3-609">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-609">String</span></span>|  
|<span data-ttu-id="eebb3-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="eebb3-611">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-611">String</span></span>|  
|<span data-ttu-id="eebb3-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="eebb3-613">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-613">String</span></span>|  
|<span data-ttu-id="eebb3-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-614">COLLATION_NAME</span></span>|<span data-ttu-id="eebb3-615">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-615">String</span></span>|  
|<span data-ttu-id="eebb3-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="eebb3-617">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-617">String</span></span>|  
|<span data-ttu-id="eebb3-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="eebb3-619">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-619">String</span></span>|  
|<span data-ttu-id="eebb3-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-620">DOMAIN_NAME</span></span>|<span data-ttu-id="eebb3-621">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-621">String</span></span>|  
|<span data-ttu-id="eebb3-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-622">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-623">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="eebb3-624">过程</span><span class="sxs-lookup"><span data-stu-id="eebb3-624">Procedures</span></span>  
  
|<span data-ttu-id="eebb3-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-625">ColumnName</span></span>|<span data-ttu-id="eebb3-626">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="eebb3-628">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-628">String</span></span>|  
|<span data-ttu-id="eebb3-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="eebb3-630">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-630">String</span></span>|  
|<span data-ttu-id="eebb3-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="eebb3-632">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-632">String</span></span>|  
|<span data-ttu-id="eebb3-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="eebb3-634">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-634">Int16</span></span>|  
|<span data-ttu-id="eebb3-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="eebb3-636">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-636">String</span></span>|  
|<span data-ttu-id="eebb3-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-637">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-638">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-638">String</span></span>|  
|<span data-ttu-id="eebb3-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-639">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-640">DateTime</span></span>|  
|<span data-ttu-id="eebb3-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-641">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="eebb3-643">视图</span><span class="sxs-lookup"><span data-stu-id="eebb3-643">Views</span></span>  
  
|<span data-ttu-id="eebb3-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-644">ColumnName</span></span>|<span data-ttu-id="eebb3-645">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-646">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-647">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-647">String</span></span>|  
|<span data-ttu-id="eebb3-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-649">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-649">String</span></span>|  
|<span data-ttu-id="eebb3-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-650">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-651">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-651">String</span></span>|  
|<span data-ttu-id="eebb3-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="eebb3-653">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-653">String</span></span>|  
|<span data-ttu-id="eebb3-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-654">CHECK_OPTION</span></span>|<span data-ttu-id="eebb3-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-655">Boolean</span></span>|  
|<span data-ttu-id="eebb3-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="eebb3-656">IS_UPDATABLE</span></span>|<span data-ttu-id="eebb3-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-657">Boolean</span></span>|  
|<span data-ttu-id="eebb3-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eebb3-658">DESCRIPTION</span></span>|<span data-ttu-id="eebb3-659">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-659">String</span></span>|  
|<span data-ttu-id="eebb3-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-660">DATE_CREATED</span></span>|<span data-ttu-id="eebb3-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-661">DateTime</span></span>|  
|<span data-ttu-id="eebb3-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="eebb3-662">DATE_MODIFIED</span></span>|<span data-ttu-id="eebb3-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="eebb3-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="eebb3-664">索引</span><span class="sxs-lookup"><span data-stu-id="eebb3-664">Indexes</span></span>  
  
|<span data-ttu-id="eebb3-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="eebb3-665">ColumnName</span></span>|<span data-ttu-id="eebb3-666">数据类型</span><span class="sxs-lookup"><span data-stu-id="eebb3-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="eebb3-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-667">TABLE_CATALOG</span></span>|<span data-ttu-id="eebb3-668">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-668">String</span></span>|  
|<span data-ttu-id="eebb3-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="eebb3-670">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-670">String</span></span>|  
|<span data-ttu-id="eebb3-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-671">TABLE_NAME</span></span>|<span data-ttu-id="eebb3-672">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-672">String</span></span>|  
|<span data-ttu-id="eebb3-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="eebb3-673">INDEX_CATALOG</span></span>|<span data-ttu-id="eebb3-674">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-674">String</span></span>|  
|<span data-ttu-id="eebb3-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="eebb3-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="eebb3-676">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-676">String</span></span>|  
|<span data-ttu-id="eebb3-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-677">INDEX_NAME</span></span>|<span data-ttu-id="eebb3-678">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-678">String</span></span>|  
|<span data-ttu-id="eebb3-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="eebb3-679">PRIMARY_KEY</span></span>|<span data-ttu-id="eebb3-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-680">Boolean</span></span>|  
|<span data-ttu-id="eebb3-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="eebb3-681">UNIQUE</span></span>|<span data-ttu-id="eebb3-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-682">Boolean</span></span>|  
|<span data-ttu-id="eebb3-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="eebb3-683">CLUSTERED</span></span>|<span data-ttu-id="eebb3-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-684">Boolean</span></span>|  
|<span data-ttu-id="eebb3-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="eebb3-685">TYPE</span></span>|<span data-ttu-id="eebb3-686">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-686">Int32</span></span>|  
|<span data-ttu-id="eebb3-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="eebb3-687">FILL_FACTOR</span></span>|<span data-ttu-id="eebb3-688">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-688">Int32</span></span>|  
|<span data-ttu-id="eebb3-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="eebb3-689">INITIAL_SIZE</span></span>|<span data-ttu-id="eebb3-690">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-690">Int32</span></span>|  
|<span data-ttu-id="eebb3-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="eebb3-691">NULLS</span></span>|<span data-ttu-id="eebb3-692">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-692">Int32</span></span>|  
|<span data-ttu-id="eebb3-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="eebb3-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="eebb3-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-694">Boolean</span></span>|  
|<span data-ttu-id="eebb3-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="eebb3-695">AUTO_UPDATE</span></span>|<span data-ttu-id="eebb3-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-696">Boolean</span></span>|  
|<span data-ttu-id="eebb3-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-697">NULL_COLLATION</span></span>|<span data-ttu-id="eebb3-698">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-698">Int32</span></span>|  
|<span data-ttu-id="eebb3-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="eebb3-700">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-700">Int64</span></span>|  
|<span data-ttu-id="eebb3-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="eebb3-701">COLUMN_NAME</span></span>|<span data-ttu-id="eebb3-702">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-702">String</span></span>|  
|<span data-ttu-id="eebb3-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="eebb3-703">COLUMN_GUID</span></span>|<span data-ttu-id="eebb3-704">Guid</span><span class="sxs-lookup"><span data-stu-id="eebb3-704">Guid</span></span>|  
|<span data-ttu-id="eebb3-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="eebb3-705">COLUMN_PROPID</span></span>|<span data-ttu-id="eebb3-706">Int64</span><span class="sxs-lookup"><span data-stu-id="eebb3-706">Int64</span></span>|  
|<span data-ttu-id="eebb3-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="eebb3-707">COLLATION</span></span>|<span data-ttu-id="eebb3-708">Int16</span><span class="sxs-lookup"><span data-stu-id="eebb3-708">Int16</span></span>|  
|<span data-ttu-id="eebb3-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="eebb3-709">CARDINALITY</span></span>|<span data-ttu-id="eebb3-710">小数</span><span class="sxs-lookup"><span data-stu-id="eebb3-710">Decimal</span></span>|  
|<span data-ttu-id="eebb3-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="eebb3-711">PAGES</span></span>|<span data-ttu-id="eebb3-712">Int32</span><span class="sxs-lookup"><span data-stu-id="eebb3-712">Int32</span></span>|  
|<span data-ttu-id="eebb3-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="eebb3-713">FILTER_CONDITION</span></span>|<span data-ttu-id="eebb3-714">字符串</span><span class="sxs-lookup"><span data-stu-id="eebb3-714">String</span></span>|  
|<span data-ttu-id="eebb3-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="eebb3-715">INTEGRATED</span></span>|<span data-ttu-id="eebb3-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="eebb3-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eebb3-717">请参阅</span><span class="sxs-lookup"><span data-stu-id="eebb3-717">See also</span></span>

- [<span data-ttu-id="eebb3-718">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="eebb3-718">ADO.NET Overview</span></span>](ado-net-overview.md)
