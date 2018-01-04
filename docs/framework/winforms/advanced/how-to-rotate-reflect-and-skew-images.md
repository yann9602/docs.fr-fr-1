---
title: "Comment : faire pivoter, refléter et incliner des images"
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
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 163af74d27adcb7ec720a54bfd969bd704f7b1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="53fd8-102">Comment : faire pivoter, refléter et incliner des images</span><span class="sxs-lookup"><span data-stu-id="53fd8-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="53fd8-103">Vous pouvez faire pivoter, refléter et incliner une image en spécifiant des points de destination pour les angles supérieur gauche, supérieur droit et inférieur gauche de l’image d’origine.</span><span class="sxs-lookup"><span data-stu-id="53fd8-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="53fd8-104">Les trois points de destination déterminent une transformation affine qui mappe l’image rectangulaire d’origine à un parallélogramme.</span><span class="sxs-lookup"><span data-stu-id="53fd8-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53fd8-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="53fd8-105">Example</span></span>  
 <span data-ttu-id="53fd8-106">Par exemple, supposons que l’image d’origine est un rectangle avec le coin supérieur gauche à (0, 0), coin supérieur droit à (100, 0) et l’angle inférieur gauche à (0, 50).</span><span class="sxs-lookup"><span data-stu-id="53fd8-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="53fd8-107">Supposons maintenant vous mappiez ces trois points aux points de destination comme suit.</span><span class="sxs-lookup"><span data-stu-id="53fd8-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="53fd8-108">Point d’origine</span><span class="sxs-lookup"><span data-stu-id="53fd8-108">Original point</span></span>|<span data-ttu-id="53fd8-109">Point de destination</span><span class="sxs-lookup"><span data-stu-id="53fd8-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="53fd8-110">Angle supérieur gauche (0, 0)</span><span class="sxs-lookup"><span data-stu-id="53fd8-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="53fd8-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="53fd8-111">(200, 20)</span></span>|  
|<span data-ttu-id="53fd8-112">Coin supérieur droit (100, 0)</span><span class="sxs-lookup"><span data-stu-id="53fd8-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="53fd8-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="53fd8-113">(110, 100)</span></span>|  
|<span data-ttu-id="53fd8-114">Inférieur gauche (0, 50)</span><span class="sxs-lookup"><span data-stu-id="53fd8-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="53fd8-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="53fd8-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="53fd8-116">L’illustration suivante montre l’image d’origine et l’image mappée au parallélogramme.</span><span class="sxs-lookup"><span data-stu-id="53fd8-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="53fd8-117">L’image d’origine ont été inégale, reflétée, pivoté et traduit.</span><span class="sxs-lookup"><span data-stu-id="53fd8-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="53fd8-118">L’axe des abscisses le long du bord supérieur de l’image d’origine sont mappé à la ligne traversant (200, 20) et (110, 100).</span><span class="sxs-lookup"><span data-stu-id="53fd8-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="53fd8-119">L’axe des y le long du bord gauche de l’image d’origine sont mappé à la ligne traversant (200, 20) et (250, 30).</span><span class="sxs-lookup"><span data-stu-id="53fd8-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="53fd8-120">![Bandes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="53fd8-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="53fd8-121">L’illustration suivante montre une transformation similaire appliquée à une image photographique.</span><span class="sxs-lookup"><span data-stu-id="53fd8-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="53fd8-122">![Transformés Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="53fd8-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="53fd8-123">L’illustration suivante montre une transformation similaire appliquée à un métafichier.</span><span class="sxs-lookup"><span data-stu-id="53fd8-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="53fd8-124">![Transformés métafichier](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="53fd8-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="53fd8-125">L’exemple suivant produit les images présentées dans la première illustration.</span><span class="sxs-lookup"><span data-stu-id="53fd8-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53fd8-126">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="53fd8-126">Compiling the Code</span></span>  
 <span data-ttu-id="53fd8-127">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="53fd8-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="53fd8-128">Veillez à remplacer `Stripes.bmp` avec le chemin d’accès à une image qui est valide sur votre système.</span><span class="sxs-lookup"><span data-stu-id="53fd8-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fd8-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53fd8-129">See Also</span></span>  
 [<span data-ttu-id="53fd8-130">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="53fd8-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
