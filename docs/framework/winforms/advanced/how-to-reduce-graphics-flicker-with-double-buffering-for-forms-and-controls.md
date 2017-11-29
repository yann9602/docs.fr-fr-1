---
title: "Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d1b22babcc653f999ff500a5e52a12616fc1ae4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Comment : réduire le scintillement des graphiques à l'aide du mécanisme de double tampon pour les formulaires et les contrôles
La double mise en mémoire tampon utilise une mémoire tampon pour résoudre les problèmes de scintillement associés aux opérations de dessin multiples. Quand la double mise en mémoire tampon est activée, toutes les opérations de dessin sont d’abord rendues dans une mémoire tampon au lieu de l’être sur la surface de dessin à l’écran. Une fois que toutes les opérations de dessin sont terminées, la mémoire tampon est copiée directement sur la surface de dessin qui y est associée. Les graphiques qu’une seule opération sur l’écran, le scintillement d’image associé aux opérations de peinture complexes est éliminé. Pour la plupart des applications, le double tampon par défaut fourni par le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournissent les meilleurs résultats. Contrôles Windows Forms standard sont doubles tampon par défaut. Vous pouvez activer la double mise en mémoire tampon dans les formulaires par défaut et créé des contrôles de deux manières. Vous pouvez soit définir la <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriété `true`, ou vous pouvez appeler la <xref:System.Windows.Forms.Control.SetStyle%2A> pour définir le <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> indicateur `true`. Les deux méthodes Active double tampon par défaut pour votre formulaire ou contrôle et fournir un rendu graphique sans scintillement. Appel de la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode est recommandée uniquement pour les contrôles personnalisés pour lequel vous avez écrit tout le code de rendu.  
  
 Pour les scénarios doubles mise en mémoire tampon plus avancés, tels que l’animation ou la gestion de mémoire avancée, vous pouvez implémenter votre propre logique de mise en mémoire tampon double. Pour plus d’informations, consultez [Comment : gérer manuellement mis en mémoire tampon des graphiques](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Pour réduire le scintillement  
  
-   Affectez à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- ou -  
  
-   Appelez le <xref:System.Windows.Forms.Control.SetStyle%2A> pour définir le <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> indicateur `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [Graphiques mis deux fois en mémoire tampon](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
