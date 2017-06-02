---
title: "Vue d&#39;ensemble des contr&#244;les HScrollBar et VScrollBar (Windows Forms) | Microsoft Docs"
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
  - "HScrollBar"
  - "VScrollBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "HScrollBar (contrôle Windows Forms), à propos de HScrollBar"
  - "barres de défilement, à propos des barres de défilement"
  - "ScrollBar (contrôle Windows Forms)"
  - "ScrollBar (contrôle Windows Forms), à propos du contrôle ScrollBar"
  - "VScrollBar (contrôle Windows Forms), à propos du contrôle VScrollBar"
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble des contr&#244;les HScrollBar et VScrollBar (Windows Forms)
Les contrôles <xref:System.Windows.Forms.ScrollBar> Windows Forms permettent une navigation facile dans une longue liste d'éléments ou un important volume d'informations en les faisant défiler horizontalement ou verticalement dans une application ou un contrôle.  Les barres de défilement sont un élément courant de l'interface Windows. De ce fait, le contrôle <xref:System.Windows.Forms.ScrollBar> est souvent utilisé avec les contrôles qui ne sont pas dérivés de la classe <xref:System.Windows.Forms.ScrollableControl>.  De la même manière, de nombreux développeurs choisissent d'incorporer le contrôle <xref:System.Windows.Forms.ScrollBar> lors de la création de leurs propres contrôles utilisateur.  
  
 Les contrôles <xref:System.Windows.Forms.HScrollBar> \(horizontaux\) et <xref:System.Windows.Forms.VScrollBar> \(verticaux\) fonctionnent indépendamment des autres contrôles et ont leur propre jeux d'événements, de propriétés et de méthodes.  Les contrôles <xref:System.Windows.Forms.ScrollBar> ne sont pas les mêmes que les barres de défilement intégrées attachées aux zones de texte, zones de liste, zones de liste déroulante ou formulaires MDI \(le contrôle <xref:System.Windows.Forms.TextBox> possède une propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> pour afficher ou masquer les barres de défilement attachées au contrôle\).  
  
 Les contrôles <xref:System.Windows.Forms.ScrollBar> utilisent l'événement <xref:System.Windows.Forms.ScrollBar.Scroll> pour surveiller le mouvement de la case de défilement \(parfois appelée le curseur\) le long de la barre de défilement.  L'utilisation de l'événement <xref:System.Windows.Forms.ScrollBar.Scroll> permet d'avoir accès à la valeur de la barre de défilement au moment même où la case de défilement est déplacée.  
  
## Value, propriété  
 La propriété <xref:System.Windows.Forms.ScrollBar.Value%2A> \(qui a par défaut la valeur 0\) est une valeur `integer` correspondant à la position de la case de défilement dans la barre de défilement.  Lorsque la position de la case de défilement est à sa valeur minimale, la case de défilement se place le plus à gauche \(pour les barres de défilement horizontal\) ou tout en haut \(pour les barres de défilement vertical\).  Lorsque la position de la case de défilement est à sa valeur maximale, cette dernière se place le plus à droite ou tout en bas.  De la même manière, une valeur à mi\-chemin entre les valeurs minimale et maximale place le bord de tête de la case de défilement au milieu de la barre de défilement.  
  
 Pour changer la valeur de la barre de défilement, l'utilisateur peut non seulement utiliser les clics de souris, mais aussi faire glisser la case de défilement à tout emplacement le long de la barre.  La valeur qui en résulte dépend de la position de la case de défilement, mais elle se situe toujours dans la plage des propriétés <xref:System.Windows.Forms.ScrollBar.Minimum%2A> aux propriétés <xref:System.Windows.Forms.ScrollBar.Maximum%2A> définies par l'utilisateur.  
  
## Propriétés LargeChange et SmallChange  
 Lorsque l'utilisateur appuie sur la touche PG. PRÉC ou PG. SUIV, ou clique dans la barre de défilement d'un côté ou de l'autre de la case de défilement, la propriété <xref:System.Windows.Forms.ScrollBar.Value%2A> change en fonction de la valeur définie dans la propriété <xref:System.Windows.Forms.ScrollBar.LargeChange%2A>.  
  
 Lorsque l'utilisateur appuie sur l'une des touches de direction ou clique sur l'un des boutons de la barre de défilement, la propriété <xref:System.Windows.Forms.ScrollBar.Value%2A> change en fonction de la valeur définie dans la propriété <xref:System.Windows.Forms.ScrollBar.SmallChange%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.HScrollBar>   
 <xref:System.Windows.Forms.VScrollBar>   
 [Additions to Windows Forms for the .NET Framework 2.0](http://msdn.microsoft.com/fr-fr/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)