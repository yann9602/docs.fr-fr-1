---
title: "Peinture et rendu personnalis&#233;s des contr&#244;les | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), peindre"
  - "contrôles personnalisés (Windows Forms), rendu"
  - "OnPaint (méthode)"
  - "contrôles utilisateur (Windows Forms), peindre"
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Peinture et rendu personnalis&#233;s des contr&#244;les
La peinture personnalisée des contrôles fait partie de ces tâches complexes qui se trouvent grandement facilitées dans le .NET Framework.  Lorsque vous créez un contrôle personnalisé, de nombreuses options vous permettent de définir son apparence graphique.  Si vous créez un contrôle héritant de `Control`, vous devez fournir du code définissant sa représentation graphique.  Si vous créez un contrôle utilisateur héritant du `UserControl` ou d'un des contrôles Windows Forms, vous pouvez substituer la représentation graphique standard par votre propre code graphique.  Si vous créez un contrôle `UserControl` et souhaitez fournir un rendu personnalisé pour ses contrôles constitutifs, vos options sont plus limitées, mais les possibilités graphiques dont vous disposez tant pour vos contrôles que pour vos applications reste très large.  
  
## Dans cette section  
 [Rendu d'un contrôle Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Montre comment programmer la logique qui affiche un contrôle.  
  
 [Contrôles dessinés par l'utilisateur](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Propose une vue d'ensemble de la procédure visant à écrire et à substituer le code de rendu de votre contrôle.  
  
 [Contrôles constitutifs](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Explique comment implémenter un code de rendu personnalisé pour les contrôles constitutifs de vos formulaires et contrôles utilisateur.  
  
 [Comment : rendre votre contrôle invisible au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Montre comment utiliser la propriété <xref:System.Windows.Forms.Control.Visible%2A> pour masquer et afficher un contrôle.  
  
 [Comment : affecter un arrière\-plan transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Montre comment utiliser la méthode <xref:System.Windows.Forms.Control.SetStyle%2A> pour créer une couleur d'arrière\-plan qui est opaque, transparente ou partiellement transparente.  
  
 [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Montre comment restituer les contrôles à l'aide de styles visuels dans les systèmes d'exploitation qui les prennent en charge.  
  
## Référence  
 <xref:System.Windows.Forms.Control>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.UserControl>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Décrit cette méthode.  
  
## Rubriques connexes  
 [Comment : créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Présente la fonctionnalité graphique [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] disponible dans Visual Studio et offre des liens vers des informations supplémentaires.  
  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 Décrit les types de contrôles personnalisés que vous pouvez créer.