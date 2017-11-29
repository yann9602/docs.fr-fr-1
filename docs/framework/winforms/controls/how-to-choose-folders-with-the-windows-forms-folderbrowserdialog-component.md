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
ms.openlocfilehash: 0824fb70fa67628326af38ff7fb5e6c097a0378c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="ca697-102">Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca697-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="ca697-103">Souvent, dans les applications Windows que vous créez, vous devez demander aux utilisateurs de sélectionner un dossier, le plus souvent pour enregistrer un ensemble de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ca697-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="ca697-104">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> composant vous permet de facilement accomplir cette tâche.</span><span class="sxs-lookup"><span data-stu-id="ca697-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="ca697-105">Pour sélectionner des dossiers avec le composant FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="ca697-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1.  <span data-ttu-id="ca697-106">Dans une procédure, vérifiez le <xref:System.Windows.Forms.FolderBrowserDialog> du composant <xref:System.Windows.Forms.Form.DialogResult%2A> à déterminer comment la boîte de dialogue a été fermée et obtenir la valeur de la <xref:System.Windows.Forms.FolderBrowserDialog> du composant <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="ca697-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2.  <span data-ttu-id="ca697-107">Si vous devez dossier ensemble le plus élevé qui apparaît dans l’arborescence de la boîte de dialogue, définissez la <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriété, qui utilise un membre de la <xref:System.Environment.SpecialFolder> énumération.</span><span class="sxs-lookup"><span data-stu-id="ca697-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3.  <span data-ttu-id="ca697-108">En outre, vous pouvez définir le <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> propriété qui spécifie la chaîne de texte qui apparaît en haut de l’arborescence des dossiers.</span><span class="sxs-lookup"><span data-stu-id="ca697-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="ca697-109">Dans l’exemple ci-dessous, le <xref:System.Windows.Forms.FolderBrowserDialog> composant est utilisé pour sélectionner un dossier, de la même manière lorsque vous créez un projet dans Visual Studio et que vous êtes invité à sélectionner un dossier pour l’enregistrer.</span><span class="sxs-lookup"><span data-stu-id="ca697-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="ca697-110">Dans cet exemple, le nom du dossier est ensuite affiché dans un <xref:System.Windows.Forms.TextBox> contrôle du formulaire.</span><span class="sxs-lookup"><span data-stu-id="ca697-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="ca697-111">Il est judicieux d’affecter à l’emplacement dans une zone modifiable, comme un <xref:System.Windows.Forms.TextBox> contrôler, afin que les utilisateurs peuvent modifier sa sélection en cas d’erreur ou d’autres problèmes.</span><span class="sxs-lookup"><span data-stu-id="ca697-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="ca697-112">Cet exemple illustre un formulaire avec un <xref:System.Windows.Forms.FolderBrowserDialog> composant et un <xref:System.Windows.Forms.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ca697-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
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
    >  <span data-ttu-id="ca697-113">Pour utiliser cette classe, votre assembly requiert un niveau de privilège accordé par le <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> propriété, qui fait partie de la <xref:System.Security.Permissions.FileIOPermissionAccess> énumération.</span><span class="sxs-lookup"><span data-stu-id="ca697-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="ca697-114">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="ca697-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="ca697-115">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ca697-115">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="ca697-116">Pour plus d’informations sur la façon d’enregistrer des fichiers, consultez [Guide pratique pour enregistrer des fichiers à l’aide du composant SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="ca697-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca697-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca697-117">See Also</span></span>  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [<span data-ttu-id="ca697-118">Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ca697-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [<span data-ttu-id="ca697-119">FolderBrowserDialog, composant</span><span class="sxs-lookup"><span data-stu-id="ca697-119">FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
