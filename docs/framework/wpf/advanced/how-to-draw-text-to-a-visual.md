---
title: "Comment : ajouter du texte à un Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 735a84a034587b1433403a45edc7c2f459340273
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-text-to-a-visual"></a>Comment : ajouter du texte à un Visual
L’exemple suivant montre comment dessiner du texte à un <xref:System.Windows.Media.DrawingVisual> à l’aide un <xref:System.Windows.Media.DrawingContext> objet. Un contexte de dessin est retourné en appelant le <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> méthode d’un <xref:System.Windows.Media.DrawingVisual> objet. Vous pouvez dessiner des graphiques et du texte dans un contexte de dessin.  
  
 Pour dessiner le texte dans le contexte de dessin, utilisez la <xref:System.Windows.Media.DrawingContext.DrawText%2A> méthode d’un <xref:System.Windows.Media.DrawingContext> objet. Lorsque vous avez terminé de dessiner le contenu dans le contexte de dessin, appelez le <xref:System.Windows.Media.DrawingContext.Close%2A> méthode pour fermer le contexte de dessin et de conserver le contenu.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](http://go.microsoft.com/fwlink/?LinkID=159994) (Test de positionnement à l’aide d’exemples de DrawingVisuals).
