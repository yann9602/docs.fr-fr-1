---
title: "Trois catégories de services graphiques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 305ffae04b6f1ddb94081f8a6ee334f8195caba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="three-categories-of-graphics-services"></a>Trois catégories de services graphiques
Les offres de graphiques dans les Windows Forms se répartissent en trois grandes catégories :  
  
-   Graphiques vectoriels (2-D)  
  
-   Acquisition d’images  
  
-   Typographie  
  
## <a name="2-d-vector-graphics"></a>Graphiques vectoriels 2D  
 Graphismes vectoriels à deux dimensions sont des primitives ; tels que des lignes, des courbes et des chiffres. qui sont spécifiées par les ensembles de points sur un système de coordonnées. Par exemple, une ligne droite est spécifiée par ses deux points de terminaison, et un rectangle spécifié par un point indiquant l’emplacement de son coin supérieur gauche et une paire de valeurs indiquant sa largeur et sa hauteur. Un chemin d’accès simple est spécifié par un tableau de points reliés par des lignes droites. Une spline de Bézier est une courbe sophistiquée spécifiée par quatre points de contrôle.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Fournit des classes et des structures qui stockent des informations sur les primitives, des classes qui stockent des informations sur la façon dont les primitives seront dessinées et des classes qui effectuent réellement le dessin. Par exemple, le <xref:System.Drawing.Rectangle> structure stocke l’emplacement et la taille d’un rectangle ; le <xref:System.Drawing.Pen> classe stocke des informations sur le style de ligne, couleur de ligne et largeur de ligne et la <xref:System.Drawing.Graphics> classe a des méthodes pour dessiner des lignes, des rectangles, des chemins d’accès, et autres chiffres. Il existe également plusieurs <xref:System.Drawing.Brush> les classes qui stockent des informations sur la façon de figures fermées et chemins d’accès seront remplies avec des couleurs ou des modèles.  
  
 Vous pouvez enregistrer une image vectorielle, qui est une séquence de commandes graphiques, dans un métafichier. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Fournit la <xref:System.Drawing.Imaging.Metafile> classe pour, afficher, enregistrer des métafichiers. Avec la <xref:System.Drawing.Imaging.MetafileHeader> et <xref:System.Drawing.Imaging.MetaHeader> classes, vous pouvez inspecter les données stockées dans un en-tête de métafichier.  
  
## <a name="imaging"></a>Acquisition d’images  
 Certains types d’images sont difficiles ou impossibles à afficher avec les techniques de graphismes vectoriels. Par exemple, les images de boutons de barre d’outils et les images qui apparaissent sous forme d’icônes sont difficiles à spécifier en tant que collections de lignes et de courbes. Une photographie numérique haute résolution d’un stade de football est encore plus difficile de créer avec les techniques de vecteur. Images de ce type sont stockées comme des bitmaps, qui sont des tableaux de nombres qui représentent les couleurs de points individuels sur l’écran. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Fournit la <xref:System.Drawing.Bitmap> classe pour l’affichage, la manipulation et enregistrer des bitmaps.  
  
## <a name="typography"></a>Typographie  
 Typographie est l’affichage du texte dans une variété de polices, les tailles et les styles. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Fournit la prise en charge étendue pour cette tâche complexe. Une des nouvelles fonctionnalités de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] est l’anticrénelage, ce qui donne au texte restitué sur un écran une apparence plus lisse.  
  
 En outre, Windows Forms offre une option permettant de dessiner du texte avec [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] fonctionnalités dans son <xref:System.Windows.Forms.TextRenderer> classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [À propos du code managé GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
