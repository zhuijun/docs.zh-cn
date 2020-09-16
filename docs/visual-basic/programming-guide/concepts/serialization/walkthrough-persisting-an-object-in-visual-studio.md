---
title: 在 Visual Basic 中保持对象
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 3febd3f74510d11a7103edbd52bcae8043a5edc0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558597"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="decd5-102">演练：在 Visual Studio 中暂留对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="decd5-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="decd5-103">虽然可在设计时将对象的属性设置为默认值，但销毁对象时，运行时输入的任何值都将丢失。</span><span class="sxs-lookup"><span data-stu-id="decd5-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="decd5-104">可使用序列化在实例之间保持对象的数据，以便可存储值并在下次实例化对象时检索这些值。</span><span class="sxs-lookup"><span data-stu-id="decd5-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="decd5-105">在 Visual Basic 中，要存储简单数据（如名称或编号），可以使用 `My.Settings` 对象。</span><span class="sxs-lookup"><span data-stu-id="decd5-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="decd5-106">有关详细信息，请参阅 [My.Settings 对象](../../../language-reference/objects/my-settings-object.md)。</span><span class="sxs-lookup"><span data-stu-id="decd5-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="decd5-107">本演练将创建一个简单的 `Loan` 对象，并将其值保留在文件中。</span><span class="sxs-lookup"><span data-stu-id="decd5-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="decd5-108">当重新创建该对象时，将检索文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="decd5-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="decd5-109">此示例在文件尚未存在时创建新文件。</span><span class="sxs-lookup"><span data-stu-id="decd5-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="decd5-110">如果应用程序必须创建文件，则该应用程序必须对文件夹具有 `Create` 权限。</span><span class="sxs-lookup"><span data-stu-id="decd5-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="decd5-111">可使用访问控制列表设置权限。</span><span class="sxs-lookup"><span data-stu-id="decd5-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="decd5-112">如果文件已存在，则该应用程序只需要 `Write` 权限（这是较弱的权限）。</span><span class="sxs-lookup"><span data-stu-id="decd5-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="decd5-113">如有可能，较安全的做法是在部署过程中创建文件并仅向单个文件授予 `Read` 权限（而不是授予文件夹的“创建”权限）。</span><span class="sxs-lookup"><span data-stu-id="decd5-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="decd5-114">此外，较安全的做法是将数据写入用户文件夹，而不是根文件夹或“Program Files”文件夹。</span><span class="sxs-lookup"><span data-stu-id="decd5-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="decd5-115">此示例将数据存储为二进制格式。</span><span class="sxs-lookup"><span data-stu-id="decd5-115">This example stores data in a binary.</span></span> <span data-ttu-id="decd5-116">不应将这些格式用于敏感数据，如密码或信用卡信息。</span><span class="sxs-lookup"><span data-stu-id="decd5-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="decd5-117">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="decd5-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="decd5-118">若要更改设置，请单击 **“工具”** 菜单上的 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="decd5-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="decd5-119">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="decd5-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="decd5-120">创建 Loan 对象</span><span class="sxs-lookup"><span data-stu-id="decd5-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="decd5-121">第一步是创建 `Loan` 类和使用该类的测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="decd5-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="decd5-122">创建 Loan 类</span><span class="sxs-lookup"><span data-stu-id="decd5-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="decd5-123">新建“类库”项目，并将其命名为“LoanClass”。</span><span class="sxs-lookup"><span data-stu-id="decd5-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="decd5-124">有关详细信息，请参阅[创建解决方案和项目](/visualstudio/ide/creating-solutions-and-projects)。</span><span class="sxs-lookup"><span data-stu-id="decd5-124">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="decd5-125">在“解决方案资源管理器”\*\*\*\* 中，打开 Class1 文件的快捷菜单，选择“重命名”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="decd5-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="decd5-126">将文件重命名为 `Loan`，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="decd5-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="decd5-127">重命名文件也会将类重命名为 `Loan`。</span><span class="sxs-lookup"><span data-stu-id="decd5-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="decd5-128">将以下公共成员添加到该类中：</span><span class="sxs-lookup"><span data-stu-id="decd5-128">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="decd5-129">还需要创建一个使用 `Loan` 类的简单应用程序。</span><span class="sxs-lookup"><span data-stu-id="decd5-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="decd5-130">创建测试应用程序</span><span class="sxs-lookup"><span data-stu-id="decd5-130">To create a test application</span></span>  
  
1. <span data-ttu-id="decd5-131">若要将 Windows 窗体应用程序项目添加到解决方案，请在“文件”\*\*\*\* 菜单上依次选择“添加”\*\*\*\*、“新建项目”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="decd5-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="decd5-132">在“添加新项目”\*\*\*\* 对话框中，选择“Windows 窗体应用程序”\*\*\*\*，然后输入 `LoanApp` 作为项目名称，然后单击“确定”\*\*\*\* 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="decd5-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="decd5-133">在“解决方案资源管理器”\*\*\*\* 中，选择 LoanApp 项目。</span><span class="sxs-lookup"><span data-stu-id="decd5-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="decd5-134">在“项目”\*\*\*\* 菜单上，选择“设为启动项目”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="decd5-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="decd5-135">在“项目”\*\*\*\* 菜单上，选择“添加引用” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="decd5-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="decd5-136">在“添加引用”\*\*\*\* 对话框中，选择“项目”\*\*\*\* 选项卡，然后选择 LoanClass 项目。</span><span class="sxs-lookup"><span data-stu-id="decd5-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="decd5-137">单击“确定”  关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="decd5-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="decd5-138">在设计器中，向窗体添加四个 <xref:System.Windows.Forms.TextBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="decd5-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="decd5-139">在代码编辑器中，添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="decd5-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="decd5-140">使用以下代码将 `PropertyChanged` 事件的事件处理程序添加到窗体：</span><span class="sxs-lookup"><span data-stu-id="decd5-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="decd5-141">此时可以生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="decd5-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="decd5-142">请注意，`Loan` 类中的默认值将显示在文本框中。</span><span class="sxs-lookup"><span data-stu-id="decd5-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="decd5-143">尝试将利率值从 7.5 更改到 7.1，然后关闭该应用程序并再次运行 - 值会还原为默认值 7.5。</span><span class="sxs-lookup"><span data-stu-id="decd5-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="decd5-144">在现实生活中，利率会定期更改，但不必在每次运行应用程序时都更改利率。</span><span class="sxs-lookup"><span data-stu-id="decd5-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="decd5-145">与其让用户在每次运行应用程序时更新利率，不如在应用程序的实例之间保留最近的利率。</span><span class="sxs-lookup"><span data-stu-id="decd5-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="decd5-146">下一步是通过向 Loan 类添加序列化来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="decd5-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="decd5-147">使用序列化保持对象</span><span class="sxs-lookup"><span data-stu-id="decd5-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="decd5-148">为了保持 Loan 类的值，必须首先使用 `Serializable` 属性标记该类。</span><span class="sxs-lookup"><span data-stu-id="decd5-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="decd5-149">将类标记为可序列化</span><span class="sxs-lookup"><span data-stu-id="decd5-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="decd5-150">更改 Loan 类的类声明，如下所示：</span><span class="sxs-lookup"><span data-stu-id="decd5-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="decd5-151">`Serializable` 属性通知编译器可将类中的所有内容保持到文件中。</span><span class="sxs-lookup"><span data-stu-id="decd5-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="decd5-152">`PropertyChanged` 事件由 Windows 窗体对象处理，因此不能将其序列化。</span><span class="sxs-lookup"><span data-stu-id="decd5-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="decd5-153">可使用 `NonSerialized` 属性标记不应保持的类成员。</span><span class="sxs-lookup"><span data-stu-id="decd5-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="decd5-154">阻止对成员进行序列化</span><span class="sxs-lookup"><span data-stu-id="decd5-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="decd5-155">更改 `PropertyChanged` 事件的声明，如下所示：</span><span class="sxs-lookup"><span data-stu-id="decd5-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="decd5-156">下一步是向 LoanApp 应用程序添加序列化代码。</span><span class="sxs-lookup"><span data-stu-id="decd5-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="decd5-157">为了将该类序列化并将其写入到文件，将使用 <xref:System.IO> 和 <xref:System.Xml.Serialization> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="decd5-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="decd5-158">为了避免键入完全限定的名称，可以添加对必要类库的引用。</span><span class="sxs-lookup"><span data-stu-id="decd5-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="decd5-159">添加对命名空间的引用</span><span class="sxs-lookup"><span data-stu-id="decd5-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="decd5-160">将下面的语句添加到 `Form1` 类的顶部：</span><span class="sxs-lookup"><span data-stu-id="decd5-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="decd5-161">在这种情况下，将使用二进制格式化程序以二进制格式保存对象。</span><span class="sxs-lookup"><span data-stu-id="decd5-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="decd5-162">下一步是添加代码，在创建对象时对文件中的对象进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="decd5-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="decd5-163">反序列化对象</span><span class="sxs-lookup"><span data-stu-id="decd5-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="decd5-164">向序列化数据的文件名的类中添加一个常量。</span><span class="sxs-lookup"><span data-stu-id="decd5-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="decd5-165">修改 `Form1_Load` 事件过程中的代码，如下所示：</span><span class="sxs-lookup"><span data-stu-id="decd5-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="decd5-166">请注意，首先必须检查该文件是否存在。</span><span class="sxs-lookup"><span data-stu-id="decd5-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="decd5-167">如果存在，则创建 <xref:System.IO.Stream> 类来读取二进制文件和 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 类，以转换该文件。</span><span class="sxs-lookup"><span data-stu-id="decd5-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="decd5-168">还需将流类型转换为 Loan 对象类型。</span><span class="sxs-lookup"><span data-stu-id="decd5-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="decd5-169">接下来，必须添加代码以将本文框中输入的数据保存到 `Loan` 类，然后必须将类序列化到文件中。</span><span class="sxs-lookup"><span data-stu-id="decd5-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="decd5-170">保存数据并对类进行序列化</span><span class="sxs-lookup"><span data-stu-id="decd5-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="decd5-171">将以下代码添加到 `Form1_FormClosing` 事件过程中：</span><span class="sxs-lookup"><span data-stu-id="decd5-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="decd5-172">此时可再次生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="decd5-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="decd5-173">最初，默认值在文本框中显示。</span><span class="sxs-lookup"><span data-stu-id="decd5-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="decd5-174">尝试更改这些值并在第四个文本框中输入名称。</span><span class="sxs-lookup"><span data-stu-id="decd5-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="decd5-175">关闭该应用程序，然后重新运行。</span><span class="sxs-lookup"><span data-stu-id="decd5-175">Close the application and then run it again.</span></span> <span data-ttu-id="decd5-176">请注意，现在文本框中将显示新值。</span><span class="sxs-lookup"><span data-stu-id="decd5-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="decd5-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="decd5-177">See also</span></span>

- <span data-ttu-id="decd5-178">序列化 (Visual Basic)[](index.md)</span><span class="sxs-lookup"><span data-stu-id="decd5-178">[Serialization (Visual Basic)](index.md)</span></span>
- [<span data-ttu-id="decd5-179">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="decd5-179">Visual Basic Programming Guide</span></span>](../../index.md)
