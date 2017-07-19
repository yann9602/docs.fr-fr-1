---
title: "Proc&#233;dure pas &#224; pas&#160;: ex&#233;cution d&#39;op&#233;rations de glisser-d&#233;placer dans Windows&#160;Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "glisser-déplacer, Windows Forms"
  - "Windows Forms, opérations de glisser-déplacer"
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Proc&#233;dure pas &#224; pas&#160;: ex&#233;cution d&#39;op&#233;rations de glisser-d&#233;placer dans Windows&#160;Forms
Pour exécuter des opérations de glisser\-déplacer dans des applications Windows, vous devez gérer une série d'événements, notamment les événements <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave> et <xref:System.Windows.Forms.Control.DragDrop>.  En utilisant les informations disponibles dans les arguments d'événement de ces événements, vous pouvez faciliter beaucoup les opérations glisser\-déplacer.  
  
## Faire glisser des données  
 Toutes les opérations glisser\-déplacer commencent par un glisser.  La fonctionnalité qui autorise la collecte des données au début de l'opération glisser est implémentée dans la méthode <xref:System.Windows.Forms.Control.DoDragDrop%2A>.  
  
 Dans l'exemple suivant, l'événement <xref:System.Windows.Forms.Control.MouseDown> est utilisé pour démarrer l'opération glisser parce qu'il est le plus intuitif \(la plupart des glisser\-déplacer commencent par un clic du bouton de la souris\).  Néanmoins, souvenez\-vous que n'importe quel événement peut servir à initialiser une procédure glisser\-déplacer.  
  
> [!NOTE]
>  Certains contrôles disposent d'événements personnalisés spécifiques au glisser.  Par exemple, les contrôles <xref:System.Windows.Forms.ListView> et <xref:System.Windows.Forms.TreeView> ont un événement <xref:System.Windows.Forms.TreeView.ItemDrag>.  
  
#### Pour démarrer une opération glisser  
  
1.  Dans l'événementd' <xref:System.Windows.Forms.Control.MouseDown>du contrôle où l'opération glisser commence, utilisez la méthode d' `DoDragDrop` pour définir les données à faire glisser et effet autorisé de l'opération glisser.  Pour plus d'informations, consultez <xref:System.Windows.Forms.DragEventArgs.Data%2A> et <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     L'exemple suivant illustre l'initialisation d'une opération glisser.  Le contrôle où l'opération glisser commence est un contrôle <xref:System.Windows.Forms.Button>, les données qui sont glissées constituent la chaîne qui représente la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button>, et les effets autorisés se résument aux opérations copier ou déplacer.  
  
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
    >  Il est possible d'utiliser n'importe quelles données comme paramètre de la méthode `DoDragDrop` ; dans l'exemple ci\-dessus, c'est la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> qui est utilisée \(plutôt que le codage irréversible d'une valeur ou la récupération des données d'un groupe de données\) parce que la propriété est liée à l'emplacement d'origine de l'opération glisser \(le contrôle <xref:System.Windows.Forms.Button>\).  Souvenez\-vous de ceci lorsque vous incorporez des opérations glisser\-déplacer dans vos applications Windows.  
  
 Pendant qu'une opération glisser est active, vous pouvez gérer l'événement <xref:System.Windows.Forms.Control.QueryContinueDrag>, qui « demande l'autorisation » au système de poursuivre l'opération glisser.  Lors de la gestion de cette méthode, c'est également le moment approprié pour vous d'appeler des méthodes qui auront un effet sur l'opération glisser, telle que développer un <xref:System.Windows.Forms.TreeNode> dans un contrôle <xref:System.Windows.Forms.TreeView> lorsque le curseur plane sur lui.  
  
## Déplacement des données  
 Dès que vous avez commencé à faire glisser les données d'un emplacement d'un Windows Form ou d'un contrôle Windows, vous souhaitez évidemment les déplacer ailleurs.  Le curseur change lorsqu'il passe sur une zone d'un formulaire ou d'un contrôle correctement configuré pour le déplacement des données.  Toute zone d'un Windows Form ou d'un contrôle peut être configurée pour accepter les données déplacées en définissant la propriété <xref:System.Windows.Forms.Control.AllowDrop%2A> et en gérant les événements <xref:System.Windows.Forms.Control.DragEnter> et <xref:System.Windows.Forms.Control.DragDrop>.  
  
#### Pour effectuer un déplacement  
  
1.  Affectez la valeur true à la propriété <xref:System.Windows.Forms.Control.AllowDrop%2A>.  
  
2.  Dans l'événement `DragEnter` pour le contrôle où le déplacement se produira, assurez\-vous que les données qui font l'objet de l'opération glisser sont d'un type acceptable \(dans ce cas, <xref:System.Windows.Forms.Control.Text%2A>\).  Le code définit ensuite l'effet produit lorsque le déplacement a lieu en lui attribuant une valeur de l'énumération <xref:System.Windows.Forms.DragDropEffects>.  Pour plus d'informations, consultez <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Vous pouvez définir votre propre <xref:System.Windows.Forms.DataFormats> en spécifiant votre propre objet comme paramètre <xref:System.Object> de la méthode <xref:System.Windows.Forms.DataObject.SetData%2A>.  Assurez\-vous, lors de cette opération, que l'objet spécifié est sérialisable.  Pour plus d'informations, consultez [ISerializable](frlrfSystemRuntimeSerializationISerializableClassTopic).  
  
3.  Dans l'événement <xref:System.Windows.Forms.Control.DragDrop> du contrôle où les données sont déplacées, utilisez la méthode <xref:System.Windows.Forms.DataObject.GetData%2A> pour récupérer les données que vous faites glisser.  Pour plus d'informations, consultez [DtaObject.Data Property](frlrfSystemSecurityCryptographyXmlDataObjectClassDataTopic).  
  
     Dans l'exemple ci\-dessous, le contrôle qui reçoit les données déplacées est un contrôle <xref:System.Windows.Forms.TextBox>.  Le code attribue à la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.TextBox> une valeur égale aux données déplacées.  
  
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
    >  Vous pouvez, par ailleurs, manipuler la propriété <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> afin de produire des effets spécifiques selon les touches enfoncées pendant l'opération glisser\-déplacer \(par exemple, la procédure standard veut que les données déplacées soient copiées lorsque la touche CTRL est enfoncée\).  
  
## Voir aussi  
 [Comment : ajouter des données au Presse\-papiers](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)   
 [Comment : récupérer des données du Presse\-papiers](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)   
 [Opérations glisser\-déplacer et prise en charge du Presse\-papiers](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)