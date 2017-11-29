---
title: "Attributs dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 21f39aa1f85e06f1967d278e07731b73dcf7cb10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-in-windows-forms-controls"></a>Attributs dans les contrôles Windows Forms
.NET Framework fournit divers attributs que vous pouvez appliquer aux membres de vos composants et contrôles personnalisés. Certains de ces attributs affectent le comportement d’exécution d’une classe, et d’autres affectent le comportement au moment de la conception.  
  
## <a name="attributes-for-control-and-component-properties"></a>Attributs pour les propriétés de composant et de contrôle  
 Le tableau suivant décrit les attributs que vous pouvez appliquer aux propriétés ou aux autres membres de vos composants et contrôles personnalisés. Pour obtenir un exemple d’utilisation de ces attributs, consultez [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Attribut|Description|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Spécifie la valeur à passer à une propriété pour que celle-ci obtienne sa valeur à partir d’une autre source. On appelle cela *l’ambiance*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Spécifie si une propriété ou un événement doit être affiché dans une fenêtre **Propriétés**.|  
|<xref:System.ComponentModel.CategoryAttribute>|Spécifie le nom de la catégorie dans laquelle grouper la propriété ou l’événement lorsque affichés dans un <xref:System.Windows.Forms.PropertyGrid> contrôle <xref:System.Windows.Forms.PropertySort.Categorized> mode.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Spécifie la valeur par défaut d'une propriété.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Spécifie une description pour une propriété ou un événement.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Spécifie le nom d’affichage complet pour une propriété, un événement, ou une méthode `public``void` qui n’accepte aucun argument.|  
|<xref:System.ComponentModel.EditorAttribute>|Spécifie l’éditeur à utiliser pour modifier une propriété.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Spécifie qu'une propriété ou une méthode peut s'afficher dans un éditeur.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Spécifie le mot-clé de contexte pour une classe ou un membre.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Spécifie si une propriété doit être localisée.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Indique que la représentation sous forme de texte d’un objet est masquée par des caractères tels que des astérisques.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Spécifie si la propriété de cet attribut est liée est en lecture seule ou lecture/écriture au moment de la conception.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Indique que la grille de propriétés doit s’actualiser lorsque la valeur de propriété associée change.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Spécifie le type à utiliser comme convertisseur de l'objet auquel cet attribut est lié.|  
  
## <a name="attributes-for-data-binding-properties"></a>Attributs pour les propriétés de liaison de données  
 Le tableau suivant montre les attributs que vous pouvez appliquer pour spécifier la façon dont vos composants et contrôles personnalisés interagissent avec la liaison de données.  
  
|Attribut|Description|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Spécifie si une propriété est généralement utilisée pour la liaison.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Spécifie la source de données et les propriétés de membre de données pour un composant.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Spécifie la propriété de liaison par défaut pour un composant.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Spécifie la source de données et les propriétés de membre de données pour un composant.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Active la redirection d’attribut.|  
  
## <a name="attributes-for-classes"></a>Attributs pour les classes  
 Le tableau suivant montre les attributs que vous pouvez appliquer pour spécifier le comportement de vos composants et contrôles personnalisés au moment de la conception.  
  
|Attribut|Description|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Spécifie l’événement par défaut d’un composant.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Spécifie la propriété par défaut d’un composant.|  
|<xref:System.ComponentModel.DesignerAttribute>|Spécifie la classe utilisée pour implémenter des services au moment de la conception pour un composant.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Spécifie que le concepteur pour une classe appartient à une certaine catégorie.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Représente un attribut d’un élément de boîte à outils.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Spécifie la chaîne de filtrage et le type de filtre à utiliser pour un élément de boîte à outils.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Attribute>  
 [Guide pratique pour appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
