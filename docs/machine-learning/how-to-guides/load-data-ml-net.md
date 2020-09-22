---
title: 从文件和其他源加载数据
description: 了解如何使用 API 将数据加载到 ML.NET 中进行处理和训练。 数据存储在文件、数据库、JSON、XML 或内存集合中。
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: edcb1c4d00a09ba8404b08ddc3ca3447a52a81b6
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679581"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="5ab24-104">从文件和其他源加载数据</span><span class="sxs-lookup"><span data-stu-id="5ab24-104">Load data from files and other sources</span></span>

<span data-ttu-id="5ab24-105">了解如何使用 API 将数据加载到 ML.NET 中进行处理和训练。</span><span class="sxs-lookup"><span data-stu-id="5ab24-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="5ab24-106">最初存储在文件或其他数据源（例如数据库、JSON、XML 或内存中集合）中的数据。</span><span class="sxs-lookup"><span data-stu-id="5ab24-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="5ab24-107">如果使用模型生成器，请参阅[将训练数据加载到模型生成器](load-data-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="5ab24-108">创建数据模型</span><span class="sxs-lookup"><span data-stu-id="5ab24-108">Create the data model</span></span>

<span data-ttu-id="5ab24-109">ML.NET 允许通过类定义数据模型。</span><span class="sxs-lookup"><span data-stu-id="5ab24-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="5ab24-110">例如，给定以下输入数据：</span><span class="sxs-lookup"><span data-stu-id="5ab24-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="5ab24-111">创建一个表示以下代码片段的数据模型：</span><span class="sxs-lookup"><span data-stu-id="5ab24-111">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="5ab24-112">使用列特性注释数据模型</span><span class="sxs-lookup"><span data-stu-id="5ab24-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="5ab24-113">特性为 ML.NET 提供有关数据模型和数据源的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5ab24-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="5ab24-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) 特性指定属性的列索引。</span><span class="sxs-lookup"><span data-stu-id="5ab24-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ab24-115">只有从文件加载数据时才需要 [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="5ab24-116">将列加载为：</span><span class="sxs-lookup"><span data-stu-id="5ab24-116">Load columns as:</span></span>

- <span data-ttu-id="5ab24-117">单个列，例如 `HousingData` 类中的 `Size` 和 `CurrentPrices`。</span><span class="sxs-lookup"><span data-stu-id="5ab24-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="5ab24-118">以向量的形式一次加载多个列，例如 `HousingData` 类中的 `HistoricalPrices`。</span><span class="sxs-lookup"><span data-stu-id="5ab24-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="5ab24-119">如果有一个向量属性，请在数据模型中向该属性应用 [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) 特性。</span><span class="sxs-lookup"><span data-stu-id="5ab24-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="5ab24-120">请务必注意，向量中的所有元素必须为相同的类型。</span><span class="sxs-lookup"><span data-stu-id="5ab24-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="5ab24-121">保持列与列之间的分隔状态可以提高特征工程的易用性和灵活性，但是对于非常多的列，在单个列上操作会对训练速度产生影响。</span><span class="sxs-lookup"><span data-stu-id="5ab24-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="5ab24-122">ML.NET 通过列名称进行操作。</span><span class="sxs-lookup"><span data-stu-id="5ab24-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="5ab24-123">如果要将某个列的名称更改为该属性名称以外的其他名称，请使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 特性。</span><span class="sxs-lookup"><span data-stu-id="5ab24-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="5ab24-124">创建内存中对象时，仍然使用该属性名称创建对象。</span><span class="sxs-lookup"><span data-stu-id="5ab24-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="5ab24-125">但是，对于数据处理和生成机器学习模型，ML.NET 使用 [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) 特性中提供的值覆盖并引用该属性。</span><span class="sxs-lookup"><span data-stu-id="5ab24-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="5ab24-126">从单个文件加载数据</span><span class="sxs-lookup"><span data-stu-id="5ab24-126">Load data from a single file</span></span>

<span data-ttu-id="5ab24-127">若要从文件加载数据，请使用 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 方法以及要加载的数据的数据模型。</span><span class="sxs-lookup"><span data-stu-id="5ab24-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="5ab24-128">由于 `separatorChar` 参数默认为制表符分隔，因此请根据需要为数据文件更改该参数。</span><span class="sxs-lookup"><span data-stu-id="5ab24-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="5ab24-129">如果文件有标头，请将 `hasHeader` 参数设置为 `true`，以忽略文件中的第一行并开始从第二行加载数据。</span><span class="sxs-lookup"><span data-stu-id="5ab24-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="5ab24-130">从多个文件加载数据</span><span class="sxs-lookup"><span data-stu-id="5ab24-130">Load data from multiple files</span></span>

<span data-ttu-id="5ab24-131">如果数据存储在多个文件中，只要数据架构相同，ML.NET 就允许从同一目录或多个目录中的多个文件加载数据。</span><span class="sxs-lookup"><span data-stu-id="5ab24-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="5ab24-132">从单个目录中的文件加载</span><span class="sxs-lookup"><span data-stu-id="5ab24-132">Load from files in a single directory</span></span>

<span data-ttu-id="5ab24-133">当所有数据文件位于同一目录中时，请在 [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 方法中使用通配符。</span><span class="sxs-lookup"><span data-stu-id="5ab24-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="5ab24-134">从多个目录中的文件加载</span><span class="sxs-lookup"><span data-stu-id="5ab24-134">Load from files in multiple directories</span></span>

<span data-ttu-id="5ab24-135">若要从多个目录加载数据，请使用 [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) 方法创建 [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="5ab24-136">然后，使用 [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) 方法并指定单个文件路径（不能使用通配符）。</span><span class="sxs-lookup"><span data-stu-id="5ab24-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="5ab24-137">从关系数据库加载数据</span><span class="sxs-lookup"><span data-stu-id="5ab24-137">Load data from a relational database</span></span>

<span data-ttu-id="5ab24-138">ML.NET 支持从各种关系数据库中加载数据（包括 SQL Server、Azure SQL 数据库、Oracle、SQLite、PostgreSQL、Progress、IBM DB2 等），这些关系数据库由 [`System.Data`](xref:System.Data) 提供支持。</span><span class="sxs-lookup"><span data-stu-id="5ab24-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="5ab24-139">若要使用 `DatabaseLoader`，请参考 [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="5ab24-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="5ab24-140">指定具有名为 `House` 的表和以下架构的数据库：</span><span class="sxs-lookup"><span data-stu-id="5ab24-140">Given a database with a table named `House` and the following schema:</span></span>

```sql
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="5ab24-141">数据可以通过 `HouseData` 等类进行建模。</span><span class="sxs-lookup"><span data-stu-id="5ab24-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="5ab24-142">然后，在应用程序中创建 `DatabaseLoader`。</span><span class="sxs-lookup"><span data-stu-id="5ab24-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="5ab24-143">定义连接字符串以及要在数据库上执行的 SQL 命令，并创建 `DatabaseSource` 实例。</span><span class="sxs-lookup"><span data-stu-id="5ab24-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="5ab24-144">此示例使用具有文件路径的 LocalDB SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="5ab24-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="5ab24-145">但是，DatabaseLoader 支持本地和云中数据库的任何其他有效连接字符串。</span><span class="sxs-lookup"><span data-stu-id="5ab24-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="5ab24-146">类型不是 [`Real`](xref:System.Data.SqlDbType) 的数值数据必须转换为 [`Real`](xref:System.Data.SqlDbType)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="5ab24-147">[`Real`](xref:System.Data.SqlDbType) 类型表示为单精度浮动点值或 [`Single`](xref:System.Single)，这是 ML.NET 算法应采用的输入类型。</span><span class="sxs-lookup"><span data-stu-id="5ab24-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="5ab24-148">在此示例中，`NumBed` 列是数据库中的一个整数。</span><span class="sxs-lookup"><span data-stu-id="5ab24-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="5ab24-149">使用 `CAST` 内置函数，将其转换为 [`Real`](xref:System.Data.SqlDbType)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="5ab24-150">由于 `Price` 属性的类型已经是 [`Real`](xref:System.Data.SqlDbType)，则按原样加载。</span><span class="sxs-lookup"><span data-stu-id="5ab24-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="5ab24-151">使用 `Load` 方法将数据加载到 [`IDataView`](xref:Microsoft.ML.IDataView)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="5ab24-152">从其他源加载数据</span><span class="sxs-lookup"><span data-stu-id="5ab24-152">Load data from other sources</span></span>

<span data-ttu-id="5ab24-153">除了加载存储在文件中的数据外，ML.NET 还支持从各种源加载数据，这些源包括但不限于：</span><span class="sxs-lookup"><span data-stu-id="5ab24-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="5ab24-154">内存中集合</span><span class="sxs-lookup"><span data-stu-id="5ab24-154">In-memory collections</span></span>
- <span data-ttu-id="5ab24-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="5ab24-155">JSON/XML</span></span>

<span data-ttu-id="5ab24-156">请注意，在使用流式处理源时，ML.NET 预计输入采用内存中集合的形式。</span><span class="sxs-lookup"><span data-stu-id="5ab24-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="5ab24-157">因此，在使用 JSON/XML 等源时，请确保将数据格式化为内存中集合。</span><span class="sxs-lookup"><span data-stu-id="5ab24-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="5ab24-158">给定以下内存中集合：</span><span class="sxs-lookup"><span data-stu-id="5ab24-158">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="5ab24-159">使用 [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) 方法将内存中集合加载到 [`IDataView`](xref:Microsoft.ML.IDataView) 中：</span><span class="sxs-lookup"><span data-stu-id="5ab24-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ab24-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) 假定其所加载的 [`IEnumerable`](xref:System.Collections.IEnumerable) 是线程安全的。</span><span class="sxs-lookup"><span data-stu-id="5ab24-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="5ab24-161">后续步骤</span><span class="sxs-lookup"><span data-stu-id="5ab24-161">Next steps</span></span>

- <span data-ttu-id="5ab24-162">若要清除或以其他方式处理数据，请参阅[准备建模的数据](prepare-data-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="5ab24-163">准备好建模后，请参阅[训练和评估模型](train-machine-learning-model-ml-net.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab24-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
