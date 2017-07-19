---
title: "Modes d&#39;affichage des donn&#233;es dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "données (Windows Forms), modes d'affichage"
  - "grilles de données, modes d'affichage"
  - "DataGridView (contrôle Windows Forms), modes d'affichage"
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Modes d&#39;affichage des donn&#233;es dans le contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> peut afficher des données en trois modes distincts : dépendant, indépendant et virtuel.  Choisissez le mode le plus approprié selon votre configuration requise.  
  
## Indépendant  
 Le mode indépendant convient pour afficher de petites quantités des données que vous gérez par programme.  Vous n'attachez pas directement le contrôle <xref:System.Windows.Forms.DataGridView> à une source de données comme en mode dépendant.  À la place, vous devez remplir le contrôle vous\-même, généralement en utilisant la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=fullName>.  
  
 Le mode indépendant peut être particulièrement utile pour les données statiques en lecture seule, ou lorsque vous souhaitez fournir votre code qui interagit avec un magasin de données externe.  Lorsque vous voulez que vos utilisateurs puissent interagir avec une source de données externe, toutefois, vous utiliserez en général le mode dépendant.  
  
 Pour obtenir un exemple qui utilise un <xref:System.Windows.Forms.DataGridView> indépendant en lecture seule, consultez [Comment : créer un contrôle DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## Dépendant  
 Le mode Dépendant convient pour gérer des données qui utilisent une interaction automatique avec le magasin de données.  Vous pouvez attacher directement le contrôle <xref:System.Windows.Forms.DataGridView> à sa source de données en définissant la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>.  Lorsque le contrôle est lié aux données, les lignes de données sont envoyées et extraites sans nécessiter une gestion explicite de votre part.  Lorsque la propriété <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> est `true`, chaque colonne dans votre source de données fera en sorte qu'une colonne correspondante soit créée dans le contrôle.  Si vous préférez créer vos propres colonnes, vous pouvez attribuer à cette propriété la valeur `false` et utiliser la propriété <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> pour lier chaque colonne lorsque vous le configurez.  C'est utile lorsque vous souhaitez utiliser un type de colonne autre que les types qui sont générés par défaut.  Pour plus d'informations, consultez [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).  
  
 Pour un obtenir exemple qui utilise un contrôle <xref:System.Windows.Forms.DataGridView> dépendant, consultez [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également ajouter des colonnes indépendantes à un contrôle <xref:System.Windows.Forms.DataGridView> en mode dépendant.  C'est utile lorsque vous souhaitez afficher une colonne de boutons ou de liens qui permettent aux utilisateurs d'exécuter des actions sur des lignes spécifiques.  Ceci est également utile pour afficher des colonnes avec des valeurs calculées provenant de colonnes dépendantes.  Vous pouvez remplir les valeurs de cellules pour les colonnes calculées dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting>.  Si, toutefois, vous utilisez un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> comme source de données, vous pouvez le cas échéant souhaiter utiliser la propriété <xref:System.Data.DataColumn.Expression%2A?displayProperty=fullName> pour créer à la place une colonne calculée.  Dans ce cas, le contrôle <xref:System.Windows.Forms.DataGridView> traitera juste la colonne calculée comme n'importe quelle autre colonne dans la source de données.  
  
 Le tri par colonnes indépendantes en mode dépendant n'est pas pris en charge.  Si vous créez, en mode dépendant, une colonne indépendante qui contient des valeurs utilisateur modifiables, vous devez implémenter le mode virtuel pour maintenir ces valeurs lorsque le contrôle est trié par une colonne dépendante.  
  
## Virtuel  
 Avec le mode virtuel, vous pouvez implémenter vos propres opérations de gestion de données.  Ceci est nécessaire pour maintenir les valeurs de colonnes indépendantes en mode dépendant lorsque le contrôle est trié par colonnes dépendantes.  Toutefois, l'utilisation principale du mode virtuel est d'optimiser la performance lors de l'interaction avec de grandes quantités de données.  
  
 Vous attachez le contrôle <xref:System.Windows.Forms.DataGridView> à un cache que vous gérez, et votre code contrôle quand les lignes de données sont envoyées et extraites.  Pour que l'encombrement mémoire reste réduit, le cache doit être similaire en taille au nombre de lignes affiché actuellement.  Lorsque l'utilisateur fait défiler de nouvelles lignes dans l'affichage, votre code demande de nouvelles données du cache et vide éventuellement les anciennes données de la mémoire.  
  
 Lorsque vous implémentez le mode virtuel, vous devrez déterminer quand une nouvelle ligne est exigée dans le modèle de données et quand annuler l'ajout de la nouvelle ligne.  L'implémentation exacte de ces fonctionnalités dépendra de l'implémentation du modèle de données et de la sémantique de transaction du modèle de données ; selon que la portée de validation se situe au niveau de la cellule ou de la ligne.  
  
 Pour plus d'informations sur le mode virtuel, consultez [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  Pour obtenir un exemple qui indique comment utiliser des événements de mode virtuel, consultez [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=fullName>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)   
 [Procédure pas à pas : création d'un contrôle DataGridView Windows Forms non lié](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)   
 [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)   
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)