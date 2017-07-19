---
title: "Comment&#160;: ancrer des contr&#244;les enfants dans un contr&#244;le FlowLayoutPanel | Microsoft Docs"
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
  - "contrôles enfants, ancrer"
  - "contrôles (Windows Forms), enfant"
  - "FlowLayoutPanel (contrôle Windows Forms), contrôles enfants"
  - "disposition (Windows Forms), contrôles enfants"
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: ancrer des contr&#244;les enfants dans un contr&#244;le FlowLayoutPanel
Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> prend en charge les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> dans ses contrôles enfants.  
  
### Pour ancrer des contrôles enfants dans un contrôle FlowLayoutPanel  
  
1.  Créez un contrôle <xref:System.Windows.Forms.FlowLayoutPanel> sur votre formulaire.  
  
2.  Affectez la valeur 300 à la propriété <xref:System.Windows.Forms.Control.Width%2A> du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> et la valeur <xref:System.Windows.Forms.FlowDirection> à sa propriété <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
3.  Créez deux contrôles <xref:System.Windows.Forms.Button> et placez\-les dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
4.  Affectez la valeur 200 à la propriété <xref:System.Windows.Forms.Control.Width%2A> du premier bouton.  
  
5.  Affectez la valeur <xref:System.Windows.Forms.DockStyle> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du deuxième bouton.  
  
    > [!NOTE]
    >  Le deuxième bouton a la même largeur que le premier.  Il ne s'étire pas sur toute la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
6.  Affectez la valeur `Aucun` à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du deuxième bouton.  Le bouton reprend sa largeur d'origine.  
  
7.  Affectez la valeur `Gauche, Droite` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du deuxième bouton.  
  
    > [!IMPORTANT]
    >  Le deuxième bouton a la même largeur que le premier.  Il ne s'étire pas sur toute la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  Il s'agit de la règle générale pour l'ancrage et l'arrimage dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> : pour les sens de flux verticaux, le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> calcule la largeur d'une colonne implicite à partir du contrôle enfant le plus large dans la colonne.  Tous les autres contrôles dans cette colonne avec des propriétés <xref:System.Windows.Forms.Control.Anchor%2A> ou <xref:System.Windows.Forms.Control.Dock%2A> sont alignés ou étirés pour s'ajuster à cette colonne implicite.  Le comportement fonctionne de façon similaire pour les sens de flux horizontaux.  Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> calcule la hauteur d'une ligne implicite à partir du plus grand contrôle enfant sur la ligne et tous les contrôles enfants ancrés ou arrimés sur cette ligne sont alignés ou dimensionnés pour s'ajuster à la ligne implicite.  
  
## Exemple  
 L'illustration suivante montre quatre boutons qui sont ancrés et arrimés par rapport au bouton bleu dans un <xref:System.Windows.Forms.FlowLayoutPanel>.  <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> a la valeur <xref:System.Windows.Forms.FlowDirection>.  
  
 ![Ancrage de FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.png "NET\_FLPanchorExp")  
  
 L'illustration suivante montre quatre boutons qui sont ancrés et arrimés par rapport au bouton bleu dans un <xref:System.Windows.Forms.FlowLayoutPanel>.  <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> a la valeur <xref:System.Windows.Forms.FlowDirection>.  
  
 ![Ancrage de FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.png "VS\_FLPanchor2")  
  
 L'exemple de code suivant illustre différentes valeurs de propriétés <xref:System.Windows.Forms.Control.Anchor%2A> pour un contrôle <xref:System.Windows.Forms.Button> dans un contrôle <xref:System.Windows.Forms.FlowLayoutPanel>.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 [Vue d'ensemble du contrôle FlowLayoutPanel](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)