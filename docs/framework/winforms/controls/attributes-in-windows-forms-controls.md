---
title: "Attributs dans les contr&#244;les Windows Forms | Microsoft Docs"
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
  - "attributs (Windows Forms)"
  - "attributs (Windows Forms), classes"
  - "attributs (Windows Forms), propriétés des contrôles"
  - "attributs (Windows Forms), propriétés de la liaison de données"
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Attributs dans les contr&#244;les Windows Forms
Le .NET Framework fournit divers attributs que vous pouvez appliquer aux membres de vos composants et contrôles personnalisés.  Quelques\-uns de ces attributs affectent le comportement à l'exécution d'une classe, et d'autres affectent le comportement au moment du design.  
  
## Attributs pour les propriétés des contrôles et composants  
 Le tableau suivant affiche les attributs que vous pouvez appliquer à des propriétés ou à d'autres membres de vos composants et contrôles personnalisés.  Pour obtenir un exemple d'utilisation de ces attributs, consultez [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Attribut|Description|  
|--------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Spécifie la valeur à passer à une propriété pour que celle\-ci obtienne obtenir sa valeur d'une autre source.  Ce concept est appelé *ambiance*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Spécifie si une propriété ou un événement doivent être affichés dans une fenêtre **Propriétés**.|  
|<xref:System.ComponentModel.CategoryAttribute>|Spécifie le nom de la catégorie dans laquelle regrouper la propriété ou l'événement lors de son affichage dans un jeu de contrôles <xref:System.Windows.Forms.PropertyGrid> défini selon le mode <xref:System.Windows.Forms.PropertySort>.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Spécifie la valeur par défaut d'une propriété.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Spécifie une description pour une propriété ou un événement.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Spécifie le nom complet d'une propriété, d'un événement ou d'une méthode  `public` `void` qui ne prend pas d'arguments.|  
|<xref:System.ComponentModel.EditorAttribute>|Spécifie l'éditeur à utiliser pour modifier une propriété.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Spécifie qu'une propriété ou méthode est affichable dans un éditeur.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Spécifie le mot clé de contexte pour une classe ou un membre.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Spécifie qu'une propriété doit être localisée.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Indique que la représentation textuelle d'un objet est masquée par des caractères tels que les astérisques.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Spécifie si la propriété à laquelle cet attribut est lié est en lecture seule ou en lecture\/écriture au moment du design.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Indique que la grille de propriété doit s'actualiser lorsque la valeur de propriété associée change.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Spécifie quel type utiliser comme convertisseur pour l'objet auquel cet attribut est lié.|  
  
## Attributs pour les propriétés de la liaison de données  
 Le tableau suivant affiche les attributs que vous pouvez appliquer pour spécifier comment vos composants et contrôles personnalisés doivent interagir avec la liaison de données.  
  
|Attribut|Description|  
|--------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Spécifie si une propriété est généralement utilisée pour la liaison.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Spécifie la source de données et les propriétés de donnée membre pour un composant.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Spécifie la propriété de liaison par défaut pour un composant.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Spécifie la source de données et les propriétés de donnée membre pour un composant.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Active la redirection d'attribut.|  
  
## Attributs pour les classes  
 Le tableau suivant affiche les attributs que vous pouvez appliquer pour spécifier le comportement de vos composants et contrôles personnalisés au moment du design.  
  
|Attribut|Description|  
|--------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Spécifie l'événement par défaut pour un composant.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Spécifie la propriété par défaut pour un composant.|  
|<xref:System.ComponentModel.DesignerAttribute>|Spécifie la classe utilisée pour implémenter des services au moment du design pour un composant.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Spécifie que le concepteur pour une classe appartient à une certaine catégorie.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Représente un attribut d'un élément de boîte à outils.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Spécifie la chaîne de filtrage et le type de filtre à utiliser pour un élément de la boîte à outils.|  
  
## Voir aussi  
 <xref:System.Attribute>   
 [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)