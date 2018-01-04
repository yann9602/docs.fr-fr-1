---
title: "Comment : accéder à des objets dans une liste déroulante DataGridViewComboBoxCell Windows Forms"
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
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d0f4eb14fbb459f6844053507d1eb4f0a46cede3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Comment : accéder à des objets dans une liste déroulante DataGridViewComboBoxCell Windows Forms
Comme le <xref:System.Windows.Forms.ComboBox> (contrôle), le <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et <xref:System.Windows.Forms.DataGridViewComboBoxCell> types permettent d’ajouter des objets arbitraires à leurs listes déroulantes. Avec cette fonctionnalité, vous pouvez représenter des États complexes dans une liste déroulante sans devoir stocker des objets correspondants dans une collection distincte.  
  
 Contrairement à la <xref:System.Windows.Forms.ComboBox> (contrôle), le <xref:System.Windows.Forms.DataGridView> types n’ont pas un <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> propriété pour récupérer l’objet actuellement sélectionné. Au lieu de cela, vous devez définir le <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> nom à la propriété d’une propriété de votre objet métier. Lorsque l’utilisateur effectue une sélection, la propriété indiquée de l’objet métier définit la cellule <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriété.  
  
 Pour récupérer l’objet métier à la valeur de cellule, le `ValueMember` propriété doit indiquer une propriété qui retourne une référence à l’objet métier lui-même. Par conséquent, si le type de l’objet métier n’est pas sous votre contrôle, vous devez ajouter une telle propriété en étendant le type via l’héritage.  
  
 Les procédures suivantes montrent comment remplir une liste déroulante avec des objets métier et récupérer les objets dans la cellule <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriété.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Pour ajouter des objets métier à la liste déroulante  
  
1.  Créer un nouveau <xref:System.Windows.Forms.DataGridViewComboBoxColumn> et remplir ses <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection. Vous pouvez également définir la colonne <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> propriété à la collection d’objets métier. Dans ce cas, toutefois, vous ne pouvez pas ajouter « non attribués » à la liste déroulante sans créer d’objet métier correspondant dans votre collection de.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Définissez les propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>Indique la propriété de l’objet métier à afficher dans la liste déroulante. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>Indique la propriété qui retourne une référence à l’objet métier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  Assurez-vous que votre type d’objet métier contient une propriété qui retourne une référence à l’instance actuelle. Cette propriété doit être nommée avec la valeur affectée à <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> à l’étape précédente.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Pour récupérer l’objet métier actuellement sélectionné  
  
-   Obtenir la cellule <xref:System.Windows.Forms.DataGridViewCell.Value%2A> propriété et un cast vers le type d’objet métier.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Exemple  
 L’exemple complet illustre l’utilisation d’objets métier dans une liste déroulante. Dans l’exemple, un <xref:System.Windows.Forms.DataGridView> contrôle est lié à une collection de `Task` objets. Chaque `Task` objet a un `AssignedTo` propriété qui indique le `Employee` objet actuellement affecté à cette tâche. Le `Assigned To` colonne affiche la `Name` valeur de propriété pour chaque employé assigné, ou « non assigné » si le `Task.AssignedTo` valeur de propriété est `null`.  
  
 Pour afficher le comportement de cet exemple, procédez comme suit :  
  
1.  Modifier les affectations dans la `Assigned To` colonne en sélectionnant des valeurs différentes dans les listes déroulantes ou en appuyant sur CTRL + 0 dans une cellule de la zone de liste déroulante.  
  
2.  Cliquez sur `Generate Report` pour afficher les assignations actuelles. Cette procédure montre qu’une modification dans le `Assigned To` colonne met automatiquement à jour le `tasks` collection.  
  
3.  Cliquez sur un `Request Status` bouton pour appeler le `RequestStatus` méthode actuelles `Employee` objet pour cette ligne. Cela montre que l’objet sélectionné a été récupéré avec succès.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms ;  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
