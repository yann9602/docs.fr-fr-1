---
title: "Liaison de donn&#233;es Windows Forms | Microsoft Docs"
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
  - "contrôles dépendants, Windows Forms"
  - "données (Windows Forms)"
  - "données (Windows Forms), architecture"
  - "Contrôles Windows Forms, liaison de données"
  - "Windows Forms, liaison de données"
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Liaison de donn&#233;es Windows Forms
La liaison de données dans les Windows Forms vous permet d'afficher et de modifier les informations d'une source de données dans les contrôles du formulaire.  Vous pouvez établir une liaison à une source de données traditionnelle et à presque toute structure qui contient des données.  
  
## Dans cette section  
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 Fournit une vue d'ensemble de la liaison de données dans les Windows Forms.  
  
 [Sources de données prises en charge par les Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 Décrit les sources de données qui peuvent être utilisées avec Windows Forms.  
  
 [Interfaces participant à la liaison de données](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 Décrit plusieurs interfaces utilisées avec la liaison de données Windows Forms.  
  
 [Comment : naviguer au sein des données dans les Windows Forms](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 Montre comment parcourir les éléments dans une source de données.  
  
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 Décrit les différents types de notifications de modifications pour la liaison de données Windows Forms.  
  
 [Comment : implémenter l'interface INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 Montre comment implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  L'interface communique à un contrôle dépendant les modifications apportées aux propriétés d'un objet métier.  
  
 [Comment : appliquer le modèle PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 Montre comment appliquer le modèle *PropertyNameChanged* aux propriétés d'un contrôle utilisateur Windows Forms.  
  
 [Comment : implémenter l'interface ITypedList](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 Montre comment activer la découverte du schéma pour une liste pouvant être liée en implémentant l'interface <xref:System.ComponentModel.ITypedList>.  
  
 [Comment : implémenter l'interface IListSource](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 Montre comment implémenter l'interface <xref:System.ComponentModel.IListSource> pour créer une classe pouvant être liée qui n'implémente pas <xref:System.Collections.IList> mais fournit une liste à partir d'un autre emplacement.  
  
 [Comment : s'assurer que plusieurs contrôles liés à la même source de données restent synchronisés](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 Montre comment gérer l'événement <xref:System.Windows.Forms.BindingSource.BindingComplete> pour garantir que tous les contrôles liés à une source de données restent synchronisés.  
  
 [Comment : s'assurer que la ligne sélectionnée dans une table enfant reste au bon emplacement](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 Montre comment s'assurer que la ligne sélectionnée dans une table enfant ne change pas quand une modification est apportée à un champ de la table parente.  
  
 Consultez également [Interfaces participant à la liaison de données](http://msdn.microsoft.com/library/41e17s4b%20\(v=vs.110\)), [Comment : naviguer au sein des données dans les Windows Forms](http://msdn.microsoft.com/library/b63ha24w%20\(v=vs.110\)), [Comment : créer un contrôle à liaison simple dans un Windows Form](http://msdn.microsoft.com/library/sw223a62%20\(v=vs.110\)).  
  
## Référence  
 <xref:System.Windows.Forms.Binding?displayProperty=fullName>  
 Décrit la classe qui représente la liaison entre un composant pouvant être lié et une source de données.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=fullName>  
 Décrit la classe qui encapsule une source de données pour la liaison à des contrôles.  
  
## Rubriques connexes  
 [Composant BindingSource](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 Contient une liste de rubriques qui expliquent comment utiliser le composant <xref:System.Windows.Forms.BindingSource>.  
  
 [DataGridView, contrôle](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 Fournit une liste de rubriques qui expliquent comment utiliser un contrôle datagrid pouvant être lié.  
  
 Consultez également [Accès aux données dans Visual Studio](http://msdn.microsoft.com/library/wzabh8c4%20\(v=vs.110\)) ou [Accès aux données dans Visual Studio](http://msdn.microsoft.com/library/wzabh8c4%20\(v=vs.110\)).