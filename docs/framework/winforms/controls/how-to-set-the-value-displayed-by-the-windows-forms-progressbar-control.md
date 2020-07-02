---
title: 设置 ProgressBar 控件显示的值
description: 了解如何设置 Windows 窗体 ProgressBar 控件显示的值。 可以选择使用多种方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 75fe1b416636471d797a39134f45a05c972c9d39
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618098"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>如何：设置 Windows 窗体 ProgressBar 控件显示的值
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> 控件取代了 <xref:System.Windows.Forms.ProgressBar> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.ProgressBar> 控件以实现向后兼容并供将来使用。  
  
 .NET Framework 提供了几种不同的方法来在控件中显示给定的值 <xref:System.Windows.Forms.ProgressBar> 。 选择哪种方法取决于手头的任务或要解决的问题。 下表显示了可以选择的方法。  
  
|方法|描述|  
|--------------|-----------------|  
|直接设置控件的值 <xref:System.Windows.Forms.ProgressBar> 。|此方法对于你知道将涉及的项（如从数据源读取记录）的总数的任务非常有用。 此外，如果只需设置一次或两次该值，这就是一种简单的方法。 最后，如果需要减少进度栏显示的值，请使用此过程。|  
|<xref:System.Windows.Forms.ProgressBar>按固定值增加显示。|当显示最小值和最大值之间的简单计数时，此方法非常有用，例如已用时间或已处理的文件数。|  
|<xref:System.Windows.Forms.ProgressBar>按变化的值增加显示。|当你需要将显示的值更改为不同数量的次数时，此方法非常有用。 例如，显示将一系列文件写入磁盘时使用的硬盘空间量。|  
  
 设置进度栏显示的值的最直接方式是设置 <xref:System.Windows.Forms.ProgressBar.Value%2A> 属性。 这可以在设计时或运行时执行。  
  
### <a name="to-set-the-progressbar-value-directly"></a>直接设置 ProgressBar 值  
  
1. 设置 <xref:System.Windows.Forms.ProgressBar> 控件的 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 值。  
  
2. 在 "代码" 中，将控件的 <xref:System.Windows.Forms.ProgressBar.Value%2A> 属性设置为一个整数值，该整数值介于已建立的最小值和最大值之间。  
  
    > [!NOTE]
    > 如果在 <xref:System.Windows.Forms.ProgressBar.Value%2A> 和属性所建立的边界外设置属性 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> <xref:System.Windows.Forms.ProgressBar.Maximum%2A> ，控件将引发 <xref:System.ArgumentException> 异常。  
  
     下面的代码示例演示如何 <xref:System.Windows.Forms.ProgressBar> 直接设置值。 此代码从数据源读取记录，并在每次读取数据记录时更新进度栏和标签。 此示例要求窗体具有一个 <xref:System.Windows.Forms.Label> 控件、一个 <xref:System.Windows.Forms.ProgressBar> 控件和一个数据表，其中有一个名 `CustomerRow` 为的行 `FirstName` 和一个 `LastName` 字段。  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     如果正在按固定间隔显示进度，则可以设置此值，然后调用一个方法，该方法可 <xref:System.Windows.Forms.ProgressBar> 按该间隔增加控件的值。 这适用于不以整体百分比度量进度的计时器和其他方案。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>按固定值增大进度栏  
  
1. 设置 <xref:System.Windows.Forms.ProgressBar> 控件的 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 值。  
  
2. 将控件的 <xref:System.Windows.Forms.ProgressBar.Step%2A> 属性设置为一个整数，该整数表示进度栏的显示值的增加量。  
  
3. 调用 <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> 方法以更改属性中设置的数量所显示的值 <xref:System.Windows.Forms.ProgressBar.Step%2A> 。  
  
     下面的代码示例说明了进度栏如何维护复制操作中的文件计数。  
  
     在下面的示例中，将每个文件读入内存中时，会更新进度栏和标签以反映读取的文件总数。 此示例要求窗体具有 <xref:System.Windows.Forms.Label> 控件和 <xref:System.Windows.Forms.ProgressBar> 控件。  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     最后，您可以增大进度栏显示的值，以便每个增加都是唯一的。 当您跟踪一系列独特操作（如将不同大小的文件写入硬盘，或以整体百分比度量进度）时，这非常有用。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>按动态值增大进度栏  
  
1. 设置 <xref:System.Windows.Forms.ProgressBar> 控件的 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 值。  
  
2. 调用 <xref:System.Windows.Forms.ProgressBar.Increment%2A> 方法以更改由指定的整数显示的值。  
  
     下面的代码示例说明了进度栏如何计算在复制操作过程中使用的磁盘空间量。  
  
     在以下示例中，将每个文件写入硬盘时，会更新进度栏和标签以反映可用的硬盘空间量。 此示例要求窗体具有 <xref:System.Windows.Forms.Label> 控件和 <xref:System.Windows.Forms.ProgressBar> 控件。  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar 控件概述](progressbar-control-overview-windows-forms.md)
- [ProgressBar 控件](progressbar-control-windows-forms.md)
