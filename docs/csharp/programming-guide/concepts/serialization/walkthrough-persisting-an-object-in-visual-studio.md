---
title: "Procédure pas à pas : persistance d’un objet dans Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b1a3fc377875ee25baa0718a25b5ac509822154
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a><span data-ttu-id="ed79c-102">Procédure pas à pas : persistance d’un objet dans Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="ed79c-102">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>
<span data-ttu-id="ed79c-103">Bien qu’il soit possible de définir des valeur par défaut pour les propriétés d’un objet au moment du design, les valeurs entrées lors de l’exécution sont perdues en cas de destruction de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed79c-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="ed79c-104">Vous pouvez utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, ce qui vous permet de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed79c-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
 <span data-ttu-id="ed79c-105">Dans cette procédure pas à pas, vous allez créer un objet `Loan` simple et rendre ses données persistantes dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="ed79c-105">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="ed79c-106">Vous récupérerez ensuite les données du fichier lors de la recréation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed79c-106">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed79c-107">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="ed79c-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="ed79c-108">Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="ed79c-108">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="ed79c-109">Les autorisations sont définies à l’aide de listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="ed79c-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="ed79c-110">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, ce qui représente une autorisation inférieure.</span><span class="sxs-lookup"><span data-stu-id="ed79c-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="ed79c-111">Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier (plutôt que l’autorisation Créer sur un dossier).</span><span class="sxs-lookup"><span data-stu-id="ed79c-111">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="ed79c-112">En outre, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.</span><span class="sxs-lookup"><span data-stu-id="ed79c-112">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed79c-113">Cet exemple stocke les données dans un fichier au format binaire.</span><span class="sxs-lookup"><span data-stu-id="ed79c-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="ed79c-114">Ces formats ne doivent pas être utilisés pour des données sensibles, telles que les mots de passe ou les informations relatives à la carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="ed79c-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed79c-115">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="ed79c-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ed79c-116">Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="ed79c-116">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ed79c-117">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ed79c-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="ed79c-118">Création de l’objet Loan</span><span class="sxs-lookup"><span data-stu-id="ed79c-118">Creating the Loan Object</span></span>  
 <span data-ttu-id="ed79c-119">La première étape consiste à créer une classe `Loan` et une application de test qui utilise cette classe.</span><span class="sxs-lookup"><span data-stu-id="ed79c-119">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="ed79c-120">Pour créer la classe Loan</span><span class="sxs-lookup"><span data-stu-id="ed79c-120">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="ed79c-121">Créez un projet Bibliothèque de classes et nommez-le « LoanClass ».</span><span class="sxs-lookup"><span data-stu-id="ed79c-121">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="ed79c-122">Pour plus d’informations, consultez [Création de solutions et de projets](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="ed79c-122">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="ed79c-123">Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le fichier Class1, puis choisissez **Renommer**.</span><span class="sxs-lookup"><span data-stu-id="ed79c-123">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="ed79c-124">Renommez le fichier `Loan` et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="ed79c-124">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="ed79c-125">Quand vous renommez le fichier, la classe est également renommée `Loan`.</span><span class="sxs-lookup"><span data-stu-id="ed79c-125">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="ed79c-126">Ajoutez les membres publics suivants à la classe :</span><span class="sxs-lookup"><span data-stu-id="ed79c-126">Add the following public members to the class:</span></span>  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 <span data-ttu-id="ed79c-127">Vous devrez également créer une application simple qui utilise la classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="ed79c-127">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="ed79c-128">Pour créer une application de test</span><span class="sxs-lookup"><span data-stu-id="ed79c-128">To create a test application</span></span>  
  
1.  <span data-ttu-id="ed79c-129">Pour ajouter un projet d’application Windows Forms à votre solution, dans le menu **Fichier**, choisissez **Ajouter**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="ed79c-129">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="ed79c-130">Dans la boîte de dialogue **Ajouter un nouveau projet**, choisissez **Application Windows Forms** et entrez `LoanApp` comme nom du projet, puis cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ed79c-130">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="ed79c-131">Dans l’**Explorateur de solutions**, choisissez le projet LoanApp.</span><span class="sxs-lookup"><span data-stu-id="ed79c-131">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="ed79c-132">Dans le menu **Projet**, choisissez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="ed79c-132">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="ed79c-133">Dans le menu **Projet** , choisissez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="ed79c-133">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="ed79c-134">Dans la boîte de dialogue **Ajouter une référence**, choisissez l’onglet **Projets**, puis le projet LoanClass.</span><span class="sxs-lookup"><span data-stu-id="ed79c-134">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="ed79c-135">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ed79c-135">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="ed79c-136">Dans le concepteur, ajoutez quatre contrôles <xref:System.Windows.Forms.TextBox> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="ed79c-136">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="ed79c-137">Dans l'éditeur de code, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ed79c-137">In the Code Editor, add the following code:</span></span>  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. <span data-ttu-id="ed79c-138">Ajoutez un gestionnaire d’événements pour l’événement `PropertyChanged` au formulaire en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ed79c-138">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 <span data-ttu-id="ed79c-139">À ce stade, vous pouvez générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ed79c-139">At this point, you can build and run the application.</span></span> <span data-ttu-id="ed79c-140">Notez que les valeurs par défaut de la classe `Loan` apparaissent dans les zones de texte.</span><span class="sxs-lookup"><span data-stu-id="ed79c-140">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="ed79c-141">Essayez de remplacer le taux d’intérêt 7,5 par 7,1, puis fermez l’application et exécutez-la de nouveau : le taux reprend sa valeur par défaut de 7,5.</span><span class="sxs-lookup"><span data-stu-id="ed79c-141">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="ed79c-142">Dans la réalité, les taux d’intérêt changent régulièrement, mais pas nécessairement chaque fois que l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="ed79c-142">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="ed79c-143">Plutôt que d’imposer à l’utilisateur de mettre à jour le taux d’intérêt chaque fois qu’il exécute l’application, il peut être plus judicieux de conserver le taux d’intérêt le plus récent entre les instances de l’application.</span><span class="sxs-lookup"><span data-stu-id="ed79c-143">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="ed79c-144">C’est ce que vous ferez à l’étape suivante, en ajoutant la sérialisation à la classe Loan.</span><span class="sxs-lookup"><span data-stu-id="ed79c-144">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="ed79c-145">Utilisation de la sérialisation pour rendre l’objet persistant</span><span class="sxs-lookup"><span data-stu-id="ed79c-145">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="ed79c-146">Pour rendre les valeurs de la classe Loan persistantes, vous devez d’abord marquer la classe avec l’attribut `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="ed79c-146">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="ed79c-147">Pour marquer une classe comme étant sérialisable</span><span class="sxs-lookup"><span data-stu-id="ed79c-147">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="ed79c-148">Modifiez la déclaration de la classe Loan de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ed79c-148">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 <span data-ttu-id="ed79c-149">L’attribut `Serializable` indique au compilateur que tout ce que contient la classe peut être persistant dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="ed79c-149">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="ed79c-150">Étant donné que l’événement `PropertyChanged` est géré par un objet Windows Form, il ne peut pas être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="ed79c-150">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="ed79c-151">L’attribut `NonSerialized` peut être utilisé pour marquer les membres de la classe qui ne doivent pas être persistants.</span><span class="sxs-lookup"><span data-stu-id="ed79c-151">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="ed79c-152">Pour empêcher la sérialisation d’un membre</span><span class="sxs-lookup"><span data-stu-id="ed79c-152">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="ed79c-153">Modifiez la déclaration de l’événement `PropertyChanged` comme suit :</span><span class="sxs-lookup"><span data-stu-id="ed79c-153">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 <span data-ttu-id="ed79c-154">L’étape suivante consiste à ajouter le code de sérialisation à l’application LoanApp.</span><span class="sxs-lookup"><span data-stu-id="ed79c-154">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="ed79c-155">Pour sérialiser la classe et l’écrire dans un fichier, vous utiliserez les espaces de noms <xref:System.IO> et <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="ed79c-155">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="ed79c-156">Pour éviter de taper les noms qualifiés complets, vous pouvez ajouter des références aux bibliothèques de classes requises.</span><span class="sxs-lookup"><span data-stu-id="ed79c-156">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="ed79c-157">Pour ajouter des références aux espaces de noms</span><span class="sxs-lookup"><span data-stu-id="ed79c-157">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="ed79c-158">Ajoutez les instructions suivantes au début de la classe `Form1` :</span><span class="sxs-lookup"><span data-stu-id="ed79c-158">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     <span data-ttu-id="ed79c-159">Dans ce cas, vous utilisez un formateur binaire pour enregistrer l’objet sous un format binaire.</span><span class="sxs-lookup"><span data-stu-id="ed79c-159">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="ed79c-160">L’étape suivante consiste à ajouter le code permettant de désérialiser l’objet à partir du fichier lors de la création de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ed79c-160">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="ed79c-161">Pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="ed79c-161">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="ed79c-162">Ajoutez une constante à la classe pour le nom de fichier des données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="ed79c-162">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  <span data-ttu-id="ed79c-163">Modifiez le code de la procédure événementielle `Form1_Load` de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ed79c-163">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     <span data-ttu-id="ed79c-164">Notez que vous devez d’abord vérifier que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="ed79c-164">Note that you first must check that the file exists.</span></span> <span data-ttu-id="ed79c-165">S’il existe, créez une classe <xref:System.IO.Stream> pour lire le fichier binaire et une classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour convertir le fichier.</span><span class="sxs-lookup"><span data-stu-id="ed79c-165">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="ed79c-166">Vous devez également convertir le type de flux en type d’objet Loan.</span><span class="sxs-lookup"><span data-stu-id="ed79c-166">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="ed79c-167">Vous devez ensuite ajouter le code permettant d’enregistrer les données saisies dans les zones de texte dans la classe `Loan`, puis sérialiser la classe dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="ed79c-167">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="ed79c-168">Pour enregistrer les données et sérialiser la classe</span><span class="sxs-lookup"><span data-stu-id="ed79c-168">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="ed79c-169">Ajoutez le code suivant à la procédure événementielle `Form1_FormClosing` :</span><span class="sxs-lookup"><span data-stu-id="ed79c-169">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 <span data-ttu-id="ed79c-170">À ce stade, vous pouvez de nouveau générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ed79c-170">At this point, you can again build and run the application.</span></span> <span data-ttu-id="ed79c-171">À l’origine, les valeurs par défaut s’affichent dans les zones de texte.</span><span class="sxs-lookup"><span data-stu-id="ed79c-171">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="ed79c-172">Essayez de modifier les valeurs et d’entrer un nom dans la quatrième zone de texte.</span><span class="sxs-lookup"><span data-stu-id="ed79c-172">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="ed79c-173">Fermez l’application et exécutez-la de nouveau.</span><span class="sxs-lookup"><span data-stu-id="ed79c-173">Close the application and then run it again.</span></span> <span data-ttu-id="ed79c-174">Notez que les nouvelles valeurs s’affichent maintenant dans les zones de texte.</span><span class="sxs-lookup"><span data-stu-id="ed79c-174">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed79c-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed79c-175">See Also</span></span>  
 [<span data-ttu-id="ed79c-176">Sérialisation (C# )</span><span class="sxs-lookup"><span data-stu-id="ed79c-176">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="ed79c-177">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ed79c-177">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
