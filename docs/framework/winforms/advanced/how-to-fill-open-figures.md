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
ms.openlocfilehash: 7a8a2d5a13cac97063bf2a04969928c859a5954d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="8ab9e-102">Comment : remplir des figures ouvertes</span><span class="sxs-lookup"><span data-stu-id="8ab9e-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="8ab9e-103">Vous pouvez remplir un chemin d’accès en passant un <xref:System.Drawing.Drawing2D.GraphicsPath> de l’objet à le <xref:System.Drawing.Graphics.FillPath%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="8ab9e-104">Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage (de substitution ou enroulement) actuellement défini pour le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="8ab9e-105">Si le chemin d’accès comporte des figures ouvertes, le chemin d’accès est rempli comme si ces figures étaient fermées.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="8ab9e-106">ferme une figure en dessinant une ligne droite à partir de son point d’arrivée à son point de départ.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab9e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ab9e-107">Example</span></span>  
 <span data-ttu-id="8ab9e-108">L’exemple suivant crée un chemin d’accès qui a une figure ouverte (un arc) et une figure fermée (une ellipse).</span><span class="sxs-lookup"><span data-stu-id="8ab9e-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="8ab9e-109">Le <xref:System.Drawing.Graphics.FillPath%2A> méthode remplit le chemin d’accès selon le mode de remplissage par défaut, qui est <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="8ab9e-110">L’illustration suivante montre la sortie de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="8ab9e-111">Notez que le chemin d’accès est rempli (conformément à <xref:System.Drawing.Drawing2D.FillMode.Alternate>) comme si la figure ouverte était fermée par une ligne droite à partir de son point de fin à son point de départ.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="8ab9e-112">![Remplir le tracé ouvert](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="8ab9e-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ab9e-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8ab9e-113">Compiling the Code</span></span>  
 <span data-ttu-id="8ab9e-114">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="8ab9e-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab9e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ab9e-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="8ab9e-116">Tracés graphiques dans GDI+</span><span class="sxs-lookup"><span data-stu-id="8ab9e-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
