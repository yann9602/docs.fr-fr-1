---
title: "Comment : remplir des figures ouvertes"
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c020e5f7306e73ee97dff0b492b04b5a153059cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-open-figures"></a>Comment : remplir des figures ouvertes
Vous pouvez remplir un chemin d’accès en passant un <xref:System.Drawing.Drawing2D.GraphicsPath> de l’objet à le <xref:System.Drawing.Graphics.FillPath%2A> (méthode). Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage (de substitution ou enroulement) actuellement défini pour le chemin d’accès. Si le chemin d’accès comporte des figures ouvertes, le chemin d’accès est rempli comme si ces figures étaient fermées. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]ferme une figure en dessinant une ligne droite à partir de son point d’arrivée à son point de départ.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un chemin d’accès qui a une figure ouverte (un arc) et une figure fermée (une ellipse). Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage par défaut, qui est <xref:System.Drawing.Drawing2D.FillMode.Alternate>.  
  
 L’illustration suivante montre la sortie de l’exemple de code. Notez que le chemin d’accès est rempli (conformément à <xref:System.Drawing.Drawing2D.FillMode.Alternate>) comme si la figure ouverte était fermée par une ligne droite à partir de son point de fin à son point de départ.  
  
 ![Remplir le tracé ouvert](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [Tracés graphiques dans GDI+](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
