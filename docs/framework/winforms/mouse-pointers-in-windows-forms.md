---
title: "Pointeurs de souris dans les Windows Forms | Microsoft Docs"
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
  - "curseurs, paramètre (Windows Forms)"
  - "curseurs de la souris"
  - "pointeurs de souris"
  - "pointeurs de souris, paramètre (Windows Forms)"
  - "souris, curseurs"
  - "pointeurs, paramètre (Windows Forms)"
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Pointeurs de souris dans les Windows Forms
Le *pointeur* de la souris, également appelé curseur, est une bitmap qui spécifie un point de focus sur l'écran destiné aux entrées d'utilisateur avec la souris.  Cette rubrique fournit une vue d'ensemble du pointeur de la souris dans Windows Forms et décrit quelques\-unes des méthodes de modification et de contrôle de ce dernier.  
  
## Accès au pointeur de la souris  
 Le pointeur de la souris est représenté par la classe <xref:System.Windows.Forms.Cursor> et chaque <xref:System.Windows.Forms.Control> possède une propriété <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=fullName> qui spécifie le pointeur associé à ce contrôle.  La classe <xref:System.Windows.Forms.Cursor> contient des propriétés qui décrivent le pointeur \(par exemple, les propriétés <xref:System.Windows.Forms.Cursor.Position%2A> et <xref:System.Windows.Forms.Cursor.HotSpot%2A>\), ainsi que des méthodes qui permettent de modifier l'aspect du pointeur \(par exemple, les méthodes <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A> et <xref:System.Windows.Forms.Cursor.DrawStretched%2A>\).  
  
## Contrôle du pointeur de la souris  
 Vous pouvez limiter la zone d'utilisation du pointeur de la souris ou modifier la position de la souris.  Vous pouvez obtenir ou définir l'emplacement actuel de la souris à l'aide de la propriété <xref:System.Windows.Forms.Cursor.Position%2A> de <xref:System.Windows.Forms.Cursor>.  De plus, vous pouvez limiter la zone d'utilisation du pointeur de la souris via la définition de la propriété <xref:System.Windows.Forms.Cursor.Clip%2A>.  La zone de découpage correspond par défaut à l'écran entier.  
  
## Modification du pointeur de la souris  
 La modification du pointeur de la souris constitue un moyen important de fournir des informations à l'utilisateur.  Par exemple, le pointeur de la souris peut être modifié dans les gestionnaires des événements <xref:System.Windows.Forms.Control.MouseEnter> et <xref:System.Windows.Forms.Control.MouseLeave> pour indiquer à l'utilisateur que des calculs sont en cours et pour limiter l'interaction utilisateur au sein du contrôle.  Il arrive parfois que le pointeur de la souris change en raison d'événements système, tels qu'une opération de glisser\-déplacer dans votre application.  
  
 Le principal moyen de modifier le pointeur de la souris consiste à définir la propriété <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.Control.DefaultCursor%2A> d'un contrôle en affectant un nouveau <xref:System.Windows.Forms.Cursor>.  Pour obtenir des exemples de modification du pointeur de la souris, consultez l'exemple de code figurant dans la classe <xref:System.Windows.Forms.Cursor>.  Par ailleurs, la classe <xref:System.Windows.Forms.Cursors> expose un jeu d'objets <xref:System.Windows.Forms.Cursor> pour un grand nombre de types de pointeurs différents \(par exemple, un pointeur qui ressemble à une main\).  Pour afficher le pointeur d'attente \(qui ressemble à un sablier\) chaque fois que le pointeur de la souris se trouve sur le contrôle, utilisez la propriété <xref:System.Windows.Forms.Control.UseWaitCursor%2A> de la classe <xref:System.Windows.Forms.Control>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Cursor>   
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)   
 [Fonctionnalité de glisser\-déplacer dans les Windows Forms](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)