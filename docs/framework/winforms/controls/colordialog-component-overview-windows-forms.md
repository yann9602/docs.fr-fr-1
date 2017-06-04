---
title: "Vue d&#39;ensemble du composant ColorDialog (Windows Forms) | Microsoft Docs"
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
  - "ColorDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "boîte de dialogue des couleurs, à propos de la boîte de dialogue des couleurs"
  - "ColorDialog (composant), à propos de ColorDialog"
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du composant ColorDialog (Windows Forms)
Le composant <xref:System.Windows.Forms.ColorDialog> Windows Forms est une boîte de dialogue préconfigurée qui permet à l'utilisateur de sélectionner une couleur dans une palette et d'ajouter des couleurs personnalisées à cette palette.  Il est identique aux boîtes de dialogue de sélection de couleurs que vous pouvez voir dans d'autres applications Windows.  L'utilisation de ce contrôle dans votre application Windows est plus simple que de configurer votre propre boîte de dialogue.  
  
 La couleur sélectionnée dans la boîte de dialogue est retournée dans la propriété <xref:System.Windows.Forms.ColorDialog.Color%2A>.  Si la propriété <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> a la valeur `false`, le bouton Définir les couleurs personnalisées est désactivé, et l'utilisateur doit limiter son choix aux couleurs prédéfinies dans la palette.  Si la propriété <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> a la valeur `true`, l'utilisateur ne peut pas sélectionner de couleurs mélangées.  Pour afficher la boîte de dialogue, vous devez appeler sa méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog, composant](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)   
 [Contrôles et composants de boîte de dialogue](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)   
 [Comment : modifier l'apparence du composant ColorDialog Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)