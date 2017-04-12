---
title: "Manipulation de fichiers à l’aide de méthodes du .NET Framework (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files, writing to
- reading text files
- text, writing to files
- files, searching
- StreamReader class, walkthroughs
- files, accessing
- I/O [Visual Basic], writing text to files
- writing to files, walkthroughs
- StreamWriter class, walkthroughs
- text files, reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e8bf73f32dba51455542778ed91ef3bfd2898754
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a>Procédure pas à pas : manipulation de fichiers à l'aide de méthodes du .NET Framework (Visual Basic)
Cette procédure pas à pas illustre comment ouvrir et lire un fichier à l’aide de la classe <xref:System.IO.StreamReader>, vérifier si une tentative d’accès à un fichier est en cours, rechercher une chaîne dans un fichier lu avec une instance de la classe <xref:System.IO.StreamReader> et écrire dans un fichier à l’aide de la classe <xref:System.IO.StreamWriter>.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-application"></a>Création de l’application  
 Démarrez [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] et commencez le projet par la création d’un formulaire qui permet à l’utilisateur d’écrire dans le fichier désigné.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Dans le menu **Fichier**, sélectionnez **Nouveau projet**.  
  
2.  Dans le volet **Nouveau projet**, cliquez sur **Application Windows**.  
  
3.  Dans la zone **Nom**, tapez `MyDiary` et cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] ajoute le projet à l’**Explorateur de solutions** et le **Concepteur Windows Forms** s’ouvre.  
  
4.  Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.  
  
|**Objet**|**Propriétés**|**Valeur**|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**|`Submit`<br /><br /> **Envoyer une entrée**|  
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**|`Clear`<br /><br /> **Effacer l’entrée**|  
|<xref:System.Windows.Forms.TextBox>|**Nom**<br /><br /> **Texte**<br /><br /> **Multiline**|`Entry`<br /><br /> **Entrez quelque chose.**<br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a>Écriture dans le fichier  
 Pour permettre l’écriture dans un fichier via l’application, utilisez la classe <xref:System.IO.StreamWriter>. La classe <xref:System.IO.StreamWriter> est conçue pour la sortie de caractères dans un encodage particulier, tandis que la classe <xref:System.IO.Stream> est conçue pour l’entrée et la sortie d’octets. Utilisez <xref:System.IO.StreamWriter> pour écrire des lignes d’informations dans un fichier texte standard. Pour plus d’informations sur la classe <xref:System.IO.StreamWriter>, consultez <xref:System.IO.StreamWriter>.  
  
#### <a name="to-add-writing-functionality"></a>Pour ajouter une fonctionnalité d’écriture  
  
1.  Dans le menu **Affichage**, choisissez **Code** pour ouvrir l’éditeur de code.  
  
2.  Étant donné que l’application fait référence à l’espace de noms <xref:System.IO>, ajoutez les instructions ci-après tout au début de votre code, avant la déclaration de classe du formulaire, `Public Class Form1`.  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     Avant d’écrire dans le fichier, vous devez créer une instance d’une classe <xref:System.IO.StreamWriter>.  
  
3.  Dans le menu **Affichage**, choisissez **Concepteur** pour retourner au **Concepteur Windows Forms**. Double-cliquez sur le bouton `Submit` pour créer un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour ce bouton, puis ajoutez le code suivant.  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  L’environnement de développement intégré (IDE, Integrated Development Environment) Visual Studio revient à l’éditeur de code et positionne le point d’insertion dans le gestionnaire d’événements, à l’emplacement où vous devez ajouter le code.  
  
1.  Pour écrire dans le fichier, utilisez la méthode <xref:System.IO.StreamWriter.Write%2A> de la classe <xref:System.IO.StreamWriter>. Ajoutez le code ci-dessous immédiatement après `Dim fw As StreamWriter`. La levée d’une exception en cas de fichier introuvable ne doit pas vous inquiéter, car le fichier est créé s’il n’existe pas.  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  Vérifiez que l’utilisateur ne peut soumettre aucune entrée vide en ajoutant le code suivant immédiatement après `Dim ReadString As String`.  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  Comme il s’agit d’un agenda, l’utilisateur veut assigner une date à chaque entrée. Insérez le code suivant après `fw = New StreamWriter("C:\MyDiary.txt", True)` pour affecter la date actuelle à la variable `Today`.  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  Enfin, attachez du code pour effacer l’objet <xref:System.Windows.Forms.TextBox>. Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Clear`.  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a>Ajout de fonctionnalités d’affichage à l’agenda  
 Dans cette section, vous ajoutez une fonctionnalité qui affiche la dernière entrée dans le contrôle <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Vous pouvez également ajouter un contrôle <xref:System.Windows.Forms.ComboBox> qui présente les diverses entrées que l’utilisateur peut sélectionner pour les afficher dans le contrôle <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Une instance de la classe <xref:System.IO.StreamReader> lit `MyDiary.txt`. Comme la classe <xref:System.IO.StreamWriter>, la classe <xref:System.IO.StreamReader> est conçue pour être utilisée avec les fichiers texte.  
  
 Pour cette section de la procédure pas à pas, ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.  
  
|Contrôle|Propriétés|Valeurs|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|**Nom**<br /><br /> **Visible**<br /><br /> **Taille**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**|`Display`<br /><br /> **Afficher**|  
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**|`GetEntries`<br /><br /> **Obtenir des entrées**|  
|<xref:System.Windows.Forms.ComboBox>|**Nom**<br /><br /> **Texte**<br /><br /> **Activé**|`PickEntries`<br /><br /> **Sélectionner une entrée**<br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a>Pour remplir la zone de liste déroulante  
  
1.  Le contrôle <xref:System.Windows.Forms.ComboBox> `PickEntries` permet d’afficher les dates auxquelles un utilisateur soumet une entrée. Par conséquent, celui-ci peut sélectionner une entrée associée à une date déterminée. Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `GetEntries` et ajoutez le code suivant.  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  Pour tester votre code, appuyez sur F5 pour compiler l’application, puis cliquez sur **Obtenir des entrées**. Cliquez sur la flèche de déroulement dans le contrôle <xref:System.Windows.Forms.ComboBox> pour afficher les dates des entrées.  
  
#### <a name="to-choose-and-display-individual-entries"></a>Pour sélectionner et afficher des entrées individuelles  
  
1.  Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `Display` et ajoutez le code suivant.  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  Pour tester votre code, appuyez sur F5 pour compiler l’application, puis soumettez une entrée. Cliquez sur **Obtenir des entrées**, sélectionnez une entrée dans le contrôle <xref:System.Windows.Forms.ComboBox>, puis cliquez sur **Afficher**. Le contenu de l’entrée sélectionnée s’affiche dans le contrôle <xref:System.Windows.Forms.TextBox> `DisplayEntry`.  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a>Autorisation aux utilisateurs de supprimer ou de modifier des entrées  
 Enfin, vous pouvez inclure des fonctionnalités supplémentaires qui permettent aux utilisateurs de supprimer ou de modifier une entrée à l’aide des boutons `DeleteEntry` et `EditEntry`. Ces deux boutons restent désactivés si aucune entrée n’est affichée.  
  
 Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.  
  
|Contrôle|Propriétés|Valeurs|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**<br /><br /> **Activé**|`DeleteEntry`<br /><br /> **Supprimer l’entrée**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**<br /><br /> **Activé**|`EditEntry`<br /><br /> **Modifier l’entrée**<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**Nom**<br /><br /> **Texte**<br /><br /> **Activé**|`SubmitEdit`<br /><br /> **Envoyer la modification**<br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a>Pour activer la suppression et la modification d’entrées  
  
1.  Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Display`, après `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `DeleteEntry` et ajoutez le code suivant.  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  Quand un utilisateur affiche une entrée, le bouton `EditEntry` devient disponible. Ajoutez le code suivant à l’événement <xref:System.Windows.Forms.Control.Click> du bouton `Display`, après `DisplayEntry.Text = ReadString`.  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `EditEntry` et ajoutez le code suivant.  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  Créez un gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour le bouton `SubmitEdit` et ajoutez le code suivant  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 Pour tester votre code, appuyez sur F5 pour compiler l’application. Cliquez sur **Obtenir des entrées**, sélectionnez une entrée, puis cliquez sur **Afficher**. L’entrée s’affiche dans le contrôle <xref:System.Windows.Forms.TextBox> `DisplayEntry`. Cliquez sur **Modifier l’entrée**. L’entrée s’affiche dans le contrôle <xref:System.Windows.Forms.TextBox> `Entry`. Modifiez l’entrée dans le contrôle <xref:System.Windows.Forms.TextBox> `Entry` et cliquez sur **Envoyer la modification**. Ouvrez le fichier `MyDiary.txt` pour confirmer vos corrections. À présent, sélectionnez une entrée et cliquez sur **Supprimer l’entrée**. Quand le message <xref:System.Windows.Forms.MessageBox> vous demande de confirmer l’opération, cliquez sur **OK**. Fermez l’application et ouvrez `MyDiary.txt` pour confirmer la suppression.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamWriter>   
 [Procédures pas à pas](../../../../visual-basic/walkthroughs.md)

