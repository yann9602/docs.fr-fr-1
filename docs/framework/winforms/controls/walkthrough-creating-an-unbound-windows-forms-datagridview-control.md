---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le DataGridView Windows Forms non li&#233; | Microsoft Docs"
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
  - "données (Windows Forms), afficher sans lier à une source de données"
  - "données (Windows Forms), sans liaison"
  - "DataGridView (contrôle Windows Forms), afficher les données sans liaison à une source de données"
  - "DataGridView (contrôle Windows Forms), données indépendantes"
  - "procédures pas à pas (Windows Forms), DataGridView (contrôle)"
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un contr&#244;le DataGridView Windows Forms non li&#233;
Il peut vous arriver fréquemment de souhaiter afficher des données sous forme de tableau qui ne proviennent pas d'une base de données.  Par exemple, vous pouvez souhaiter afficher le contenu d'un tableau de chaînes à deux dimensions.  La classe <xref:System.Windows.Forms.DataGridView> fournit un moyen facile et très personnalisable d'afficher des données sans créer de liaison à une source de données.  Cette procédure pas à pas indique comment remplir un contrôle <xref:System.Windows.Forms.DataGridView> et gérer l'ajout et la suppression de lignes en mode "indépendant".  Par défaut, l'utilisateur peut ajouter de nouvelles lignes.  Pour empêcher l'ajout de ligne, donnez à la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> la valeur `false`.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un contrôle DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## Création du formulaire  
  
#### Pour utiliser un contrôle DataGridView indépendant  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient les déclarations de variable suivantes et la méthode `Main`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  Implémentez une méthode `SetupLayout` dans la définition de classe de votre formulaire pour configurer la disposition du formulaire.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  Créez une méthode `SetupDataGridView` pour configurer les colonnes et les propriétés de <xref:System.Windows.Forms.DataGridView>.  
  
     Cette méthode ajoute d'abord le contrôle <xref:System.Windows.Forms.DataGridView> à la collection <xref:System.Windows.Forms.Control.Controls%2A> du formulaire.  Ensuite, le nombre de colonnes à afficher est défini à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.ColumnCount%2A>.  Le style par défaut des en\-têtes de colonnes est défini à l'aide des propriétés <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> et <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> du <xref:System.Windows.Forms.DataGridViewCellStyle> retourné par la propriété <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>.  
  
     Les propriétés de disposition et d'apparence sont définies, puis les noms de colonnes sont assignés.  Lorsque cette méthode a terminé son exécution, le contrôle <xref:System.Windows.Forms.DataGridView> est prêt à être rempli.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  Créez une méthode `PopulateDataGridView` pour ajouter des lignes au contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Chaque ligne représente une chanson et les informations qui lui sont associées.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  Avec les méthodes utilitaires en place, vous pouvez joindre des gestionnaires d'événements.  
  
     Vous gérerez les événements <xref:System.Windows.Forms.Control.Click> des boutons **Ajouter** et **Supprimer**, l'événement <xref:System.Windows.Forms.Form.Load> du formulaire et l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque l'événement <xref:System.Windows.Forms.Control.Click> du bouton **Ajouter** est déclenché, une nouvelle ligne vide est ajoutée à <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque l'événement <xref:System.Windows.Forms.Control.Click> du bouton **Supprimer** est déclenché, la ligne sélectionnée est supprimée, sauf s'il s'agit de la ligne prévue pour les nouveaux enregistrements, qui permet à l'utilisateur d'ajouter de nouvelles lignes.  Cette ligne est toujours la dernière dans le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Lorsque l'événement <xref:System.Windows.Forms.Form.Load> du formulaire est déclenché, les méthodes utilitaires `SetupLayout`, `SetupDataGridView` et `PopulateDataGridView` sont appelées.  
  
     Lorsque l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting> est déclenché, chaque cellule de la colonne `Date` est mise en forme comme une longue date, sauf si la valeur de la cellule ne peut pas être analysée.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## Test de l'application  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
     Vous verrez un contrôle <xref:System.Windows.Forms.DataGridView> qui affiche les chansons répertoriées dans `PopulateDataGridView`.  Vous pouvez ajouter de nouvelles lignes avec le bouton **Ajouter une ligne**, et supprimer les lignes sélectionnées à l'aide du bouton **Supprimer la ligne**.  Le contrôle <xref:System.Windows.Forms.DataGridView> indépendant est le magasin de données, et ses données sont indépendantes de toute source externe, telle qu'un <xref:System.Data.DataSet> ou un tableau.  
  
## Étapes suivantes  
 Cette application vous donne une présentation basique des capacités du contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez personnaliser l'apparence et le comportement du contrôle <xref:System.Windows.Forms.DataGridView> de plusieurs manières :  
  
-   Changez les styles de bordure et d'en\-tête.  Pour plus d'informations, consultez [Comment : modifier les styles de bordures et de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Activez ou restreignez les entrées d'utilisateur au contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations, consultez [Comment : empêcher l'ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md) et [Comment : définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Recherchez dans les entrées d'utilisateur les erreurs relatives à la base de données.  Pour plus d'informations, consultez [Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Gérez de très grandes quantités de données à l'aide du mode virtuel.  Pour plus d'informations, consultez [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Personnalisez l'apparence des cellules.  Pour plus d'informations, consultez [Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : créer un contrôle DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)   
 [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)