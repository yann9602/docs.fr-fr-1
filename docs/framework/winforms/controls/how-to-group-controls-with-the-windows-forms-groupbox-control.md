---
title: "Comment&#160;: regrouper des contr&#244;les au moyen du contr&#244;le GroupBox Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), regroupement"
  - "GroupBox (contrôle Windows Forms), regrouper les contrôles"
  - "contrôles Windows Forms, regroupement"
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: regrouper des contr&#244;les au moyen du contr&#244;le GroupBox Windows Forms
Les contrôles <xref:System.Windows.Forms.GroupBox> Windows Forms permettent de regrouper d'autres contrôles.  Il existe trois raisons de regrouper des contrôles :  
  
-   Pour créer un regroupement visuel d'éléments de formulaire connexes en vue de fournir une interface plus claire à l'utilisateur.  
  
-   Pour créer un regroupement de programmation \(des cases d'option par exemple\).  
  
-   Pour déplacer les contrôles comme une même entité au moment du design.  
  
### Pour créer un groupe de contrôles  
  
1.  Dessinez un contrôle <xref:System.Windows.Forms.GroupBox> dans un formulaire.  
  
2.  Ajoutez des contrôles en les dessinant l'un après l'autre jusqu'à la zone de groupe.  
  
     Si vous voulez inclure dans la zone de groupe des contrôles existants, sélectionnez\-les tous, coupez\-les dans le Presse\-papiers, sélectionnez le contrôle <xref:System.Windows.Forms.GroupBox>, puis collez\-les dans la zone de groupe.  Vous pouvez aussi les faire glisser jusqu'à la zone de groupe.  
  
3.  Indiquez une légende appropriée pour la propriété <xref:System.Windows.Forms.GroupBox.Text%2A> de la zone de groupe.  
  
## Voir aussi  
 <xref:System.Windows.Forms.GroupBox>   
 [GroupBox, contrôle](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)