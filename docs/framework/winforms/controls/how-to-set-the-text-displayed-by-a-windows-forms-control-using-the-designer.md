---
title: "Comment&#160;: d&#233;finir le texte affich&#233; par un contr&#244;le Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "contrôles (Windows Forms), définir la légende"
  - "Windows Forms, définir le texte affiché"
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: d&#233;finir le texte affich&#233; par un contr&#244;le Windows Forms &#224; l&#39;aide du concepteur
En général, un contrôle Windows Forms affiche un texte qui rappelle sa fonction première.  Par exemple, un contrôle <xref:System.Windows.Forms.Button> affiche habituellement une légende qui indique l'action qui est exécutée lorsque l'utilisateur clique sur le bouton.  Pour tous les contrôles, vous pouvez définir ou retourner le texte en utilisant la propriété <xref:System.Windows.Forms.Control.Text%2A>.  Vous pouvez changer la police à l'aide de la propriété <xref:System.Windows.Forms.Control.Font%2A>.  
  
### Pour définir le texte et la police à l'aide du concepteur  
  
1.  Dans la fenêtre Propriétés, définissez pour la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle une chaîne appropriée.  
  
     Pour créer une touche de raccourci soulignée, incluez un signe & avant la lettre destinée à devenir la touche de raccourci.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.Control.Font%2A>.  
  
     Dans la boîte de dialogue de police de caractères standard, sélectionnez la police, le style de police, la taille, les effets \(tels que barré ou soulignement\) et le script que vous voulez.  
  
## Voir aussi  
 [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)