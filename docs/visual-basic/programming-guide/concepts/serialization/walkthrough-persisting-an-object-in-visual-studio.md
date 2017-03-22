---
title: "Persistance d’un objet dans Visual Studio (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0ff6320aee65850b8b445f445f80b4bbe2c9c254
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Procédure pas à pas : Persistance d’un objet dans Visual Studio (Visual Basic)
Bien que vous pouvez définir les propriétés d’un objet les valeurs par défaut au moment du design, toute valeur entrée au moment de l’exécution est perdues lorsque l’objet est détruit. Vous pouvez utiliser la sérialisation pour conserver les données d’un objet entre des instances, ce qui vous permet de stocker des valeurs et de les récupérer à la prochaine fois que l’objet est instancié.  
  
> [!NOTE]
>  Dans Visual Basic, pour stocker des données simples, telles que le nom ou le numéro que vous pouvez utiliser la `My.Settings` objet. Pour plus d’informations, consultez [My.Settings (objet)](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 Dans cette procédure pas à pas, vous allez créer une simple `Loan` de l’objet et conserver ses données dans un fichier. Vous serez ensuite récupérer les données à partir du fichier lorsque vous recréez l’objet.  
  
> [!IMPORTANT]
>  Cet exemple crée un nouveau fichier, si le fichier n’existe pas déjà. Si une application doit créer un fichier, elle doit `Create` autorisation pour le dossier. Les autorisations sont définies à l’aide de listes de contrôle d’accès. Si le fichier existe déjà, l’application doit uniquement `Write` autorisation, une autorisation inférieure. Si possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder `Read` des autorisations pour un seul fichier (au lieu de créer des autorisations pour un dossier). En outre, il est plus sûr d’écrire des données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.  
  
> [!IMPORTANT]
>  Cet exemple stocke les données dans un fichier binaire. Ces formats ne doivent pas servir pour les données sensibles, telles que les mots de passe ou des informations de carte de crédit.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-loan-object"></a>Création de l’objet de prêt  
 La première étape consiste à créer un `Loan` classe et une application de test qui utilise la classe.  
  
### <a name="to-create-the-loan-class"></a>Pour créer la classe Loan  
  
1.  Créez un nouveau projet de bibliothèque de classes et nommez-le « LoanClass ». Pour plus d’informations, consultez [Création de solutions et de projets](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier Class1 et choisissez **renommer**. Renommez le fichier `Loan` et appuyez sur ENTRÉE. Renommer le fichier sera également renommer la classe `Loan`.  
  
3.  Ajoutez les membres publics suivants à la classe :  
  
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
  
 Vous devrez également créer une application simple qui utilise le `Loan` classe.  
  
### <a name="to-create-a-test-application"></a>Pour créer une application de test  
  
1.  Pour ajouter un projet d’Application Windows Forms à votre solution, sur le **fichier** menu, choisissez **ajouter**,**nouveau projet**.  
  
2.  Dans le **ajouter un nouveau projet** boîte de dialogue, sélectionnez **Application Windows Forms**, entrez `LoanApp` comme nom de projet, puis cliquez sur **OK** pour fermer la boîte de dialogue.  
  
3.  Dans **l’Explorateur de solutions**, sélectionnez le projet LoanApp.  
  
4.  Sur le **projet** menu, choisissez **définir comme projet de démarrage**.  
  
5.  Dans le menu **Projet** , choisissez **Ajouter une référence**.  
  
6.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez le **projets** onglet, puis choisissez le projet LoanClass.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
8.  Dans le concepteur, ajoutez quatre <xref:System.Windows.Forms.TextBox>contrôles au formulaire.</xref:System.Windows.Forms.TextBox>  
  
9. Dans l'éditeur de code, ajoutez le code suivant :  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. Ajoutez un gestionnaire d’événements pour le `PropertyChanged` événement au formulaire en utilisant le code suivant :  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 À ce stade, vous pouvez générer et exécuter l’application. Notez que les valeurs par défaut à partir de la `Loan` classe apparaissent dans les zones de texte. Essayez de modifier la valeur de taux d’intérêt de 7.5 et 7.1, puis fermez l’application et exécutez-la de nouveau : la valeur revient à la valeur par défaut de 7.5.  
  
 Dans le monde réel, les taux d’intérêt changent régulièrement, mais pas nécessairement chaque fois que l’application est exécutée. Plutôt que d’effectuer à l’utilisateur de mettre à jour le taux d’intérêt chaque fois que l’application s’exécute, il est préférable de conserver le taux d’intérêt le plus récent entre des instances de l’application. Dans l’étape suivante, vous effectuerez qu’en ajoutant la sérialisation à la classe de prêt.  
  
## <a name="using-serialization-to-persist-the-object"></a>À l’aide de la sérialisation pour conserver l’objet  
 Afin de rendre persistantes les valeurs de la classe Loan, vous devez tout d’abord marquer la classe avec le `Serializable` attribut.  
  
### <a name="to-mark-a-class-as-serializable"></a>Pour marquer une classe comme sérialisable  
  
-   Modifiez la déclaration de classe de la classe Loan comme suit :  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 Le `Serializable` attribut indique au compilateur que tous les éléments de la classe peuvent être persistant dans un fichier. Étant donné que le `PropertyChanged` est géré par un objet Windows Form, il ne peut pas être sérialisé. Le `NonSerialized` attribut peut être utilisé pour marquer les membres de classe qui ne doivent pas être persistants.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Pour empêcher la sérialisation d’un membre  
  
-   Modifiez la déclaration de la `PropertyChanged` événement comme suit :  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 L’étape suivante consiste à ajouter le code de sérialisation à l’application LoanApp. Pour sérialiser la classe et l’écrire dans un fichier, vous allez utiliser le <xref:System.IO>et <xref:System.Xml.Serialization>espaces de noms.</xref:System.Xml.Serialization> </xref:System.IO> Pour éviter de taper les noms qualifiés complets, vous pouvez ajouter des références aux bibliothèques de classes nécessaires.  
  
### <a name="to-add-references-to-namespaces"></a>Pour ajouter des références aux espaces de noms  
  
-   Ajoutez les instructions suivantes en haut de la `Form1` classe :  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     Dans ce cas, vous utilisez un formateur binaire pour enregistrer l’objet dans un format binaire.  
  
 L’étape suivante consiste à ajouter du code pour désérialiser l’objet à partir du fichier lorsque l’objet est créé.  
  
### <a name="to-deserialize-an-object"></a>Pour désérialiser un objet  
  
1.  Ajoutez une constante à la classe pour le nom de fichier des données sérialisées.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  Modifier le code dans la `Form1_Load` procédure d’événement comme suit :  
  
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
  
     Notez que vous devez tout d’abord vérifier que le fichier existe. S’il existe, créez un <xref:System.IO.Stream>classe pour lire le fichier binaire et une <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>classe pour convertir le fichier.</xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> </xref:System.IO.Stream> Vous devez également convertir le type de flux pour le type d’objet prêt.  
  
 Vous devez ensuite ajouter le code pour enregistrer les données entrées dans les zones de texte pour le `Loan` (classe), puis de sérialiser la classe dans un fichier.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Pour enregistrer les données et sérialiser la classe  
  
-   Ajoutez le code suivant à la `Form1_FormClosing` procédure d’événement :  
  
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
  
 À ce stade, vous pouvez à nouveau générer et exécuter l’application. Initialement, les valeurs par défaut apparaissent dans les zones de texte. Essayez de modifier les valeurs et entrez un nom dans la quatrième zone de texte. Fermez l’application et exécutez-le à nouveau. Notez que les nouvelles valeurs s’affichent maintenant dans les zones de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)
