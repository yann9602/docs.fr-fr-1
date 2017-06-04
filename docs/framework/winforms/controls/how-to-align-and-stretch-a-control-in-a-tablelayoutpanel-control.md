---
title: "Comment&#160;: aligner et &#233;tirer un contr&#244;le dans un contr&#244;le TableLayoutPanel | Microsoft Docs"
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
  - "net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), aligner"
  - "contrôles (Windows Forms), étirer"
  - "TableLayoutPanel (contrôle Windows Forms), étirer les contrôles"
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: aligner et &#233;tirer un contr&#244;le dans un contr&#244;le TableLayoutPanel
Vous pouvez aligner et étirer des contrôles dans un <xref:System.Windows.Forms.TableLayoutPanel> avec les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A>.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour aligner et étirer un contrôle  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers la cellule supérieure gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Le contrôle <xref:System.Windows.Forms.Button> est centré dans la cellule.  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `Left,Right`.  Le contrôle <xref:System.Windows.Forms.Button> s'étire pour correspondre à la largeur de la cellule.  
  
4.  Affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `Top,Bottom`.  Le contrôle <xref:System.Windows.Forms.Button> s'étire pour correspondre à la hauteur de la cellule.  
  
5.  Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur <xref:System.Windows.Forms.DockStyle>.  Le contrôle <xref:System.Windows.Forms.Button> se développe pour remplir la cellule.  
  
6.  Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur <xref:System.Windows.Forms.DockStyle>.  Le contrôle <xref:System.Windows.Forms.Button> retourne à sa taille d'origine et se déplace vers l'angle supérieur gauche de la cellule.  Le **Concepteur Windows Forms** a attribué à la propriété  <xref:System.Windows.Forms.Control.Anchor%2A> la valeur `Top, Left`.  
  
7.  Affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur `Bottom,Right`.  Le contrôle <xref:System.Windows.Forms.Button> se déplace vers l'angle inférieur droit de la cellule.  
  
8.  Affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur <xref:System.Windows.Forms.AnchorStyles>.  Le contrôle <xref:System.Windows.Forms.Button> se déplace au centre de la cellule.  
  
## Voir aussi  
 [TableLayoutPanel, contrôle](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)