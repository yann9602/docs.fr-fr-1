---
title: "&#201;v&#233;nements de modification de propri&#233;t&#233; | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), modification des propriétés à l'aide du code"
  - "propriétés (Windows Forms), modifications"
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# &#201;v&#233;nements de modification de propri&#233;t&#233;
Si vous souhaitez que votre contrôle envoie des notifications lorsqu'une propriété nommée *NomPropriété* change, définissez un événement nommé *NomPropriété*`Changed` et une méthode  nommée `On`*NomPropriété*`Changed` qui déclenche l'événement.  La convention d'affectation de noms dans les Windows Forms spécifie l'ajout du mot *Changed* au nom de la propriété.  Le type délégué d'événement associé pour les événements de modification de propriété est <xref:System.EventHandler> et le type des données d'événement est <xref:System.EventArgs>.  La classe de base <xref:System.Windows.Forms.Control> définit beaucoup d'événements changés par la propriété, par exemple <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, et d'autres.  Pour plus informations générales sur les événements, consultez [Événements](../../../../docs/standard/events/index.md) et [Événements dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).  
  
 Les événements de modification de propriété sont utiles, car ils permettent aux consommateurs d'un contrôle d'attacher des gestionnaires d'événements qui répondent à la modification.  Si votre contrôle doit répondre à un événement de modification de propriété qu'il déclenche, substituez la méthode `On`*NomPropriété*`Changed` correspondante plutôt que d'attacher un délégué à l'événement.  Un contrôle répond généralement à un événement de modification de propriété en mettant à jour d'autres propriétés ou encore en redessinant une partie ou la totalité de sa surface de dessin.  
  
 L'exemple suivant montre comment le contrôle personnalisé `FlashTrackBar` répond à certains événements de modification de propriété qu'il hérite de <xref:System.Windows.Forms.Control>.  Pour l'exemple complet, consultez [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## Voir aussi  
 [Événements](../../../../docs/standard/events/index.md)   
 [Événements dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [Propriétés dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)