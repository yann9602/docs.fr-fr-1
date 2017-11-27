---
title: "Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms"
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
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe2b54123e117f21f3bda7bc78bc9c5b45fc9ae3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Procédure pas à pas : exécution d’opérations de glisser-déposer dans Windows Forms
Pour effectuer des opérations de glisser-déplacer dans des applications Windows vous devez gérer une série d’événements, notamment le <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, et <xref:System.Windows.Forms.Control.DragDrop> événements. En utilisant les informations disponibles dans les arguments de ces événements, vous pouvez faciliter les opérations de glisser-déplacer.  
  
## <a name="dragging-data"></a>Faire glisser des données  
 Toutes les opérations de glisser-déplacer commencent par un glisser. La fonctionnalité pour activer les données soient collectées lorsque commence à faire glisser est implémentée dans le <xref:System.Windows.Forms.Control.DoDragDrop%2A> (méthode).  
  
 Dans l’exemple suivant, la <xref:System.Windows.Forms.Control.MouseDown> événement est utilisé pour démarrer l’opération glisser, car il est le plus intuitif (la plupart des actions de glisser-déplacer commence avec le bouton de souris). N’oubliez cependant pas que n’importe quel événement peut être utilisé pour lancer une procédure de glisser-déplacer.  
  
> [!NOTE]
>  Certains contrôles ont des événements personnalisés spécifiques au glisser. Le <xref:System.Windows.Forms.ListView> et <xref:System.Windows.Forms.TreeView> contrôles, par exemple, ont un <xref:System.Windows.Forms.TreeView.ItemDrag> événement.  
  
#### <a name="to-start-a-drag-operation"></a>Pour démarrer une opération de glisser  
  
1.  Dans le <xref:System.Windows.Forms.Control.MouseDown> événement du contrôle où l’opération glisser commence, utilisez le `DoDragDrop` auront de méthode pour définir les données à faire glisser et l’effet autorisé en faisant glisser. Pour plus d’informations, consultez <xref:System.Windows.Forms.DragEventArgs.Data%2A> et <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     L’exemple suivant montre comment initier une opération glisser. Le contrôle où l’opération glisser commence est un <xref:System.Windows.Forms.Button> (contrôle), les données glissées est la chaîne qui représente le <xref:System.Windows.Forms.Control.Text%2A> propriété de la <xref:System.Windows.Forms.Button> contrôle et les effets autorisés soit copie ou de déplacement.  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    >  Toutes les données peuvent être utilisées en tant que paramètre dans le `DoDragDrop` (méthode) ; dans l’exemple ci-dessus, le <xref:System.Windows.Forms.Control.Text%2A> propriété de la <xref:System.Windows.Forms.Button> contrôle était utilisé (au lieu de coder en dur une valeur ou la récupération des données à partir d’un jeu de données) parce que la propriété est liée à la emplacement glissé à partir de (la <xref:System.Windows.Forms.Button> contrôle). Gardez cela à l’esprit quand vous incorporez des opérations de glisser-déplacer dans vos applications Windows.  
  
 Pendant qu’une opération de glissement est activée, vous pouvez gérer le <xref:System.Windows.Forms.Control.QueryContinueDrag> événement, qui « demande l’autorisation » du système pour continuer l’opération de glissement. Lors du traitement de cette méthode, il est également le moment approprié pour appeler des méthodes qui ont une incidence sur l’opération de glissement, par exemple de développer un <xref:System.Windows.Forms.TreeNode> dans un <xref:System.Windows.Forms.TreeView> contrôle lorsque le curseur pointe sur elle.  
  
## <a name="dropping-data"></a>Déposer des données  
 Une fois que vous avez commencé à faire glisser des données à partir d’un emplacement sur un Windows Form ou un contrôle, vous voulez naturellement les déposer quelque part. Le curseur change quand il passe sur une zone d’un formulaire ou d’un contrôle qui est correctement configuré pour le dépôt des données. Toute zone dans un Windows Form ou un contrôle peut être configurée pour accepter les données déplacées en définissant le <xref:System.Windows.Forms.Control.AllowDrop%2A> propriété et la gestion du <xref:System.Windows.Forms.Control.DragEnter> et <xref:System.Windows.Forms.Control.DragDrop> événements.  
  
#### <a name="to-perform-a-drop"></a>Pour effectuer un dépôt  
  
1.  Définir le <xref:System.Windows.Forms.Control.AllowDrop%2A> true à la propriété.  
  
2.  Dans le `DragEnter` événement du contrôle où le déplacement se produira, assurez-vous que les données glissées sont d’un type acceptable (dans ce cas, <xref:System.Windows.Forms.Control.Text%2A>). Le code définit ensuite l’effet se produira lors de la suppression d’une valeur dans la <xref:System.Windows.Forms.DragDropEffects> énumération. Pour plus d'informations, consultez <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    >  Vous pouvez définir vos propres <xref:System.Windows.Forms.DataFormats> en spécifiant votre propre objet en tant que le <xref:System.Object> paramètre de la <xref:System.Windows.Forms.DataObject.SetData%2A> (méthode). Pour cela, vérifiez que l’objet spécifié est sérialisable. Pour plus d'informations, consultez <xref:System.Runtime.Serialization.ISerializable>.  
  
3.  Dans le <xref:System.Windows.Forms.Control.DragDrop> événement du contrôle où le déplacement se produira, utilisez le <xref:System.Windows.Forms.DataObject.GetData%2A> pour récupérer les données glissées. Pour plus d'informations, consultez <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.TextBox> contrôle est le contrôle glissé vers (où le déplacement se produira). Le code définit les <xref:System.Windows.Forms.Control.Text%2A> propriété de la <xref:System.Windows.Forms.TextBox> contrôler égale aux données glissées.  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    >  En outre, vous pouvez travailler avec le <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> propriété, afin que, selon les touches enfoncées pendant l’opération de glisser-déplacer, certains effets se produisent (par exemple, il est standard pour copier les données déplacées lors de la touche CTRL).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour ajouter des données au Presse-papiers](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Guide pratique pour récupérer des données du Presse-papiers](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Opérations glisser-déposer et prise en charge du Presse-papiers](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
