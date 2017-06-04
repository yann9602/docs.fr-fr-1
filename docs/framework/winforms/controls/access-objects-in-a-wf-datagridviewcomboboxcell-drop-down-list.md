---
title: "Comment&#160;: acc&#233;der &#224; des objets dans une liste d&#233;roulante DataGridViewComboBoxCell Windows Forms | Microsoft Docs"
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
  - "zones de liste déroulante, accéder à des objets dans des listes déroulantes DataGridViewComboBoxCell"
  - "zones de liste déroulante, dans le contrôle DataGridView"
  - "DataGridView (contrôle Windows Forms), accéder à des objets dans des cellules de zone de liste déroulante"
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: acc&#233;der &#224; des objets dans une liste d&#233;roulante DataGridViewComboBoxCell Windows Forms
Comme le contrôle <xref:System.Windows.Forms.ComboBox>, les types <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et <xref:System.Windows.Forms.DataGridViewComboBoxCell> vous permettent d'ajouter des objets arbitraires à leurs listes déroulantes.  Cette fonctionnalité vous permet de représenter des états complexes dans une liste déroulante sans devoir stocker les objets correspondants dans une collection séparée.  
  
 Contrairement au contrôle <xref:System.Windows.Forms.ComboBox>, les types <xref:System.Windows.Forms.DataGridView> n'ont pas de propriété <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> pour récupérer l'objet actuellement sélectionné.  À la place, vous devez affecter à la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=fullName> le nom d'une propriété de votre objet métier.  Lorsque l'utilisateur effectue une sélection, la propriété indiquée de l'objet métier définit la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule.  
  
 Pour récupérer l'objet métier par le biais de la valeur de la cellule, la propriété `ValueMember` doit indiquer une propriété qui retourne une référence à l'objet métier lui\-même.  Par conséquent, si le type de l'objet métier n'est pas sous votre contrôle, vous devez ajouter une telle propriété en étendant le type via l'héritage.  
  
 Les procédures suivantes montrent comment remplir une liste déroulante avec les objets métier et récupérer les objets par le biais de la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule.  
  
### Pour ajouter des objets métier à la liste déroulante  
  
1.  Créez une <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et remplissez sa collection <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>.  Vous pouvez également affecter à la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> de la colonne la collection des objets métier.  Dans ce cas, toutefois, vous ne pouvez pas ajouter "non assigné" à la liste déroulante sans créer d'objet métier correspondant dans votre collection.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Définissez les propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indique la propriété de l'objet métier à afficher dans la liste déroulante.  <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indique la propriété qui retourne une référence à l'objet métier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  Assurez\-vous que le type de l'objet métier contient une propriété qui retourne une référence à l'instance actuelle.  Cette propriété doit être nommée avec la valeur assignée à <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> à l'étape précédente.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### Pour récupérer l'objet métier actuellement sélectionné  
  
-   Obtenez la propriété <xref:System.Windows.Forms.DataGridViewCell.Value%2A> de la cellule et effectuez un cast de cette propriété en type d'objet métier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## Exemple  
 L'exemple complet illustre l'utilisation d'objets métier dans une liste déroulante.  Dans l'exemple, un contrôle <xref:System.Windows.Forms.DataGridView> est lié à une collection d'objets `Task`.  Chaque objet `Task` a une propriété `AssignedTo` qui indique l'objet `Employee` assigné actuellement à cette tâche.  La colonne `Assigned To` affiche la valeur de propriété `Name` pour chaque employé assigné, ou "non assigné" si la valeur de propriété `Task.AssignedTo` est `null`.  
  
 Pour afficher le comportement de cet exemple, procédez comme suit :  
  
1.  Modifiez les assignations dans la colonne `Assigned To` en sélectionnant des valeurs différentes dans les listes déroulantes ou en appuyant sur CTRL\+0 dans une cellule de zone de liste déroulante.  
  
2.  Cliquez sur `Generate Report` pour afficher les assignations actuelles.  Cette procédure montre qu'une modification de la colonne `Assigned To` met à jour automatiquement la collection `tasks`.  
  
3.  Cliquez sur un bouton `Request Status` pour appeler la méthode `RequestStatus` de l'objet `Employee` actuel pour cette ligne.  Cette procédure montre que l'objet sélectionné a été récupéré avec succès.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System et System.Windows.Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ComboBox>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)