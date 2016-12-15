---
title: "Walkthrough: Manipulating Files and Directories in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "files, reading text"
  - "reading files, text"
  - "I/O [Visual Basic], walkthroughs"
  - "text, writing to files"
  - "text, reading from files"
  - "reading text from files, walkthroughs"
  - "Visual Basic code, file access"
  - "files, writing text"
  - "I/O [Visual Basic], writing text to files"
  - "file access, walkthroughs"
  - "writing to files, walkthroughs"
  - "I/O [Visual Basic], reading text from files"
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
caps.handback.revision: 49
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manipulating Files and Directories in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette procédure pas à pas présente les notions de base relatives aux E\/S de fichier dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Elle décrit comment créer une petite application qui répertorie et examine des fichiers texte dans un répertoire.  Pour chaque fichier texte sélectionné, l'application fournit des attributs de fichier et la première ligne de contenu.  Il existe une option pour écrire les informations dans un fichier journal.  
  
 Cette procédure pas à pas utilise des membres de l'`My.Computer.FileSystem Object`, qui sont disponibles dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Consultez <xref:Microsoft.VisualBasic.FileIO.FileSystem> pour plus d'informations.  À la fin de la procédure pas à pas, un exemple équivalent est fourni ; il utilise des classes de l'espace de noms <xref:System.IO>.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Pour créer le projet  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Dans le volet **Modèles installés**, développez **Visual Basic**, puis cliquez sur **Windows**.  Dans le volet **Modèles** au milieu, cliquez sur **Application Windows Forms**.  
  
3.  Dans la zone **Nom**, tapez `FileExplorer` pour définir le nom du projet, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] ajoute le projet à l'**Explorateur de solutions** et le Concepteur Windows Forms s'ouvre.  
  
4.  Ajoutez au formulaire les contrôles répertoriés dans le tableau suivant et définissez les valeurs de propriété correspondantes.  
  
    |Contrôle|Propriété|Valeur|  
    |--------------|---------------|------------|  
    |**ListBox**|**Nom**|`filesListBox`|  
    |**Button**|**Nom**<br /><br /> **Texte**|`browseButton`<br /><br /> Parcourir|  
    |**Button**|**Nom**<br /><br /> **Texte**|`examineButton`<br /><br /> Examiner|  
    |**CheckBox**|**Nom**<br /><br /> **Texte**|`saveCheckBox`<br /><br /> Enregistrer les résultats|  
    |**FolderBrowserDialog**|**Nom**|`FolderBrowserDialog1`|  
  
### Pour sélectionner un dossier et répertorier les fichiers dans un dossier  
  
1.  Créez un gestionnaire d'événements de type `Click` pour `browseButton` en double\-cliquant sur le contrôle situé sur le formulaire.  L'éditeur de code s'ouvre.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     L'appel `FolderBrowserDialog1.ShowDialog` ouvre la boîte de dialogue **Rechercher un dossier**.  Lorsque l'utilisateur clique sur **OK**, la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> est envoyée comme un argument à la méthode `ListFiles`, qui est ajoutée dans l'étape suivante.  
  
3.  Ajoutez la méthode `ListFiles` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     Ce code efface d'abord le **ListBox**.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> extrait ensuite une collection de chaînes \(une pour chaque fichier dans le répertoire\).  La méthode `GetFiles` accepte un argument de modèle de recherche pour extraire les fichiers qui correspondent à un modèle particulier.  Dans cet exemple, seuls les fichiers avec l'extension .txt sont retournés.  
  
     Les chaînes retournées par la méthode `GetFiles` sont ensuite ajoutées au **ListBox**.  
  
4.  Exécutez l'application.  Cliquez sur le bouton **Parcourir**.  Dans la boîte de dialogue **Rechercher un dossier**, accédez à un dossier qui contient des fichiers .txt, puis sélectionnez ce dossier et cliquez sur **OK**.  
  
     Le `ListBox` contient la liste des fichiers .txt dans le dossier sélectionné.  
  
5.  Arrêtez l'exécution de l'application.  
  
### Pour obtenir les attributs d'un fichier et le contenu d'un fichier texte  
  
1.  Créez un gestionnaire d'événements de type `Click` pour `examineButton` en double\-cliquant sur le contrôle situé sur le formulaire.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements `Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     Le code vérifie qu'un élément est sélectionné dans le `ListBox`.  Il obtient alors l'entrée de chemin d'accès de fichier du `ListBox`.  La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> est utilisée pour vérifier si le fichier existe encore.  
  
     Le chemin d'accès du fichier est envoyé comme un argument à la méthode `GetTextForOutput`, qui est ajoutée dans l'étape suivante.  Cette méthode retourne une chaîne qui contient les informations sur le fichier.  Les informations sur le fichier s'affichent dans un **MessageBox**.  
  
3.  Ajoutez la méthode `GetTextForOutput` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     Le code utilise la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> pour obtenir les paramètres du fichier.  Ces paramètres sont ajoutés à un <xref:System.Text.StringBuilder>.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> lit le contenu du fichier dans un <xref:System.IO.StreamReader>.  La première ligne du contenu est obtenue du `StreamReader` et est ajoutée au `StringBuilder`.  
  
4.  Exécutez l'application.  Cliquez sur **Parcourir** et recherchez un dossier qui contient des fichiers .txt.  Cliquez sur **OK**.  
  
     Sélectionnez un fichier dans le `ListBox`, puis cliquez sur **Examiner**.  Un `MessageBox` affiche les informations sur le fichier.  
  
5.  Arrêtez l'exécution de l'application.  
  
### Pour ajouter une entrée du journal  
  
1.  Ajoutez le code suivant à la fin du gestionnaire d'événements `examineButton_Click`.  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     Le code définit le chemin d'accès du fichier journal de sorte que ce dernier soit placé dans le même répertoire que celui du fichier sélectionné.  Le texte de l'entrée de journal prend comme valeur la date et l'heure actuelles, suivies des informations sur le fichier.  
  
     La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>, avec l'argument `append` ayant comme valeur `True`, est utilisée pour créer l'entrée de journal.  
  
2.  Exécutez l'application.  Accédez à un fichier texte, sélectionnez\-le dans le `ListBox`, activez la case à cocher **Enregistrer les résultats**, puis cliquez sur **Examiner**.  Vérifiez que l'entrée de journal est écrite dans le fichier `log.txt`.  
  
3.  Arrêtez l'exécution de l'application.  
  
### Pour utiliser le répertoire actif  
  
1.  Créez un gestionnaire d'événements pour `Form1_Load` en double\-cliquant sur le formulaire.  
  
2.  Ajoutez le code suivant au gestionnaire d'événements.  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     Ce code définit le répertoire actif comme le répertoire par défaut de la recherche des dossiers.  
  
3.  Exécutez l'application.  Lorsque vous cliquez pour la première fois sur **Parcourir**, la boîte de dialogue **Rechercher un dossier** affiche le répertoire actif.  
  
4.  Arrêtez l'exécution de l'application.  
  
### Pour activer des contrôles de manière sélective  
  
1.  Ajoutez la méthode `SetEnabled` suivante.  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     La méthode `SetEnabled` active ou désactive les contrôles, selon qu'un élément est sélectionné ou non dans le `ListBox`.  
  
2.  Créez un gestionnaire d'événements de type `SelectedIndexChanged` pour `filesListBox` en double\-cliquant sur le contrôle `ListBox` situé sur le formulaire.  
  
3.  Ajoutez un appel à `SetEnabled` dans le nouveau gestionnaire d'événements `filesListBox_SelectedIndexChanged`.  
  
4.  Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d'événements `browseButton_Click`.  
  
5.  Ajoutez un appel à `SetEnabled` à la fin du gestionnaire d'événements `Form1_Load`.  
  
6.  Exécutez l'application.  La case à cocher **Enregistrer les résultats** et le bouton **Examiner** sont désactivés si aucun élément n'est sélectionné dans le `ListBox`.  
  
## Exemple complet de l'utilisation de My.Computer.FileSystem  
 L'exemple complet se trouve ci\-dessous.  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## Exemple complet de l'utilisation de System.IO  
 L'exemple équivalent suivant utilise des classes de l'espace de noms <xref:System.IO> au lieu d'utiliser des objets `My.Computer.FileSystem`.  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## Voir aussi  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [Walkthrough: Manipulating Files by Using .NET Framework Methods](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)