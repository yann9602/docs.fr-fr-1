---
title: "Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de41d5664c2481032dffe213a52779834338ca2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms
Souvent, dans les applications Windows que vous créez, vous devez demander aux utilisateurs de sélectionner un dossier, le plus souvent pour enregistrer un ensemble de fichiers. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> composant vous permet de facilement accomplir cette tâche.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Pour sélectionner des dossiers avec le composant FolderBrowserDialog  
  
1.  Dans une procédure, vérifiez le <xref:System.Windows.Forms.FolderBrowserDialog> du composant <xref:System.Windows.Forms.Form.DialogResult%2A> à déterminer comment la boîte de dialogue a été fermée et obtenir la valeur de la <xref:System.Windows.Forms.FolderBrowserDialog> du composant <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriété.  
  
2.  Si vous devez dossier ensemble le plus élevé qui apparaît dans l’arborescence de la boîte de dialogue, définissez la <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriété, qui utilise un membre de la <xref:System.Environment.SpecialFolder> énumération.  
  
3.  En outre, vous pouvez définir le <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriété qui spécifie la chaîne de texte qui apparaît en haut de l’arborescence des dossiers.  
  
     Dans l’exemple ci-dessous, le <xref:System.Windows.Forms.FolderBrowserDialog> composant est utilisé pour sélectionner un dossier, de la même manière lorsque vous créez un projet dans Visual Studio et que vous êtes invité à sélectionner un dossier pour l’enregistrer. Dans cet exemple, le nom du dossier est ensuite affiché dans un <xref:System.Windows.Forms.TextBox> contrôle du formulaire. Il est judicieux d’affecter à l’emplacement dans une zone modifiable, comme un <xref:System.Windows.Forms.TextBox> contrôler, afin que les utilisateurs peuvent modifier sa sélection en cas d’erreur ou d’autres problèmes. Cet exemple illustre un formulaire avec un <xref:System.Windows.Forms.FolderBrowserDialog> composant et un <xref:System.Windows.Forms.TextBox> contrôle.  
  
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
    >  Pour utiliser cette classe, votre assembly requiert un niveau de privilège accordé par le <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriété, qui fait partie de la <xref:System.Security.Permissions.FileIOPermissionAccess> énumération. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Pour plus d’informations sur la façon d’enregistrer des fichiers, consultez [Guide pratique pour enregistrer des fichiers à l’aide du composant SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [FolderBrowserDialog, composant](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
