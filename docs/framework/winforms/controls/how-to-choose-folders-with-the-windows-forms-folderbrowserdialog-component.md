---
title: "Comment&#160;: s&#233;lectionner des dossiers avec le composant FolderBrowserDialog Windows Forms | Microsoft Docs"
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
  - "répertoires (Windows Forms), choisir"
  - "répertoires (Windows Forms), sélectionner"
  - "FolderBrowserDialog (composant Windows Forms), choisir des répertoires"
  - "dossiers (Windows Forms), choisir"
  - "dossiers (Windows Forms), sélectionner"
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: s&#233;lectionner des dossiers avec le composant FolderBrowserDialog Windows Forms
Dans les applications Windows que vous créez, vous êtes souvent amené à inviter l'utilisateur à sélectionner un dossier, le plus souvent pour enregistrer des fichiers.  Le composant <xref:System.Windows.Forms.FolderBrowserDialog> Windows Forms vous permet d'effectuer cette tâche rapidement.  
  
### Pour sélectionner des dossiers avec le composant FolderBrowserDialog  
  
1.  Dans une procédure, examinez la propriété <xref:System.Windows.Forms.FolderBrowserDialog> du composant <xref:System.Windows.Forms.Form.DialogResult%2A> afin de déterminer comment la boîte de dialogue a été fermée et afin d'obtenir la valeur de la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> du composant <xref:System.Windows.Forms.FolderBrowserDialog>.  
  
2.  Si vous devez définir le dossier de niveau le plus élevé qui apparaît dans l'arborescence de la boîte de dialogue, définissez la propriété <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, qui utilise un membre de l'énumération [SpecialFolder](frlrfSystemEnvironmentSpecialFolderClassTopic).  
  
3.  Vous pouvez également définir la propriété <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>, qui précise la chaîne de texte qui apparaît au sommet de l'arborescence des dossiers.  
  
     Dans l'exemple ci\-dessous, le composant <xref:System.Windows.Forms.FolderBrowserDialog> est utilisé pour sélectionner un dossier, de la même manière que lorsque vous créez un projet dans Visual Studio et êtes invité à sélectionner un dossier dans lequel l'enregistrer.  Dans cet exemple, le nom du dossier est affiché dans un contrôle <xref:System.Windows.Forms.TextBox> sur le formulaire.  Il est judicieux d'affecter à l'emplacement une zone modifiable, par exemple un contrôle <xref:System.Windows.Forms.TextBox>, afin que l'utilisateur puisse modifier sa sélection en cas d'erreur ou autre problème.  Cet exemple illustre un formulaire avec un composant <xref:System.Windows.Forms.FolderBrowserDialog> et un contrôle <xref:System.Windows.Forms.TextBox>.  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Pour utiliser cette classe, votre assembly nécessite un niveau de privilège accordé par la propriété [FileIOPermissionAttribute.PathDiscoveryProperty](frlrfSystemSecurityPermissionsFileIOPermissionAttributeClassPathDiscoveryTopic), qui fait partie de l'énumération <xref:System.Security.Permissions.FileIOPermissionAccess>.  Si vous exécutez le programme dans un contexte partiellement fiable, le processus peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Pour plus d'informations sur l'enregistrement de fichiers, consultez [Comment : enregistrer des fichiers à l'aide du composant SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.FolderBrowserDialog>   
 [Vue d'ensemble du composant FolderBrowserDialog \(Windows Forms\)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)   
 [FolderBrowserDialog, composant](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)