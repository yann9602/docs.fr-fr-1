---
title: "Comment : utiliser le mode de composition pour commander la fusion alpha"
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
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564d46cb2d72ac63962657b39146489aaafd6a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="709fb-102">Comment : utiliser le mode de composition pour commander la fusion alpha</span><span class="sxs-lookup"><span data-stu-id="709fb-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="709fb-103">Il peut arriver lorsque vous souhaitez créer une bitmap hors écran ayant les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="709fb-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="709fb-104">Les couleurs ont les valeurs alphanumériques inférieur à 255.</span><span class="sxs-lookup"><span data-stu-id="709fb-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="709fb-105">Couleurs ne sont pas alphanumériques fusionnés entre eux que vous créez l’image bitmap.</span><span class="sxs-lookup"><span data-stu-id="709fb-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="709fb-106">Lorsque vous affichez la bitmap terminée, les couleurs de la bitmap sont fusionnée alpha avec les couleurs d’arrière-plan sur le périphérique d’affichage.</span><span class="sxs-lookup"><span data-stu-id="709fb-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="709fb-107">Pour créer une telle bitmap, construisez un espace <xref:System.Drawing.Bitmap> de l’objet et à construire un <xref:System.Drawing.Graphics> objet basé sur cette bitmap.</span><span class="sxs-lookup"><span data-stu-id="709fb-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="709fb-108">Le mode de composition de la <xref:System.Drawing.Graphics> objet <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="709fb-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="709fb-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="709fb-109">Example</span></span>  
 <span data-ttu-id="709fb-110">L’exemple suivant crée un <xref:System.Drawing.Graphics> objet basé sur un <xref:System.Drawing.Bitmap> objet.</span><span class="sxs-lookup"><span data-stu-id="709fb-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="709fb-111">Le code utilise le <xref:System.Drawing.Graphics> objet, ainsi que deux pinceaux translucides (alpha = 160) pour peindre sur la bitmap.</span><span class="sxs-lookup"><span data-stu-id="709fb-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="709fb-112">Le code remplit une ellipse rouge et une ellipse verte en utilisant des pinceaux translucides.</span><span class="sxs-lookup"><span data-stu-id="709fb-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="709fb-113">L’ellipse verte chevauche l’ellipse rouge, mais le vert n’est pas fusionnée avec la croix rouge, car le mode de composition le <xref:System.Drawing.Graphics> objet a la valeur <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="709fb-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="709fb-114">Le code dessine l’image bitmap à l’écran à deux reprises : une fois sur un arrière-plan blanc et qu’une seule fois sur un arrière-plan multicolore.</span><span class="sxs-lookup"><span data-stu-id="709fb-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="709fb-115">Les pixels dans la bitmap qui font partie des deux ellipses ont un composant alpha de 160, pour les points de suspension sont fusionnés avec les couleurs d’arrière-plan sur l’écran.</span><span class="sxs-lookup"><span data-stu-id="709fb-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="709fb-116">L’illustration suivante montre la sortie de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="709fb-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="709fb-117">Notez que les points de suspension sont fusionnés avec l’arrière-plan, mais ils ne sont pas fusionnés entre eux.</span><span class="sxs-lookup"><span data-stu-id="709fb-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 <span data-ttu-id="709fb-118">![Source de copie](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span><span class="sxs-lookup"><span data-stu-id="709fb-118">![Source Copy](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span></span>  
  
 <span data-ttu-id="709fb-119">L’exemple de code contient cette instruction :</span><span class="sxs-lookup"><span data-stu-id="709fb-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="709fb-120">Si vous souhaitez que les points de suspension pour être fusionnés entre eux ainsi qu’avec l’arrière-plan, modifiez cette instruction comme suit :</span><span class="sxs-lookup"><span data-stu-id="709fb-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="709fb-121">L’illustration suivante montre la sortie du code révisé.</span><span class="sxs-lookup"><span data-stu-id="709fb-121">The following illustration shows the output of the revised code.</span></span>  
  
 <span data-ttu-id="709fb-122">![Sur la source](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span><span class="sxs-lookup"><span data-stu-id="709fb-122">![Source Over](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="709fb-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="709fb-123">Compiling the Code</span></span>  
 <span data-ttu-id="709fb-124">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="709fb-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709fb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="709fb-125">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="709fb-126">Fusion alpha de lignes et de remplissages</span><span class="sxs-lookup"><span data-stu-id="709fb-126">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
