---
title: "Comment&#160;: cr&#233;er des touches d&#39;acc&#232;s rapide pour les contr&#244;les Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "touches d'accès rapide, créer des touches pour les contrôles"
  - "touches d'accès rapide, Windows Forms"
  - "touche ALT"
  - "caractère et commercial de la touche de raccourci"
  - "bouton (contrôle Windows Forms), touches d'accès rapide"
  - "contrôles (Windows Forms), touches d'accès rapide"
  - "contrôles de boîte de dialogue, mnémoniques"
  - "exemples (Windows Forms), contrôles"
  - "raccourcis clavier, créer des touches pour les contrôles"
  - "mnémoniques, ajouter aux contrôles de boîte de dialogue"
  - "Text (propriété), spécifier des touches d'accès pour les contrôles"
  - "contrôles Windows Forms, touches d'accès rapide"
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: cr&#233;er des touches d&#39;acc&#232;s rapide pour les contr&#244;les Windows Forms &#224; l&#39;aide du concepteur
Une *touche d'accès rapide* est un caractère souligné dans le texte d'un menu, d'un élément de menu ou dans l'étiquette d'un contrôle, tel qu'un bouton.  Elle permet à l'utilisateur de « cliquer » sur un bouton en appuyant sur la touche ALT en même temps que sur la touche d'accès rapide prédéfinie.  Par exemple, si un bouton exécute une procédure d'impression d'un formulaire \(sa propriété `Text` a donc la valeur « Print »\), l'ajout d'un et commercial \(&\) devant la lettre « P » a pour effet de souligner celle\-ci dans le texte du bouton au moment de l'exécution.  L'utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT\+P.  Vous ne pouvez pas avoir de touche d'accès rapide pour un contrôle qui ne peut pas recevoir le focus.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer une touche d'accès rapide pour un contrôle  
  
1.  Dans la fenêtre **Propriétés**, définissez comme valeur de la propriété `Text` une chaîne qui inclut un signe & devant la lettre destinée à servir de touche d'accès rapide.  Par exemple, pour définir la lettre « P » comme touche d'accès rapide, tapez &Print dans la grille.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Button>   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)