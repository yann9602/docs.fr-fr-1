---
title: "Comment&#160;: ancrer et arrimer des contr&#244;les enfants dans un contr&#244;le TableLayoutPanel | Microsoft Docs"
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
  - "net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles enfants, ancrer"
  - "contrôles (Windows Forms), enfant"
  - "disposition (Windows Forms), contrôles enfants"
  - "TableLayoutPanel (contrôle Windows Forms), contrôles enfants"
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ancrer et arrimer des contr&#244;les enfants dans un contr&#244;le TableLayoutPanel
Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> prend en charge les propriétés <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> dans ses contrôles enfants.  
  
### Pour aligner un contrôle enfant dans une cellule TableLayoutPanel  
  
1.  Créez un contrôle <xref:System.Windows.Forms.TableLayoutPanel> sur votre formulaire.  
  
2.  Affectez la valeur 1 aux propriétés <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> et <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
3.  Créez un contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Le <xref:System.Windows.Forms.Button> occupe le coin supérieur gauche de la cellule.  
  
4.  Affectez la valeur `Gauche` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> se déplace pour s'aligner avec la bordure gauche de la cellule.  
  
    > [!NOTE]
    >  Ce comportement diffère du comportement des autres contrôles conteneurs.  Dans d'autres contrôles conteneurs, le contrôle enfant ne bouge pas quand la propriété <xref:System.Windows.Forms.Control.Anchor%2A> est définie et la distance entre le contrôle ancré et la limite du parent conteneur est fixée au moment où la propriété <xref:System.Windows.Forms.Control.Anchor%2A> est définie.  
  
5.  Affectez la valeur `Haut, Gauche` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> se déplace pour occuper l'angle supérieur gauche de la cellule.  
  
6.  Répétez l'étape 5 avec la valeur `Top, Droite` pour déplacer le contrôle <xref:System.Windows.Forms.Button> à l'angle supérieur droit de la cellule.  Répétez l'opération avec les valeurs `Bas, Gauche` et `Bas, Droite`.  
  
### Pour étendre un contrôle enfant dans une cellule TableLayoutPanel  
  
1.  Affectez la valeur `Gauche, Droite` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour s'étendre sur toute la cellule.  
  
    > [!NOTE]
    >  Ce comportement diffère du comportement des autres contrôles conteneurs.  Dans d'autres contrôles conteneurs, le contrôle enfant n'est pas redimensionné quand la valeur `Gauche, Droite` ou `Haut, Bas` est affectée à la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.  
  
2.  Affectez la valeur `Haut, Bas` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour s'étendre du haut en bas de la cellule.  
  
3.  Affectez la valeur `Haut, Bas, Gauche, Droite` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour remplir la cellule.  
  
4.  Affectez la valeur `Aucun` à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> est redimensionné et centré dans la cellule.  
  
5.  Affectez la valeur <xref:System.Windows.Forms.DockStyle> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> se déplace pour s'aligner avec la bordure gauche de la cellule.  Le contrôle <xref:System.Windows.Forms.Button> conserve sa largeur, mais sa hauteur est redimensionnée pour remplir la cellule verticalement.  
  
    > [!NOTE]
    >  Il s'agit du même comportement que celui des autres contrôles conteneurs.  
  
6.  Affectez la valeur <xref:System.Windows.Forms.DockStyle> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.Button>.  Le contrôle <xref:System.Windows.Forms.Button> est redimensionné pour remplir la cellule.  
  
## Exemple  
 L'illustration suivante montre cinq boutons ancrés dans cinq cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.  
  
 ![Ancrage de TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.png "VS\_TLPanchor")  
  
 L'illustration suivante montre quatre boutons ancrés dans les coins de quatre cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.  
  
 ![Ancrage de TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.png "VS\_TLPanchor2")  
  
 L'illustration suivante montre trois boutons étirés par ancrage dans trois cellules <xref:System.Windows.Forms.TableLayoutPanel> distinctes.  
  
 ![Ancrage de TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS\_TLPAnchor3")  
  
 L'exemple de code suivant montre toutes les combinaisons de valeurs de propriété <xref:System.Windows.Forms.Control.Anchor%2A> pour un contrôle <xref:System.Windows.Forms.Button> dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [TableLayoutPanel, contrôle](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)