---
title: "Graphiques mis deux fois en m&#233;moire tampon | Microsoft Docs"
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
  - "doubles tampons"
  - "exemples (Windows Forms), graphiques mis deux fois en mémoire tampon"
  - "scintillement, réduire à l'aide du mécanisme de double tampon"
  - "graphiques, mis deux fois en mémoire tampon"
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Graphiques mis deux fois en m&#233;moire tampon
Le scintillement est un problème commun lors de la programmation de graphiques.  Les opérations graphiques qui requièrent plusieurs opérations de peinture complexes peuvent donner l'impression que les images rendues scintillent ou ont une apparence inacceptable.  Pour traiter ces problèmes, le .NET Framework fournit l'accès au mécanisme de double tampon.  
  
 Le mécanisme de double tampon utilise une mémoire tampon pour traiter les problèmes de scintillement associés aux opérations de peinture multiples.  Lorsque le mécanisme de double tampon est activé, toutes les opérations de peinture sont restituées en premier à une mémoire tampon à la place de la surface de dessin sur l'écran.  Après avoir effectué toutes les opérations de peinture, la mémoire tampon est copiée directement vers la surface de dessin qui lui est associée.  Dans la mesure où une seule opération graphique est exécutée sur l'écran, le scintillement de l'image associé aux opérations de peinture complexes est éliminé.  
  
## Mécanisme de double tampon par défaut  
 La façon la plus facile d'utiliser le mécanisme de double tampon dans vos applications est d'utiliser le mécanisme de double tampon par défaut pour les formulaires et les contrôles qui est fourni par le .NET Framework.  Vous pouvez activer le mécanisme de double tampon par défaut pour vos Windows Forms et contrôles Windows créés en attribuant à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true` ou en utilisant la méthode <xref:System.Windows.Forms.Control.SetStyle%2A>.  Pour plus d'informations, consultez [Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## Gestion manuelle des graphiques mis en mémoire tampon  
 Pour des scénarios plus avancés de mécanisme de double tampon, tels que l'animation ou la gestion de mémoire avancée, vous pouvez utiliser les classes .NET Framework pour implémenter votre propre logique de mécanisme de double tampon.  La classe responsable de l'allocation et de la gestion des mémoires tampon de graphiques individuelles est la classe <xref:System.Drawing.BufferedGraphicsContext>.  Chaque domaine d'application a sa propre instance de <xref:System.Drawing.BufferedGraphicsContext> par défaut qui gère tout le mécanisme de double tampon par défaut pour cette application.  Dans la plupart des cas, il n'y aura qu'un seul domaine d'application par application ; il y a, donc, en général un <xref:System.Drawing.BufferedGraphicsContext> par défaut par application.  Les instances de <xref:System.Drawing.BufferedGraphicsContext> par défaut sont gérées par la classe <xref:System.Drawing.BufferedGraphicsManager>.  Vous pouvez récupérer une référence à l'instance de <xref:System.Drawing.BufferedGraphicsContext> par défaut en appelant le [BufferedGraphicsManager.Current Property](frlrfSystemDrawingBufferedGraphicsManagerClassCurrentTopic).  Vous pouvez également créer une instance de <xref:System.Drawing.BufferedGraphicsContext> dédiée qui peut améliorer les performances des applications à forte intensité graphique.  Pour plus d'informations sur la création d'une instance de <xref:System.Drawing.BufferedGraphicsContext>, consultez [Comment : gérer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
## Affichage manuel des graphiques mis en mémoire tampon  
 Vous pouvez utiliser une instance de la classe <xref:System.Drawing.BufferedGraphicsContext> pour créer des mémoires tampon de graphiques en appelant la [méthode BufferedGraphicsContext.Allocate](frlrfSystemDrawingBufferedGraphicsContextClassAllocateTopic) qui retourne une instance de la classe <xref:System.Drawing.BufferedGraphics>.  Un objet <xref:System.Drawing.BufferedGraphics> gère une mémoire tampon qui est associée à une surface de rendu, telle qu'un formulaire ou un contrôle.  
  
 Après qu'il a été instancié, la classe <xref:System.Drawing.BufferedGraphics> gère le rendu dans une mémoire tampon de graphiques en mémoire.  Vous pouvez restituer des graphiques à la mémoire tampon à travers la [propriété BufferedGraphics.Graphics](frlrfSystemDrawingBufferedGraphicsClassGraphicsTopic), laquelle expose un objet <xref:System.Drawing.Graphics> qui représente directement la mémoire tampon.  Vous pouvez peindre sur cet objet <xref:System.Drawing.Graphics> comme vous le feriez sur un objet <xref:System.Drawing.Graphics> qui représente une surface de dessin.  Après que tous les graphiques ont été dessinés dans la mémoire tampon, vous pouvez utiliser la [méthode BufferedGraphics.Render](frlrfSystemDrawingBufferedGraphicsClassRenderTopic) pour copier le contenu de la mémoire tampon vers la surface de dessin sur l'écran.  
  
 Pour plus d'informations sur l'utilisation de la classe <xref:System.Drawing.BufferedGraphics>, consultez [Rendu manuel des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md).  Pour plus d'informations sur le rendu de graphiques, consultez [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
  
## Voir aussi  
 <xref:System.Drawing.BufferedGraphics>   
 <xref:System.Drawing.BufferedGraphicsContext>   
 <xref:System.Drawing.BufferedGraphicsManager>   
 [Comment : restituer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)   
 [Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)   
 [Comment : gérer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)