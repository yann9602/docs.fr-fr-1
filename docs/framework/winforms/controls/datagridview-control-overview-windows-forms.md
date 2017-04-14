---
title: "Vue d&#39;ensemble du contr&#244;le DataGridView (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataGridView"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles dépendants, DataGridView (contrôle)"
  - "colonnes (Windows Forms), DataGridView (contrôle)"
  - "données (Windows Forms), naviguer"
  - "données (Windows Forms), retrier"
  - "liaison de données, DataGridView (contrôle)"
  - "grilles de données, à propos des grilles de données"
  - "sources de données, lier au contrôle DataGridView"
  - "DataGridView (contrôle Windows Forms), à propos du contrôle DataGridView"
  - "DataGridView (contrôle Windows Forms), liaison de données"
  - "groupes de données (Windows Forms), lier au contrôle DataGridView"
  - "contrôles de grille (Windows Forms)"
  - "grilles (Windows Forms)"
  - "tables (Windows Forms), lier au contrôle DataGridView"
  - "tables (Windows Forms), afficher dans le contrôle DataGridView"
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Vue d&#39;ensemble du contr&#244;le DataGridView (Windows Forms)
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet d'afficher et de modifier les données sous forme de tableau provenant de nombreux types de sources de données différents.  
  
 Lier des données au contrôle <xref:System.Windows.Forms.DataGridView> est simple et intuitif et, dans de nombreux cas, aussi simple que de définir la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>.  Lorsque vous créez une liaison avec une source de données qui contient plusieurs listes ou tables, définissez la propriété <xref:System.Windows.Forms.DataGridView.DataMember%2A> à une chaîne à qui spécifie la liste ou la table avec laquelle créer la liaison.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge le modèle de liaison de données Windows Forms standard, et se liera donc aux instances des classes décrites dans la liste suivante :  
  
-   Toute classe qui implémente l'interface <xref:System.Collections.IList>, y compris les tableaux unidimensionnels.  
  
-   Toute classe qui implémente l'interface <xref:System.ComponentModel.IListSource>, telles que les classes <xref:System.Data.DataTable> et <xref:System.Data.DataSet>.  
  
-   Toute classe qui implémente l'interface <xref:System.ComponentModel.IBindingList>, telle que la classe <xref:System.ComponentModel.BindingList%601>.  
  
-   Toute classe qui implémente l'interface <xref:System.ComponentModel.IBindingListView>, telle que la classe <xref:System.Windows.Forms.BindingSource>.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge la liaison de données aux propriétés publiques des objets retournés par ces interfaces ou à la collection de propriétés retournée par une interface <xref:System.ComponentModel.ICustomTypeDescriptor>, si elle est implémentée sur les objets retournés.  
  
 En général, vous créez une liaison avec un composant <xref:System.Windows.Forms.BindingSource> et liez le composant <xref:System.Windows.Forms.BindingSource> à une autre source de données ou le remplissez avec des objets métier.  Le composant <xref:System.Windows.Forms.BindingSource> est la source de données par défaut car il peut se lier à une vaste gamme de sources de données et peut résoudre automatiquement de nombreux problèmes de liaison de données.  Pour plus d'informations, consultez [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> peut être également utilisé en mode *indépendant*, sans magasin de données sous\-jacent.  Pour obtenir un exemple de code qui utilise un contrôle <xref:System.Windows.Forms.DataGridView> indépendant, consultez [Procédure pas à pas : création d'un contrôle DataGridView Windows Forms non lié](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> est hautement configurable et extensible, et fournit un nombre élevé de propriétés, de méthodes et d'événements permettant de personnaliser son aspect et son comportement.  Si vous souhaitez que votre application Windows Forms affiche des données sous forme de tableau, envisagez d'utiliser le contrôle <xref:System.Windows.Forms.DataGridView> avant d'autres \(par exemple, <xref:System.Windows.Forms.DataGrid>\).  Si vous affichez une petite grille de valeurs en lecture seule, ou si vous permettez à un utilisateur de modifier une table contenant des millions d'enregistrements, le contrôle <xref:System.Windows.Forms.DataGridView> vous fournira une solution économe en mémoire facilement programmable.  
  
## Dans cette section  
 [Résumé de la technologie du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 Résume les concepts du contrôle <xref:System.Windows.Forms.DataGridView> et l'utilisation des classes connexes.  
  
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 Décrit l'architecture du contrôle <xref:System.Windows.Forms.DataGridView>, en expliquant sa hiérarchie de types et sa structure d'héritage.  
  
 [Scénarios du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 Décrit les scénarios d'utilisation les plus courants des contrôles <xref:System.Windows.Forms.DataGridView>.  
  
 [Répertoire de code du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 Fournit des liens vers des exemples de code dans la documentation pour différentes tâches <xref:System.Windows.Forms.DataGridView>.  Ces exemples sont catégorisés par type de tâche.  
  
## Rubriques connexes  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Décrit les types de colonne dans le contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms utilisé pour afficher les informations et permettre aux utilisateurs de modifier ou d'ajouter des informations.  
  
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment remplir le contrôle avec des données, manuellement ou à partir d'une source de données externe.  
  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent la peinture personnalisée de cellules et de lignes <xref:System.Windows.Forms.DataGridView>, ainsi que la création de types de cellule, colonne et ligne dérivés.  
  
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment utiliser efficacement le contrôle pour éviter des problèmes de performance lorsque vous travaillez avec de grandes quantités de données.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Fonctionnalités par défaut du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)   
 [Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)