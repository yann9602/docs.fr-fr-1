---
title: "Vue d&#39;ensemble du contr&#244;le StatusBar (Windows Forms) | Microsoft Docs"
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
  - "StatusBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "barres d'état"
  - "StatusBar (contrôle Windows Forms), à propos du contrôle StatusBar"
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du contr&#244;le StatusBar (Windows Forms)
> [!IMPORTANT]
>  Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> et y ajoutent des fonctionnalités ; toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 Le contrôle Windows Forms [StatusBar, contrôle](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) est utilisé sur les formulaires en tant que zone, qui s'affiche la plupart du temps en bas d'une fenêtre, dans laquelle une application peut afficher différents types d'informations d'état.  Les contrôles <xref:System.Windows.Forms.StatusBar> peuvent avoir des panneaux de barre d'état affichant du texte ou des icônes indiquant l'état ou bien une série d'icônes dans une animation indiquant qu'un processus fonctionne, comme par exemple, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] qui indique que le document est enregistré.  
  
## Utilisation du contrôle StatusBar  
 Internet Explorer utilise une barre d'état pour indiquer l'URL d'une page lorsque la souris passe sur le lien hypertexte. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] vous donne des informations sur l'emplacement des pages et des sections, ainsi que sur les modes de modification tels que la refrappe ou le suivi des révisions. [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] utilise la barre d'état pour donner des informations contextuelles, par exemple sur la manipulation des fenêtres ancrables ancrées ou flottantes.  
  
 Vous pouvez afficher un message dans la barre d'état en affectant à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `false` \(valeur par défaut\) et en définissant pour la propriété <xref:System.Windows.Forms.StatusBar.Text%2A> de la barre d'état le texte que vous voulez y voir affiché.  Vous pouvez diviser la barre d'état en panneaux pour afficher plusieurs types d'informations en affectant à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `true` et en utilisant la méthode <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)