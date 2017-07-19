---
title: "Comment&#160;: r&#233;duire le scintillement des graphiques &#224; l&#39;aide du m&#233;canisme de double tampon pour les formulaires et les contr&#244;les | Microsoft Docs"
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
  - "DoubleBuffered (propriété)"
  - "scintillement, réduire dans les Windows Forms"
  - "graphiques, réduire le scintillement des doubles tampons"
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: r&#233;duire le scintillement des graphiques &#224; l&#39;aide du m&#233;canisme de double tampon pour les formulaires et les contr&#244;les
Le mécanisme de double tampon utilise une mémoire tampon pour traiter les problèmes de scintillement associés aux opérations de peinture multiples.  Lorsque le mécanisme de double tampon est activé, toutes les opérations de peinture sont restituées en premier à une mémoire tampon à la place de la surface de dessin sur l'écran.  Après avoir effectué toutes les opérations de peinture, la mémoire tampon est copiée directement vers la surface de dessin qui lui est associée.  Étant donné qu'une opération de graphiques est exécutée sur l'écran, il élimine le scintillement d'image associé avec des opérations de peinture complexes. Pour la plupart des applications, le mécanisme de double tampon par défaut fourni par le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fournissent les meilleurs résultats.  Les contrôles Windows Forms standard sont copiés dans le double tampon par défaut.  Vous pouvez activer de deux façons le mécanisme de double tampon par défaut dans vos formulaires et contrôles créés.  Vous pouvez attribuer à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true`, ou appeler la méthode <xref:System.Windows.Forms.Control.SetStyle%2A> pour affecter à l'indicateur <xref:System.Windows.Forms.ControlStyles> la valeur `true`.  Les deux méthodes activeront le mécanisme de double tampon par défaut pour votre formulaire ou contrôle et fourniront le rendu graphique sans scintillement.  L'appel de la méthode <xref:System.Windows.Forms.Control.SetStyle%2A> est recommandé uniquement pour les contrôles personnalisés pour lesquels vous avez écrit tout le code de rendu.  
  
 Pour des scénarios de mécanisme de double tampon plus avancés, tels que l'animation ou la gestion de mémoire avancée, vous pouvez implémenter votre propre logique de mécanisme de double tampon.  Pour plus d'informations, consultez [Comment : gérer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
### Pour réduire le scintillement  
  
-   Affectez à la propriété <xref:System.Windows.Forms.Control.DoubleBuffered%2A> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- ou \-  
  
-   Appelez la méthode <xref:System.Windows.Forms.Control.SetStyle%2A> pour affecter à l'indicateur <xref:System.Windows.Forms.ControlStyles> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>   
 <xref:System.Windows.Forms.Control.SetStyle%2A>   
 [Graphiques mis deux fois en mémoire tampon](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)