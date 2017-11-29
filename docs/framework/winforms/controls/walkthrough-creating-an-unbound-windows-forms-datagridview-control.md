---
title: "Procédure pas à pas : création d'un contrôle DataGridView Windows Forms non lié"
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
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e2c57cfbab4d3af6cebff96517383999ae5b73d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>Procédure pas à pas : création d'un contrôle DataGridView Windows Forms non lié
Vous souhaiterez souvent affichent les données sous forme de tableau qui ne proviennent pas d’une base de données. Par exemple, vous souhaiterez afficher le contenu du tableau de chaînes à deux dimensions. La <xref:System.Windows.Forms.DataGridView> classe fournit un moyen simple et hautement personnalisable pour afficher les données sans liaison à une source de données. Cette procédure pas à pas montre comment remplir un <xref:System.Windows.Forms.DataGridView> contrôler et gérer l’ajout et la suppression de lignes en mode « indépendant ». Par défaut, l’utilisateur peut ajouter de nouvelles lignes. Pour empêcher l’ajout de ligne, définissez la <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriété est `false`.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un contrôle de DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Création du formulaire  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>Pour utiliser un contrôle DataGridView indépendant  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient les déclarations de variable suivantes et `Main` (méthode).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  Implémentez un `SetupLayout` méthode dans la définition de classe de votre formulaire pour configurer la disposition du formulaire.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  Créer un `SetupDataGridView` méthode pour configurer le <xref:System.Windows.Forms.DataGridView> colonnes et des propriétés.  
  
     Cette méthode ajoute d’abord le <xref:System.Windows.Forms.DataGridView> contrôle du formulaire <xref:System.Windows.Forms.Control.Controls%2A> collection. Ensuite, le nombre de colonnes à afficher est défini à l’aide de la <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> propriété. Le style par défaut pour les en-têtes de colonne est défini en définissant le <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, et <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> propriétés de la <xref:System.Windows.Forms.DataGridViewCellStyle> retournée par le <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> propriété.  
  
     Définir des propriétés de disposition et l’apparence et les noms de colonne sont ensuite affectés. Lorsque cette méthode se termine, la <xref:System.Windows.Forms.DataGridView> contrôle est prêt à être rempli.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  Créer un `PopulateDataGridView` méthode pour ajouter des lignes à la <xref:System.Windows.Forms.DataGridView> contrôle.  
  
     Chaque ligne représente une chanson et les informations associées.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  Avec les méthodes utilitaires en place, vous pouvez attacher des gestionnaires d’événements.  
  
     Vous allez gérer les **ajouter** et **supprimer** boutons <xref:System.Windows.Forms.Control.Click> événements, du formulaire <xref:System.Windows.Forms.Form.Load> événement et le <xref:System.Windows.Forms.DataGridView> du contrôle <xref:System.Windows.Forms.DataGridView.CellFormatting> événement.  
  
     Lorsque le **ajouter** du bouton <xref:System.Windows.Forms.Control.Click> événement est déclenché, une nouvelle ligne vide est ajoutée à la <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque le **supprimer** du bouton <xref:System.Windows.Forms.Control.Click> événement est déclenché, la ligne sélectionnée est supprimée, ajouter de nouvelles lignes, sauf si elle est la ligne pour les nouveaux enregistrements, ce qui permet à l’utilisateur. Cette ligne est toujours la dernière ligne dans le <xref:System.Windows.Forms.DataGridView> contrôle.  
  
     Lorsque du formulaire <xref:System.Windows.Forms.Form.Load> événement est déclenché, le `SetupLayout`, `SetupDataGridView`, et `PopulateDataGridView` utilitaire méthodes sont appelées.  
  
     Lorsque le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement est déclenché, chaque cellule de la `Date` colonne est mise en forme comme une longue date, sauf si la valeur de la cellule ne peut pas être analysée.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
     Vous verrez un <xref:System.Windows.Forms.DataGridView> contrôle qui affiche les chansons répertoriées dans `PopulateDataGridView`. Vous pouvez ajouter de nouvelles lignes avec le **ajouter une ligne** et vous pouvez supprimer des lignes sélectionnées avec la **supprimer la ligne** bouton. L’indépendant <xref:System.Windows.Forms.DataGridView> contrôle est le magasin de données et ses données sont indépendantes de toute source externe, comme un <xref:System.Data.DataSet> ou un tableau.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application vous donne une connaissance élémentaire de la <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle. Vous pouvez personnaliser l’apparence et le comportement de la <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs manières :  
  
-   Modifier les styles de bordure et en-tête. Pour plus d’informations, consultez [Comment : modifier la bordure et les Styles de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Activer ou restreindre l’entrée d’utilisateur à le <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations, consultez [Comment : empêcher l’ajout ligne et la suppression dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), et [Comment : rendre en lecture seule les colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Vérifiez l’entrée d’utilisateur pour les erreurs relatives à la base de données. Pour plus d’informations, consultez [procédure pas à pas : gestion des erreurs qui se produisent pendant la saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Gérer des jeux de données très volumineux à l’aide du mode virtuel. Pour plus d’informations, consultez [procédure pas à pas : implémentation du Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des Styles de cellule par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour créer un contrôle DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
