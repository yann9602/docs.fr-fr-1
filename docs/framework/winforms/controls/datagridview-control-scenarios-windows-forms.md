---
title: "Sc&#233;narios du contr&#244;le DataGridView (Windows Forms) | Microsoft Docs"
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
  - "données (Windows Forms), afficher sous forme de tableau"
  - "grilles de données, à propos des grilles de données"
  - "DataGridView (contrôle Windows Forms), scénarios"
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Sc&#233;narios du contr&#244;le DataGridView (Windows Forms)
Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez afficher les données sous forme de tableau à partir de diverses sources de données.  Pour les utilisations simples, vous pouvez remplir une <xref:System.Windows.Forms.DataGridView> manuellement et manipuler directement les données à travers le contrôle.  Vous stockerez toutefois généralement vos données dans une source de données externe à laquelle vous lierez le contrôle via un composant <xref:System.Windows.Forms.BindingSource>.  
  
 Cette rubrique décrit certains des scénarios courants qui impliquent le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## Scénario 1 : Affichage de petites quantités de données  
 Vous n'êtes pas obligé de stocker vos données dans une source de données externe pour les afficher dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Si vous travaillez avec une petite quantité de données, vous pouvez remplir le contrôle vous\-même et manipuler les données à travers le contrôle.  C'est ce qu'on appelle le *mode indépendant*.  Pour plus d'informations, consultez [Comment : créer un contrôle DataGridView Windows Forms indépendant](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### Points clés du scénario  
  
-   En mode indépendant, vous remplissez le contrôle manuellement.  
  
-   Le mode indépendant est particulièrement adapté aux petites quantités de données en lecture seule.  
  
-   Le mode indépendant est également adapté aux tables en forme de feuille de calcul ou faiblement remplies.  
  
## Scénario 2 : Affichage et mise à jour des données stockées dans une source de données externe  
 Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.DataGridView> comme une interface utilisateur à travers laquelle les utilisateurs peuvent accéder aux données conservées dans une source de données comme une table de base de données ou une collection d'objets métier.  Pour plus d'informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### Points clés du scénario  
  
-   Le mode dépendant vous permet de vous connecter à une source de données, de générer automatiquement des colonnes basées sur les propriétés de source de données ou les colonnes de base de données, et de remplir automatiquement le contrôle.  
  
-   Le mode dépendant est adapté à une interaction intensive de l'utilisateur avec les données.  Les données peuvent être mises en forme pour l'affichage, et les données spécifiées par l'utilisateur peuvent être analysées dans le format attendu par la source de données.  Les erreurs de format d'entrée des données et de contrainte de base de données peuvent être détectées pour que les utilisateurs soient avertis et les cellules erronées corrigées.  
  
-   Les fonctionnalités supplémentaires telles que le tri, la réorganisation et le fait de figer les colonnes permettent aux utilisateurs de consulter les données de la manière qui convient le mieux à leur flux de travail.  
  
-   La prise en charge du Presse\-papiers permet aux utilisateurs de copier les données de votre application dans d'autres applications.  
  
## Scénario 3 : Données avancées  
 Si vous avez des besoins spéciaux que le modèle de liaison de données standard ne permet pas de résoudre, vous pouvez gérer l'interaction entre le contrôle et vos données en implémentant le *mode virtuel*.  L'implémentation du mode virtuel correspond à l'implémentation d'un ou de plusieurs gestionnaires d'événements permettant au contrôle d'obtenir des informations sur les cellules à mesure qu'il en a besoin.  
  
 Par exemple, si vous travaillez avec de grandes quantités de données, implémenter le mode virtuel peut vous permettre de disposer d'un niveau d'efficacité optimal.  Le mode virtuel est également utile pour maintenir les valeurs de colonnes indépendantes que vous affichez conjointement à des colonnes extraites d'une autre source de données.  
  
 Pour plus d'informations sur le mode virtuel, consultez [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
### Points clés du scénario  
  
-   Le mode virtuel est adapté à l'affichage de très grandes quantités de données lorsque vous devez ajuster la performance avec précision.  
  
## Scénario 4 : Redimensionnement automatique des lignes et des colonnes  
 Lorsque vous affichez des données qui sont régulièrement mises à jour, vous pouvez automatiquement redimensionner des lignes et des colonnes pour veiller à ce que la totalité du contenu soit visible.  Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs options qui vous permettent d'activer ou de désactiver le redimensionnement manuel, de redimensionner par programme à des moments spécifiques ou de redimensionner automatiquement chaque fois que le contenu change.  Pour plus d'informations, consultez [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### Points clés du scénario  
  
-   Le redimensionnement manuel permet aux utilisateurs de régler la hauteur et la largeur des cellules.  
  
-   Le redimensionnement automatique vous permet de conserver les tailles de cellule de sorte que le contenu de la cellule ne soit jamais tronqué.  
  
-   Le redimensionnement par programmation vous permet de redimensionner des cellules à des moments spécifiques afin d'éviter l'impact sur les performances d'un redimensionnement automatique permanent.  
  
## Scénario 5 : Personnalisation simple  
 Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de modifier son apparence et son comportement de base de nombreuses manières.  Pour plus d'informations, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### Points clés du scénario  
  
-   Les objets <xref:System.Windows.Forms.DataGridViewCellStyle> vous permettent de fournir des informations de couleur, de police, de mise en forme et de positionnement à plusieurs niveaux et pour les éléments individuels du contrôle.  
  
-   Les styles de cellule peuvent être superposés en couches et partagés par plusieurs éléments, vous permettant de réutiliser le code.  
  
## Scénario 6 : Personnalisation avancée  
 Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de personnaliser son apparence et son comportement de nombreuses manières.  
  
### Points clés du scénario  
  
-   Vous pouvez fournir votre propre code de peinture de cellule.  Pour plus d'informations, consultez [Comment : personnaliser l'apparence des cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Vous pouvez fournir votre propre peinture de ligne.  Cela est pratique, par exemple, pour créer des lignes dont le contenu couvre plusieurs colonnes.  Pour plus d'informations, consultez [Comment : personnaliser l'apparence des lignes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Vous pouvez implémenter vos propres classes de cellule et de colonne pour personnaliser l'apparence des cellules.  Pour plus d'informations, consultez [Comment : personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Vous pouvez implémenter vos propres classes de cellule et de colonne pour héberger des contrôles autres que ceux qui sont fournis par les types de colonne intégrés.  Pour plus d'informations, consultez [Comment : héberger des contrôles dans des cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Vue d'ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)