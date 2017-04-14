---
title: "Comment&#160;: g&#233;rer manuellement des graphiques mis en m&#233;moire tampon | Microsoft Docs"
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
  - "BufferedGraphicsContext (classe)"
  - "scintillement, réduire en gérant manuellement les graphiques"
  - "graphiques, gérer les graphiques mis en mémoire tampon"
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: g&#233;rer manuellement des graphiques mis en m&#233;moire tampon
Pour des scénarios de double mise en mémoire tampon plus avancés, utilisez les classes [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour implémenter votre propre logique de double mise en mémoire tampon.  La classe responsable de l'allocation et de la gestion des mémoires tampon de graphiques individuelles est la classe <xref:System.Drawing.BufferedGraphicsContext>.  Chaque application a son propre <xref:System.Drawing.BufferedGraphicsContext> par défaut qui gère tout le mécanisme de double tampon par défaut pour cette application.  Vous pouvez récupérer une référence à cette instance en appelant le <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### Pour obtenir une référence au BufferedGraphicsContext par défaut  
  
-   Utilisez la propriété <xref:System.Drawing.BufferedGraphicsManager.Current%2A>, comme le montre l'exemple de code ci\-dessous.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Vous n'avez pas besoin d'appeler la méthode `Dispose` sur la référence <xref:System.Drawing.BufferedGraphicsContext> que vous recevez de la classe <xref:System.Drawing.BufferedGraphicsManager>.  Le <xref:System.Drawing.BufferedGraphicsManager> gère toute l'allocation de mémoire et la distribution pour les instances de <xref:System.Drawing.BufferedGraphicsContext> par défaut.  
  
     Pour les applications à forte intensité graphique telles que les animations, vous pouvez parfois améliorer les performances en utilisant un <xref:System.Drawing.BufferedGraphicsContext> dédié à la place du <xref:System.Drawing.BufferedGraphicsContext> fourni par <xref:System.Drawing.BufferedGraphicsManager>.  Cela vous permet de créer et de gérer des mémoires tampon de graphiques individuellement, sans la baisse des performances liée à la gestion de tous les autres graphiques mis en mémoire tampon et associés à votre application, même si la mémoire consommée par l'application sera supérieure.  
  
### Pour créer un BufferedGraphicsContext dédié  
  
-   Déclarez et créez une nouvelle instance de la classe <xref:System.Drawing.BufferedGraphicsContext>, comme illustré dans l'exemple de code suivant.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## Voir aussi  
 <xref:System.Drawing.BufferedGraphicsContext>   
 [Graphiques mis deux fois en mémoire tampon](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [Comment : restituer manuellement des graphiques mis en mémoire tampon](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)