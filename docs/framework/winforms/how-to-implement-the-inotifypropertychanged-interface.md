---
title: "Comment&#160;: impl&#233;menter l&#39;interface INotifyPropertyChanged | Microsoft Docs"
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
  - "INotifyPropertyChanged (interface), implémenter"
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: impl&#233;menter l&#39;interface INotifyPropertyChanged
L'exemple de code suivant illustre l'implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  Implémentez cette interface sur les objets métier utilisés dans la liaison de données Windows Forms.  Une fois implémentée, l'interface communique à un contrôle dépendant les modifications des propriétés d'un objet métier.  
  
## Exemple  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## Voir aussi  
 [Comment : appliquer le modèle PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)   
 [Notification de modifications dans la liaison de données Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)