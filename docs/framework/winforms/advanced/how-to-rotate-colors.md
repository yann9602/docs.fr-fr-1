---
title: "Comment : faire pivoter des couleurs"
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
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81b022011bd5613b8e956aa83482d2836508a4f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="5f4ad-102">Comment : faire pivoter des couleurs</span><span class="sxs-lookup"><span data-stu-id="5f4ad-102">How to: Rotate Colors</span></span>
<span data-ttu-id="5f4ad-103">Rotation dans un espace de couleurs à quatre dimensions est difficile de visualiser.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="5f4ad-104">Nous pouvons facilitent la visualisation, choisissez de conserver un des composants de couleur fixe.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="5f4ad-105">Supposons que nous acceptons de conserver le composant alpha est fixé à 1 (entièrement opaque).</span><span class="sxs-lookup"><span data-stu-id="5f4ad-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="5f4ad-106">Vous pouvez ensuite visualiser un espace à trois dimensions de couleur des axes de rouges, verts et bleus, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="5f4ad-107">![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="5f4ad-107">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="5f4ad-108">Une couleur peut être considérée comme un point dans un espace 3D.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="5f4ad-109">Par exemple, le point (1, 0, 0) dans l’espace représente la couleur rouge, et le point (0, 1, 0) dans l’espace représente la couleur verte.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="5f4ad-110">L’illustration suivante montre ce que cela signifie pour faire pivoter la couleur (1, 0, 0) via un angle de 60 degrés dans le plan rouge-vert.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="5f4ad-111">Rotation d’un plan parallèle au plan rouge-vert peut être considérée comme une rotation sur l’axe bleu.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="5f4ad-112">![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="5f4ad-112">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="5f4ad-113">L’illustration suivante montre comment initialiser une matrice de couleurs pour effectuer des rotations sur chacun des trois axes de coordonnées (rouge, vert, bleu).</span><span class="sxs-lookup"><span data-stu-id="5f4ad-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="5f4ad-114">![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="5f4ad-114">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f4ad-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f4ad-115">Example</span></span>  
 <span data-ttu-id="5f4ad-116">L’exemple suivant prend une image qui est une couleur (1, 0, 0.6) et applique une rotation de 60 degrés sur l’axe bleu.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="5f4ad-117">L’angle de rotation est rangé dans un plan parallèle au plan rouge-vert.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="5f4ad-118">L’illustration suivante montre l’image d’origine sur la gauche et l’image pivotée de couleur sur la droite.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="5f4ad-119">![Faire pivoter des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="5f4ad-119">![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="5f4ad-120">L’illustration suivante montre une visualisation de la rotation de couleurs effectuée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="5f4ad-121">![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="5f4ad-121">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f4ad-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5f4ad-122">Compiling the Code</span></span>  
 <span data-ttu-id="5f4ad-123">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="5f4ad-124">Remplacez `RotationInput.bmp` avec un nom de fichier image et le chemin d’accès valide sur votre système.</span><span class="sxs-lookup"><span data-stu-id="5f4ad-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4ad-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f4ad-125">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="5f4ad-126">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f4ad-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="5f4ad-127">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="5f4ad-127">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
