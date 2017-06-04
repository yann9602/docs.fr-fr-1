---
title: "Trois cat&#233;gories de services graphiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "2D (graphismes vectoriels)"
  - "graphiques, catégories"
  - "images"
  - "typographie"
  - "graphismes vectoriels"
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Trois cat&#233;gories de services graphiques
Dans les Windows Forms, les offres graphiques figurent dans les trois catégories générales suivantes :  
  
-   Graphiques vectoriels à deux dimensions \(2D\)  
  
-   Images  
  
-   Typographie  
  
## Graphiques vectoriels 2D  
 Les graphiques vectoriels à deux dimensions sont des primitives \(lignes, courbes et figures\) qui sont spécifiées par des ensembles de points sur un système de coordonnées.  Par exemple, une ligne droite est spécifiée par ses deux extrémités et un rectangle, par un point indiquant l'emplacement de son coin supérieur gauche et un couple de valeurs indiquant sa largeur et sa hauteur.  Un tracé simple est spécifié par un tableau de points reliés par des segments de droite.  Une spline de Bézier est une courbe sophistiquée spécifiée par quatre points de contrôle.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit des classes et des structures qui stockent des informations sur les primitives, des classes qui stockent des informations sur la manière dont les primitives seront dessinées et des classes qui effectuent le dessin.  Par exemple, la structure <xref:System.Drawing.Rectangle> stocke l'emplacement et la taille d'un rectangle, la classe <xref:System.Drawing.Pen> stocke les informations sur la couleur, la largeur et le style de ligne, et la classe <xref:System.Drawing.Graphics> comprend des méthodes permettant de dessiner des lignes, des rectangles, des tracés et d'autres figures.  Il existe également plusieurs classes <xref:System.Drawing.Brush> qui stockent des informations sur la manière de remplir les figures fermées et les tracés avec des couleurs ou des motifs.  
  
 Vous pouvez enregistrer une image vectorielle, qui est une séquence de commandes graphiques, dans un métafichier.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit la classe <xref:System.Drawing.Imaging.Metafile> permettant d'enregistrer, d'afficher et de sauvegarder des métafichiers.  Avec les classes <xref:System.Drawing.Imaging.MetafileHeader> et <xref:System.Drawing.Imaging.MetaHeader>, vous pouvez inspecter les données stockées dans un en\-tête de métafichier.  
  
## Images  
 Certains types d'images sont difficiles ou impossibles à afficher avec les techniques de graphisme vectoriel.  Par exemple, il est difficile de spécifier en tant que collections de lignes et de courbes les images sur des boutons de barre d'outils ou qui s'affichent en tant qu'icônes.  Il est encore plus difficile de créer une photographie numérique haute résolution d'un stade de football bondé à l'aide de techniques vectorielles.  Les images de ce type sont stockées comme des bitmaps, qui sont des tableaux de nombres représentant les couleurs de points individuels sur l'écran.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit la classe <xref:System.Drawing.Bitmap> pour l'affichage, la manipulation et l'enregistrement des bitmaps.  
  
## Typographie  
 La typographie est l'affichage de texte dans divers styles, polices et tailles.  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit une prise en charge complète pour cette tâche complexe.  L'une des nouvelles fonctionnalités dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est l'anticrénelage de sous\-pixels, qui donne au texte restitué sur un écran à cristaux liquides une apparence plus lissée.  
  
 De plus, Windows Forms offre une option permettant de dessiner du texte avec les fonctions [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] de sa classe <xref:System.Windows.Forms.TextRenderer>.  
  
## Voir aussi  
 [Vue d'ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)   
 [À propos du code managé GDI\+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)   
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)