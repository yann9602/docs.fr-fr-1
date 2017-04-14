---
title: "Comment&#160;: impl&#233;menter la validation avec le contr&#244;le DataGrid | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataGrid (WPF), validation"
  - "validation (WPF), DataGrid"
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: impl&#233;menter la validation avec le contr&#244;le DataGrid
Le contrôle <xref:System.Windows.Controls.DataGrid> vous permet d'exécuter à la fois la validation au niveau de la cellule et au niveau de la ligne.  La validation au niveau de la cellule vous permet de valider les propriétés d'un objet de données lié lorsqu'un utilisateur met à jour une valeur.  La validation au niveau de la ligne vous permet de valider des objets de données entiers lorsqu'un utilisateur valide des modifications apportées à une ligne.  Vous pouvez également fournir une rétroaction visuelle personnalisée pour les erreurs de validation ou utiliser la rétroaction visuelle par défaut fournie par le contrôle <xref:System.Windows.Controls.DataGrid>.  
  
 Les procédures suivantes expliquent comment appliquer des règles de validation aux liaisons <xref:System.Windows.Controls.DataGrid> et personnaliser la rétroaction visuelle.  
  
### Pour valider des valeurs de cellules  
  
-   Spécifiez une ou plusieurs règles de validation sur la liaison utilisée avec une colonne.  Cette opération est semblable à la validation de données dans des contrôles simples, comme décrit dans [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
     L'exemple suivant montre un contrôle <xref:System.Windows.Controls.DataGrid> avec quatre colonnes liées à différentes propriétés d'un objet métier.  Trois de ces colonnes spécifient le <xref:System.Windows.Controls.ExceptionValidationRule> en affectant à la propriété <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> la valeur `true`.  
  
     [!code-xml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Lorsqu'un utilisateur entre une valeur non valide \(telle qu'un non entier dans la colonne ID cours\), la cellule est bordée de rouge.  Vous pouvez modifier ces commentaires de validation par défaut comme décrit dans la procédure suivante.  
  
### Pour personnaliser les commentaires de validation de la cellule  
  
-   Affectez à la propriété <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> de la colonne un style approprié pour le contrôle d'édition de la colonne.  Étant donné que les contrôles d'édition sont créés au moment de l'exécution, vous ne pouvez pas utiliser la propriété jointe <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=fullName> comme vous le feriez avec les contrôles simples.  
  
     L'exemple suivant met à jour l'exemple précédent en ajoutant un style d'erreur partagé par les trois colonnes avec les règles de validation.  Lorsqu'un utilisateur entre une valeur non valide, le style modifie la couleur d'arrière\-plan de cellule et ajoute une info\-bulle.  Notez l'utilisation d'un déclencheur pour déterminer s'il y a une erreur de validation.  Ceci est obligatoire car il n'existe actuellement aucun modèle d'erreur dédié pour les cellules.  
  
     [!code-xml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Vous pouvez implémenter une personnalisation plus étendue en remplaçant le <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> utilisé par la colonne.  
  
### Pour valider plusieurs valeurs d'une ligne unique  
  
1.  Implémentez une sous\-classe <xref:System.Windows.Controls.ValidationRule> qui vérifie plusieurs propriétés de l'objet de données lié.  Dans l'implémentation de la méthode <xref:System.Windows.Controls.ValidationRule.Validate%2A>, effectuez un cast de la valeur du paramètre `value` en une instance <xref:System.Windows.Data.BindingGroup>.  Vous pouvez alors accéder à l'objet de données via la propriété <xref:System.Windows.Data.BindingGroup.Items%2A>.  
  
     L'exemple suivant montre le processus permettant de valider si la valeur de la propriété `StartDate` d'un objet `Course` est antérieure à sa valeur de propriété `EndDate`.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Ajoutez une règle de validation à la collection <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=fullName>.  La propriété <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> fournit un accès direct à la propriété <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> d'une instance <xref:System.Windows.Data.BindingGroup> qui groupe toutes les liaisons utilisée par le contrôle.  
  
     L'exemple de code suivant définit la propriété <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> en XAML.  La propriété <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a la valeur <xref:System.Windows.Controls.ValidationStep> afin que la validation se produise uniquement après la mise à jour de l'objet de données lié.  
  
     [!code-xml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Lorsqu'un utilisateur spécifie une date de fin antérieure à la date de début, un point d'exclamation rouge \(\!\) apparaît dans l'en\-tête de la ligne.  Vous pouvez modifier ces commentaires de validation par défaut comme décrit dans la procédure suivante.  
  
### Pour personnaliser les commentaires de validation de ligne  
  
-   Définissez la propriété <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=fullName>.  Cette propriété vous permet de personnaliser les commentaires de validation de ligne pour les contrôles <xref:System.Windows.Controls.DataGrid>.  Vous pouvez également affecter plusieurs contrôles en utilisant un style de ligne implicite pour définir la propriété <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=fullName>.  
  
     L'exemple suivant remplace les commentaires de validation de ligne par défaut par un indicateur plus visible.  Lorsqu'un utilisateur entre une valeur non valide, un cercle rouge avec un point d'exclamation blanc s'affiche dans l'en\-tête de la ligne.  Cela se produit pour les erreurs de validation de ligne et de cellule.  Le message d'erreur associé s'affiche dans une info\-bulle.  
  
     [!code-xml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## Exemple  
 L'exemple suivant fournit une démonstration complète de la validation de cellule et de ligne.  La classe `Course` fournit un exemple d'objet de données qui implémente <xref:System.ComponentModel.IEditableObject> pour prendre en charge les transactions.  Le contrôle <xref:System.Windows.Controls.DataGrid> interagit avec <xref:System.ComponentModel.IEditableObject> pour permettre aux utilisateurs de rétablir des modifications en appuyant sur Échap.  
  
> [!NOTE]
>  Si vous utilisez Visual Basic, dans la première ligne de MainWindow.xaml, remplacez `x:Class="DataGridValidation.MainWindow"` par `x:Class="MainWindow"`.  
  
 Pour tester la validation, essayez ce qui suit :  
  
-   Dans la colonne ID cours, entrez une valeur non entière.  
  
-   Dans la colonne Date de fin, entrez une date antérieure à la date de début.  
  
-   Supprimez la valeur dans ID cours, Date de début ou Date de fin.  
  
-   Pour annuler une valeur de cellule non valide, remettez le curseur dans la cellule et appuyez sur la touche Échap.  
  
-   Pour annuler les modifications d'une ligne entière lorsque la cellule active est en mode Édition, appuyez sur la touche Échap deux fois.  
  
-   Lorsqu'une erreur de validation se produit, déplacez le pointeur de votre souris sur l'indicateur dans l'en\-tête de ligne pour lire le message d'erreur associé.  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.DataGrid>   
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)   
 [Liaison de données](../../../../docs/framework/wpf/data/data-binding-wpf.md)   
 [Implémenter la validation de la liaison](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [Implémenter une logique de validation sur des objets personnalisés](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)