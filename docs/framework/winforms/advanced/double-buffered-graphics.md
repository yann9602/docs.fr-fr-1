---
title: "Graphiques mis deux fois en mémoire tampon"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7e4445b0a729eb1f826d17340db02f0c56149b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="double-buffered-graphics"></a>Graphiques mis deux fois en mémoire tampon
Le scintillement est un problème courant lors de la programmation de graphiques. Les opérations graphiques qui nécessitent plusieurs opérations de dessin complexes peuvent provoquer le scintillement du rendu des images ou une apparence qui n’est pas acceptable. Pour résoudre ces problèmes, le .NET Framework fournit un accès à la double mise en mémoire tampon.  
  
 La double mise en mémoire tampon utilise une mémoire tampon pour résoudre les problèmes de scintillement associés aux opérations de dessin multiples. Quand la double mise en mémoire tampon est activée, toutes les opérations de dessin sont d’abord rendues dans une mémoire tampon au lieu de l’être sur la surface de dessin à l’écran. Une fois que toutes les opérations de dessin sont terminées, la mémoire tampon est copiée directement sur la surface de dessin qui y est associée. Comme une seule opération de dessin est effectuée sur l’écran, le scintillement de l’image associé aux opérations de dessin complexes est éliminé.  
  
## <a name="default-double-buffering"></a>Doubles mise en mémoire tampon par défaut  
 La façon la plus simple d’utiliser la double mise en mémoire tampon dans vos applications consiste à utiliser la double mise en mémoire tampon par défaut pour les formulaires et les contrôles qui est fournie par le .NET Framework. Vous pouvez activer la double mise en mémoire tampon pour vos formulaires Windows par défaut et contrôles Windows créés en définissant le <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriété `true` ou à l’aide de la <xref:System.Windows.Forms.Control.SetStyle%2A> (méthode). Pour plus d’informations, consultez [Guide pratique pour réduire le scintillement des graphiques à l’aide du mécanisme de double mise en mémoire tampon pour les formulaires et les contrôles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Gestion manuelle des graphiques mis en mémoire tampon  
 Pour des scénarios plus avancés de double mise en mémoire tampon, comme l’animation ou la gestion avancée de la mémoire, vous pouvez utiliser les classes .NET Framework pour implémenter votre propre logique de double mise en mémoire tampon. La classe chargée de l’allocation et la gestion des mémoires tampon de graphiques individuelles est la <xref:System.Drawing.BufferedGraphicsContext> classe. Chaque domaine d’application a sa propre valeur par défaut <xref:System.Drawing.BufferedGraphicsContext> instance qui gère toutes la valeur par défaut est de double tampon pour cette application. Dans la plupart des cas il y aura qu’un seul domaine d’application par application, il est généralement une valeur par défaut <xref:System.Drawing.BufferedGraphicsContext> par application. Par défaut <xref:System.Drawing.BufferedGraphicsContext> instances sont gérées par la <xref:System.Drawing.BufferedGraphicsManager> classe. Vous pouvez récupérer une référence à la valeur par défaut <xref:System.Drawing.BufferedGraphicsContext> instance en appelant le <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Vous pouvez également créer une dédiée <xref:System.Drawing.BufferedGraphicsContext> instance, ce qui peut améliorer les performances des applications graphiques. Pour plus d’informations sur la création d’un <xref:System.Drawing.BufferedGraphicsContext> une instance, consultez [Comment : gérer manuellement mis en mémoire tampon des graphiques](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Affichage manuel de graphiques mis en mémoire tampon  
 Vous pouvez utiliser une instance de la <xref:System.Drawing.BufferedGraphicsContext> classe pour créer des mémoires tampon de graphiques en appelant le <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, qui retourne une instance de la <xref:System.Drawing.BufferedGraphics> classe. A <xref:System.Drawing.BufferedGraphics> objet gère une mémoire tampon qui est associée à une surface de rendu, comme un formulaire ou un contrôle.  
  
 Une fois qu’il est instancié, le <xref:System.Drawing.BufferedGraphics> classe gère le rendu dans une mémoire tampon de graphiques de la mémoire. Vous pouvez restituer des graphiques à la mémoire tampon par le biais du <xref:System.Drawing.BufferedGraphics.Graphics%2A>, qui expose un <xref:System.Drawing.Graphics> objet qui représente directement la mémoire tampon. Vous pouvez peindre sur cet <xref:System.Drawing.Graphics> de l’objet comme vous le feriez pour un <xref:System.Drawing.Graphics> objet qui représente une surface de dessin. Une fois que tous les graphiques ont été dessinés dans la mémoire tampon, vous pouvez utiliser la <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> pour copier le contenu de la mémoire tampon vers la surface de dessin à l’écran.  
  
 Pour plus d’informations sur l’utilisation de la <xref:System.Drawing.BufferedGraphics> de classe, consultez [manuellement de rendu des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md). Pour plus d’informations sur le rendu de graphiques, consultez [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [Guide pratique pour restituer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [Guide pratique pour réduire le scintillement des graphiques à l’aide de la double mise en mémoire tampon pour les formulaires et les contrôles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [Guide pratique pour gérer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
