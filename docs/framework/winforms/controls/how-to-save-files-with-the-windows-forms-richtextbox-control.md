---
title: "Comment&#160;: enregistrer des fichiers avec le contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "fichiers .rtf, enregistrer dans le contrôle RichTextBox"
  - "exemples (Windows Forms), zones de texte"
  - "fichiers, enregistrer avec le contrôle RichTextBox"
  - "RichTextBox (contrôle Windows Forms), enregistrer des fichiers"
  - "fichiers RTF, enregistrer dans le contrôle RichTextBox"
  - "enregistrer des fichiers"
  - "enregistrer des fichiers, RichTextBox (contrôle)"
  - "fichiers texte, enregistrer à partir du contrôle RichTextBox"
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: enregistrer des fichiers avec le contr&#244;le RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms peut écrire les informations qu'il affiche dans l'un des formats suivants :  
  
-   Texte brut  
  
-   Texte brut Unicode  
  
-   Texte RTF  
  
-   RTF avec des espaces à la place d'objets OLE  
  
-   Texte brut avec une représentation textuelle des objets OLE  
  
 Pour enregistrer un fichier, appelez la méthode <xref:System.Windows.Forms.RichTextBox.SaveFile%2A>.  Vous pouvez également utiliser la méthode **SaveFile** pour enregistrer des données dans un flux.  Pour plus d'informations, consultez <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### Pour enregistrer le contenu du contrôle dans un fichier  
  
1.  Déterminez le chemin d'accès du fichier à enregistrer.  
  
     Dans une application réelle, vous utiliserez généralement pour cela le composant <xref:System.Windows.Forms.SaveFileDialog>.  Pour une vue d'ensemble, consultez [Vue d'ensemble du composant SaveFileDialog](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).  
  
2.  Appelez la méthode <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> en spécifiant le fichier à enregistrer et éventuellement un type de fichier.  Si vous appelez cette méthode en spécifiant un nom de fichier comme seul argument, le fichier sera enregistré au format RTF.  Pour spécifier un autre type de fichier, appelez la méthode en utilisant une valeur de l'énumération <xref:System.Windows.Forms.RichTextBoxStreamType> comme second argument.  
  
     Dans l'exemple ci\-dessous, le chemin défini pour l'emplacement du fichier au format RTF est le dossier **Mes documents**.  Cet emplacement est utilisé parce que la plupart des ordinateurs exécutant le système d'exploitation Windows incluent ce dossier.  Le choix de cet emplacement permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  L'exemple suivant suppose un formulaire auquel un contrôle <xref:System.Windows.Forms.RichTextBox> a déjà été ajouté.  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Cet exemple crée un fichier s'il n'existe pas.  Si une application doit créer un fichier, elle doit disposer de l'accès Créer pour le dossier.  Les autorisations sont définies à l'aide de listes de contrôle d'accès.  Si le fichier existe déjà, l'application a uniquement besoin de l'accès Écrire, ce qui représente un privilège inférieur.  Lorsque cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n'accorder l'accès Lire que sur un seul fichier \(plutôt que l'accès Créer sur un dossier\).  En outre, il est plus sûr d'écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)