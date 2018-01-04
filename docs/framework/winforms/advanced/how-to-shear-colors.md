---
title: "Comment : altérer des couleurs"
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
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a32e6c1901f84c276c071402dac641d45566717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="2096a-102">Comment : altérer des couleurs</span><span class="sxs-lookup"><span data-stu-id="2096a-102">How to: Shear Colors</span></span>
<span data-ttu-id="2096a-103">Inclinaison augmente ou diminue d’un composant de couleur d’un montant proportionnel à un autre composant de couleur.</span><span class="sxs-lookup"><span data-stu-id="2096a-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="2096a-104">Par exemple, considérez la transformation où la composante rouge est augmentée par la moitié de la valeur du composant bleu.</span><span class="sxs-lookup"><span data-stu-id="2096a-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="2096a-105">Sous une transformation de ce type, la couleur (0,2, 0,5, 1) deviendrait (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="2096a-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="2096a-106">Le nouveau composant rouge est 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="2096a-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2096a-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2096a-107">Example</span></span>  
 <span data-ttu-id="2096a-108">L’exemple suivant construit une <xref:System.Drawing.Image> objet à partir du fichier ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="2096a-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="2096a-109">Le code applique ensuite la transformation d’inclinaison décrite dans le paragraphe précédent à chaque pixel de l’image.</span><span class="sxs-lookup"><span data-stu-id="2096a-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="2096a-110">L’illustration suivante montre l’image d’origine sur la gauche et l’image inclinée sur la droite.</span><span class="sxs-lookup"><span data-stu-id="2096a-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="2096a-111">![Cisaillement des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="2096a-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="2096a-112">Le tableau suivant répertorie les vecteurs de couleur pour les quatre barres avant et après la transformation d’inclinaison.</span><span class="sxs-lookup"><span data-stu-id="2096a-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="2096a-113">D'origine</span><span class="sxs-lookup"><span data-stu-id="2096a-113">Original</span></span>|<span data-ttu-id="2096a-114">Inclinée</span><span class="sxs-lookup"><span data-stu-id="2096a-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2096a-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="2096a-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="2096a-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="2096a-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="2096a-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="2096a-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="2096a-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="2096a-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="2096a-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2096a-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2096a-123">Compiling the Code</span></span>  
 <span data-ttu-id="2096a-124">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="2096a-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="2096a-125">Remplacez `ColorBars.bmp` avec un nom de l’image et le chemin d’accès valide sur votre système.</span><span class="sxs-lookup"><span data-stu-id="2096a-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2096a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2096a-126">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="2096a-127">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2096a-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="2096a-128">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="2096a-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
