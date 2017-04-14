---
title: "Vue d&#39;ensemble du contr&#244;le TableLayoutPanel | Microsoft Docs"
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
  - "TableLayoutPanel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), redimensionner"
  - "disposition (Windows Forms), TableLayoutPanel (contrôle)"
  - "contrôles redimensionnables"
  - "TableLayoutPanel (contrôle Windows Forms), à propos du contrôle TableLayoutPanel"
  - "contrôles Windows Forms, redimensionnement proportionnel"
  - "Windows Forms, redimensionnement proportionnel des contrôles"
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du contr&#244;le TableLayoutPanel
Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> réorganise son contenu dans une grille.  La disposition étant effectuée au moment du design et au moment de l'exécution, elle peut changer dynamiquement quand l'environnement d'application change.  Cela permet de redimensionner proportionnellement les contrôles du panneau, pour pouvoir répondre à des modifications telles que le redimensionnement du contrôle parent ou le changement de longueur de texte en raison de la localisation.  
  
 Tout contrôle Windows Forms peut être un enfant du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, y compris d'autres instances de <xref:System.Windows.Forms.TableLayoutPanel>.  Cela vous permet de construire des dispositions sophistiquées qui s'adaptent aux modifications au moment de l'exécution.  
  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> peut s'étendre pour accepter de nouveaux contrôles quand ils sont ajoutés, en fonction de la valeur des propriétés <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, et <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A>.  L'affectation de la valeur 0 à la propriété <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> ou <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> indique que le <xref:System.Windows.Forms.TableLayoutPanel> sera indépendant dans la direction correspondante.  
  
 Vous pouvez également contrôler la direction d'expansion \(horizontale ou verticale\) une fois que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> est rempli de contrôles enfants.  Par défaut, le contrôle <xref:System.Windows.Forms.TableLayoutPanel> s'étend vers le bas en ajoutant des lignes.  
  
 Si vous souhaitez que les lignes et les colonnes se comportent différemment du comportement par défaut, vous pouvez contrôler leurs propriétés à l'aide des propriétés <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> et <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>.  Vous pouvez définir les propriétés des lignes ou des colonnes individuellement.  
  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> ajoute les propriétés suivantes à ses contrôles enfants : `Cell`, `Column`, `Row`, `ColumnSpan`, et `RowSpan`.  
  
 Vous pouvez fusionner des cellules dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel> en définissant les propriétés `ColumnSpan` ou `RowSpan` sur un contrôle enfant.  
  
1.  [Comment : aligner et étirer un contrôle dans un contrôle TableLayoutPanel](http://msdn.microsoft.com/library/ms171688%20\(v=vs.110\))  
  
2.  [Comment : étendre des lignes et des colonnes dans un contrôle TableLayoutPanel](http://msdn.microsoft.com/library/ms171687%20\(v=vs.110\))  
  
3.  [Comment : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel](http://msdn.microsoft.com/library/ms171686%20\(v=vs.110\))  
  
4.  [Procédure pas à pas : disposition des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c%20\(v=vs.110\))  
  
## Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutSettings>   
 [Comment : créer une présentation Windows Forms qui répond bien à la localisation](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)   
 [Comment : créer un Windows Form redimensionnable pour l'entrée de données](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)   
 [Meilleures pratiques pour le contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)