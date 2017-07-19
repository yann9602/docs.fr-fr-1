---
title: "Utilisation de la ligne pour les nouveaux enregistrements dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "DataGridView (contrôle Windows Forms), ajouter des lignes pour les nouveaux enregistrements"
  - "DataGridView (contrôle Windows Forms), entrée de données"
  - "lignes, nouveaux enregistrements"
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Utilisation de la ligne pour les nouveaux enregistrements dans le contr&#244;le DataGridView Windows Forms
Lorsque vous utilisez un <xref:System.Windows.Forms.DataGridView> pour modifier des données dans votre application, vous souhaiterez souvent donner aux utilisateurs la possibilité d'ajouter des nouvelles lignes de données au magasin de données.  Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge ces fonctionnalités en fournissant une ligne de nouveaux enregistrements, qui sont toujours indiqués comme étant la dernière ligne.  Elle est marquée avec un symbole d'astérisque \(\*\) dans son en\-tête de ligne.  Les sections suivantes passent en revue quelques\-uns des aspects que vous devez prendre en considération lorsque vous programmez avec la ligne des nouveaux enregistrements activée.  
  
## Affichage de la ligne pour les nouveaux enregistrements  
 Utilisez la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> pour indiquer si la ligne des nouveaux enregistrements est affichée.  La valeur par défaut de cette propriété est `true`.  
  
 Pour le cas lié aux données, la ligne pour les nouveaux enregistrements sera indiquée si la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> du contrôle et la propriété <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=fullName> de la source de données ont toutes les deux la valeur `true`.  Si l'une ou l'autre a la valeur `false`, la ligne ne sera pas indiquée.  
  
## Remplissage de la ligne pour les nouveaux enregistrements avec des données par défaut  
 Lorsque l'utilisateur sélectionne la ligne pour les nouveaux enregistrements comme ligne actuelle, le contrôle <xref:System.Windows.Forms.DataGridView> déclenche l'événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
 Cet événement fournit l'accès au nouveau <xref:System.Windows.Forms.DataGridViewRow> et vous permet de remplir la nouvelle ligne avec les données par défaut.  Pour plus d'informations, consultez [Comment : spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## La collection Rows  
 La ligne pour les nouveaux enregistrements est contenue dans la collection <xref:System.Windows.Forms.DataGridView.Rows%2A> du contrôle <xref:System.Windows.Forms.DataGridView>, mais se comporte différemment à deux égards :  
  
-   La ligne pour les nouveaux enregistrements ne peut pas être supprimée par programme de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>.  Une <xref:System.InvalidOperationException> est levée si cette opération est tentée.  L'utilisateur ne peut pas non plus supprimer la ligne pour les nouveaux enregistrements.  La méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=fullName> ne supprime pas cette ligne de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>.  
  
-   Aucune ligne ne peut être ajoutée après la ligne pour les nouveaux enregistrements.  Une <xref:System.InvalidOperationException> est levée si cette opération est tentée.  En conséquence, la ligne pour les nouveaux enregistrements est toujours la dernière ligne dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Les méthodes de <xref:System.Windows.Forms.DataGridViewRowCollection> qui ajoute des lignes — <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A> et <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— appellent toutes les méthodes d'insertion en interne lorsque la ligne pour les nouveaux enregistrements est présente.  
  
## Personnalisation visuelle de la ligne pour les nouveaux enregistrements  
 Lorsque la ligne pour les nouveaux enregistrements est créée, elle repose sur la ligne spécifiée par la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.  Tous les styles de cellule qui ne sont pas spécifiés pour cette ligne sont hérités d'autres propriétés.  Pour plus d'informations sur l'héritage du style de cellule, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Les valeurs initiales affichées par les cellules dans la ligne pour les nouveaux enregistrements sont récupérées de la propriété <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> de chaque cellule.  Pour les cellules de type <xref:System.Windows.Forms.DataGridViewImageCell>, cette propriété retourne une image d'espace réservé.  Sinon, cette propriété retourne `null`.  Vous pouvez substituer cette propriété pour retourner une valeur personnalisée.  Toutefois, ces valeurs initiales peuvent être remplacées par un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> lorsque le focus se retrouve sur la ligne pour les nouveaux enregistrements.  
  
 Les icônes standard pour l'en\-tête de cette ligne, une flèche ou un astérisque, ne sont pas exposées publiquement.  Si vous souhaitez personnaliser les icônes, vous devrez créer une classe <xref:System.Windows.Forms.DataGridViewRowHeaderCell> personnalisée.  
  
 Les icônes standard utilisent la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> du <xref:System.Windows.Forms.DataGridViewCellStyle> utilisé par la cellule d'en\-tête de ligne.  Les icônes standard ne sont pas restituées s'il n'y a pas assez d'espace pour les afficher complètement.  
  
 Si la cellule d'en\-tête de ligne a un jeu de valeurs de chaînes, et s'il n'y a pas assez d'espace pour à la fois le texte et icône, l'icône est ignorée en premier.  
  
## Tri  
 En mode indépendant, les nouveaux enregistrements sont toujours ajoutés à la fin du <xref:System.Windows.Forms.DataGridView> même si l'utilisateur a trié le contenu du <xref:System.Windows.Forms.DataGridView>.  L'utilisateur doit appliquer encore le tri pour trier la ligne à la position correcte ; ce comportement est similaire à celui du contrôle <xref:System.Windows.Forms.ListView>.  
  
 En modes lié aux données et virtuel, le comportement d'insertion lorsqu'un tri est appliqué varie en fonction de l'implémentation du modèle de données.  Pour [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], la ligne est immédiatement placée à la bonne position.  
  
## D'autres remarques sur la ligne pour les nouveaux enregistrements  
 Vous ne pouvez pas attribuer à la propriété <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> de cette ligne la valeur `false`.  Une <xref:System.InvalidOperationException> est levée si cette opération est tentée.  
  
 La ligne pour les nouveaux enregistrements est toujours créée dans l'état désélectionné.  
  
## Mode virtuel  
 Si vous implémentez le mode virtuel, vous devrez assurer un suivi pour déterminer quand une ligne pour les nouveaux enregistrements est nécessaire dans le modèle de données et quand annuler l'ajout de la ligne.  L'implémentation exacte de ces fonctionnalités dépend de l'implémentation du modèle de données et de sa sémantique de transaction ; par exemple, selon que la portée de validation se situe au niveau de la cellule ou de la ligne.  Pour plus d'informations, consultez [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=fullName>   
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [Comment : spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)