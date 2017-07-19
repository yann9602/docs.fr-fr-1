---
title: "Comment&#160;: dimensionner un contr&#244;le Label Windows Forms en fonction de son contenu | Microsoft Docs"
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
  - "légendes, dimensionner"
  - "Label (contrôle Windows Forms), dimensionner en fonction du contenu"
  - "étiquettes, dimensionner en fonction du contenu"
  - "taille, contrôles"
  - "dimensionner les contrôles"
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: dimensionner un contr&#244;le Label Windows Forms en fonction de son contenu
Le contrôle <xref:System.Windows.Forms.Label> Windows Forms peut compter une ou plusieurs lignes ; il peut avoir une taille fixe ou au contraire être redimensionnable pour pouvoir afficher sa légende.  La propriété <xref:System.Windows.Forms.Label.AutoSize%2A> vous permet de dimensionner les contrôles en fonction de la taille des légendes, ce qui est particulièrement utile si celles\-ci sont appelées à changer au moment de l'exécution.  
  
### Pour qu'un contrôle Label soit redimensionné dynamiquement en fonction de son contenu  
  
1.  affectez à sa propriété <xref:System.Windows.Forms.Label.AutoSize%2A> la valeur `true`.  
  
 Si la propriété <xref:System.Windows.Forms.Label.AutoSize%2A> a la valeur `false`, le texte spécifié dans la propriété <xref:System.Windows.Forms.Label.Text%2A> passe à la ligne suivante, si cela est possible, mais le contrôle ne s'agrandit pas.  
  
## Voir aussi  
 [Comment : créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)   
 [Vue d'ensemble du contrôle Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Label, contrôle](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)