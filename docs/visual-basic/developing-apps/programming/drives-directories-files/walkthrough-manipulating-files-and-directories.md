---
title: "Manipulation de fichiers et de répertoires dans Visual Basic | Microsoft Docs"
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
- files, reading text
- reading files, text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files, walkthroughs
- Visual Basic code, file access
- files, writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files, walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a5ae7f4a720c04639191edf36425426dfc339a37
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic
Cette procédure pas à pas présente les notions de base d’E/S de fichier dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Elle décrit comment créer une petite application qui répertorie et examine des fichiers texte dans un répertoire. Pour chaque fichier texte sélectionné, l’application fournit des attributs de fichier et la première ligne de contenu. Elle comprend une option pour écrire des informations dans un fichier journal.  
  
 Cette procédure pas à pas utilise des membres de `My.Computer.FileSystem Object`, qui sont disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Pour plus d'informations, voir <xref:Microsoft.VisualBasic.FileIO.FileSystem>. À la fin de la procédure pas à pas, un exemple équivalent est fourni, qui utilise des classes de l’espace de noms <xref:System.IO>.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Dans le volet **Modèles installés**, développez **Visual Basic**, puis cliquez sur **Windows**. Dans le volet **Modèles** du milieu, cliquez sur **Application Windows Forms**.  
  
3.  Dans la zone **Nom**, tapez `FileExplorer` pour définir le nom de projet, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] ajoute le projet à l’**Explorateur de solutions** et le Concepteur Windows Forms s’ouvre.  
  
4.  Ajoutez au formulaire les contrôles répertoriés dans le tableau ci-après et définissez les valeurs de propriété correspondantes.  
  
    |Contrôle|Propriété|Valeur|  
    |-------------|--------------|-----------|  
    |**ListBox**|**Nom**|`filesListBox`|  
    |**Button**|**Nom**<br /><br /> **Texte**|`browseButton`<br /><br /> **Parcourir**|  
    |**Button**|**Nom**<br /><br /> **Texte**|`examineButton`<br /><br /> **Examiner**|  
    |**CheckBox**|**Nom**<br /><br /> **Texte**|`saveCheckBox`<br /><br /> **Enregistrer les résultats**|  
    |**FolderBrowserDialog**|**Nom**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>Pour sélectionner un dossier et répertorier les fichiers dans un dossier  
  
1.  Créez un gestionnaire d’événements `Click` pour `browseButton` en double-cliquant sur le contrôle sur le formulaire. L'éditeur de code s'ouvre.  
  
2.  Ajoutez le code ci-après au gestionnaire d'événements `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     L’appel de `FolderBrowserDialog1.ShowDialog` ouvre la boîte de dialogue **Rechercher un dossier**. Une fois que l’utilisateur a cliqué sur **OK**, la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> est envoyée en tant qu’argument à la méthode `ListFiles`, qui est ajoutée à l’étape suivante.  
  
3.  Ajoutez la méthode `ListFiles` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Ce code efface d’abord le contrôle **ListBox**.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> récupère ensuite une collection de chaînes, une pour chaque fichier dans le répertoire. La méthode `GetFiles` accepte un argument de modèle de recherche pour récupérer les fichiers qui correspondent à un modèle particulier. Dans cet exemple, seuls les fichiers ayant l’extension .txt sont retournés.  
  
     Les chaînes qui sont retournées par la méthode `GetFiles` sont ensuite ajoutées à **ListBox**.  
  
4.  Exécutez l'application. Cliquez sur le bouton **Parcourir**. Dans la boîte de dialogue **Rechercher un dossier**, accédez à un dossier qui contient des fichiers .txt, puis sélectionnez le dossier et cliquez sur **OK**.  
  
     `ListBox` contient une liste des fichiers.txt du dossier sélectionné.  
  
5.  Arrêtez l’exécution de l’application.  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>Pour obtenir les attributs d’un fichier et le contenu d’un fichier texte  
  
1.  Créez un gestionnaire d’événements `Click` pour `examineButton` en double-cliquant sur le contrôle sur le formulaire.  
  
2.  Ajoutez le code ci-après au gestionnaire d'événements `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     Le code vérifie qu’un élément est sélectionné dans le contrôle `ListBox`. Il obtient ensuite l’entrée du chemin du fichier à partir de `ListBox`. La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> est utilisée pour vérifier si le fichier existe toujours.  
  
     Le chemin du fichier est envoyé en tant qu’argument à la méthode `GetTextForOutput`, qui est ajoutée à l’étape suivante. Cette méthode retourne une chaîne qui contient des informations sur le fichier. Les informations sur le fichier s’affichent dans un élément **MessageBox**.  
  
3.  Ajoutez la méthode `GetTextForOutput` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     Le code utilise la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> pour obtenir des paramètres de fichier. Les paramètres de fichier sont ajoutés à un <xref:System.Text.StringBuilder>.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lit le contenu du fichier dans un <xref:System.IO.StreamReader>. La première ligne du contenu est obtenue à partir du `StreamReader` et est ajoutée au `StringBuilder`.  
  
4.  Exécutez l'application. Cliquez sur **Parcourir** et recherchez un dossier qui contient des fichiers .txt. Cliquez sur **OK**.  
  
     Sélectionnez un fichier dans le contrôle `ListBox`, puis cliquez sur **Examiner**. `MessageBox` affiche les informations sur le fichier.  
  
5.  Arrêtez l’exécution de l’application.  
  
### <a name="to-add-a-log-entry"></a>Pour ajouter une entrée de journal  
  
1.  Ajoutez le code suivant à la fin du gestionnaire d’événements `examineButton_Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     Le code définit le chemin du fichier journal de sorte que ce dernier soit placé dans le même répertoire que celui du fichier sélectionné. Le texte de l’entrée de journal prend comme valeur la date et l’heure actuelles, suivies des informations sur le fichier.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, avec l’argument `append` défini sur `True`, est utilisée pour créer l’entrée de journal.  
  
2.  Exécutez l'application. Accédez à un fichier texte, sélectionnez-le dans le contrôle `ListBox`, cochez la case **Enregistrer les résultats**, puis cliquez sur **Examiner**. Vérifiez que l’entrée de journal est écrite dans le fichier `log.txt`.  
  
3.  Arrêtez l’exécution de l’application.  
  
### <a name="to-use-the-current-directory"></a>Pour utiliser le répertoire actif  
  
1.  Créez un gestionnaire d’événements pour `Form1_Load` en double-cliquant sur le formulaire.  
  
2.  Ajoutez le code suivant au gestionnaire d’événements.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Ce code définit le répertoire actif comme le répertoire par défaut de l’Explorateur de dossiers.  
  
3.  Exécutez l'application. Quand vous cliquez pour la première fois sur **Parcourir**, la boîte de dialogue **Rechercher un dossier** affiche le répertoire actif.  
  
4.  Arrêtez l’exécution de l’application.  
  
### <a name="to-selectively-enable-controls"></a>Pour activer des contrôles de manière sélective  
  
1.  Ajoutez la méthode `SetEnabled` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     La méthode `SetEnabled` active ou désactive les contrôles, selon qu’un élément est sélectionné ou non dans le contrôle `ListBox`.  
  
2.  Créez un gestionnaire d’événements `SelectedIndexChanged` pour `filesListBox` en double-cliquant sur le contrôle `ListBox` sur le formulaire.  
  
3.  Ajoutez un appel à `SetEnabled` dans le nouveau gestionnaire d’événements `filesListBox_SelectedIndexChanged`.  
  
4.  Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `browseButton_Click`.  
  
5.  Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d’événements `Form1_Load`.  
  
6.  Exécutez l'application. La case **Enregistrer les résultats** et le bouton **Examiner** sont désactivés si aucun élément n’est sélectionné dans le contrôle `ListBox`.  
  
## <a name="full-example-using-mycomputerfilesystem"></a>Exemple complet de l’utilisation de My.Computer.FileSystem  
 L’exemple complet se trouve ci-dessous.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>Exemple complet de l’utilisation de System.IO  
 L’exemple équivalent suivant utilise des classes de l’espace de noms <xref:System.IO> au lieu d’utiliser des objets `My.Computer.FileSystem`.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [Procédure pas à pas : manipulation de fichiers à l’aide de méthodes du .NET Framework](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

