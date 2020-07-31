---
title: 如何比较两个文件夹的内容 (LINQ) (C#)
description: 此示例演示了使用 C# 中的 LINQ 查询来比较文件列表的三种方法。 使用这些方法来比较任何类型的对象序列。
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: 3cdac57d3d746aa2290c51d1263a7d42dc3463e0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105333"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="fda2d-104">如何比较两个文件夹的内容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fda2d-104">How to compare the contents of two folders (LINQ) (C#)</span></span>
<span data-ttu-id="fda2d-105">此示例演示了比较两个文件列表的 3 种方法：</span><span class="sxs-lookup"><span data-stu-id="fda2d-105">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="fda2d-106">通过查询布尔值指定两个文件列表是否相同。</span><span class="sxs-lookup"><span data-stu-id="fda2d-106">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="fda2d-107">通过查询交集检索同时存在于两个文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="fda2d-107">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="fda2d-108">通过查询差集检索仅存在于一个文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="fda2d-108">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fda2d-109">此处的方法适用于比较任何类型的对象序列。</span><span class="sxs-lookup"><span data-stu-id="fda2d-109">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="fda2d-110">此处的 `FileComparer` 类演示如何将自定义比较器类与标准查询运算符结合使用。</span><span class="sxs-lookup"><span data-stu-id="fda2d-110">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="fda2d-111">此类不适合在实际方案中使用。</span><span class="sxs-lookup"><span data-stu-id="fda2d-111">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="fda2d-112">它仅使用每个文件的名称和字节长度来确定每个文件夹的内容是否相同。</span><span class="sxs-lookup"><span data-stu-id="fda2d-112">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="fda2d-113">在实际方案中，应修改此比较器以执行更严格的等同性检查。</span><span class="sxs-lookup"><span data-stu-id="fda2d-113">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fda2d-114">示例</span><span class="sxs-lookup"><span data-stu-id="fda2d-114">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Any())  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = $"{fi.Name}{fi.Length}";
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fda2d-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="fda2d-115">Compiling the Code</span></span>  
 <span data-ttu-id="fda2d-116">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="fda2d-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda2d-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="fda2d-117">See also</span></span>

- [<span data-ttu-id="fda2d-118">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="fda2d-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="fda2d-119">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="fda2d-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
