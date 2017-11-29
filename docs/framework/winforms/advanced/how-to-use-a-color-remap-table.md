---
title: "Comment : utiliser une table de remappage des couleurs"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c4399e98504a675cfbf63462b8dc964c677488e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="23d53-102">Comment : utiliser une table de remappage des couleurs</span><span class="sxs-lookup"><span data-stu-id="23d53-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="23d53-103">Le remappage est le processus de conversion des couleurs dans une image en fonction d’une table de remappage des couleurs.</span><span class="sxs-lookup"><span data-stu-id="23d53-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="23d53-104">La table de remappage des couleurs est un tableau de <xref:System.Drawing.Imaging.ColorMap> objets.</span><span class="sxs-lookup"><span data-stu-id="23d53-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="23d53-105">Chaque <xref:System.Drawing.Imaging.ColorMap> objet dans le tableau a une <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> propriété et un <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="23d53-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="23d53-106">Lorsque [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Dessine une image, chaque pixel de l’image est comparé au tableau des anciennes couleurs.</span><span class="sxs-lookup"><span data-stu-id="23d53-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="23d53-107">Si de la couleur d’un pixel correspond à une ancienne couleur, sa couleur est remplacée par la nouvelle couleur correspondante.</span><span class="sxs-lookup"><span data-stu-id="23d53-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="23d53-108">Les couleurs sont modifiées uniquement pour le rendu, les valeurs de couleur de l’image elle-même (stockées dans un <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objet) ne sont pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="23d53-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="23d53-109">Pour dessiner une image remappée, initialisez un tableau de <xref:System.Drawing.Imaging.ColorMap> objets.</span><span class="sxs-lookup"><span data-stu-id="23d53-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="23d53-110">Passer ce tableau à la <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> méthode d’un <xref:System.Drawing.Imaging.ImageAttributes> de l’objet, puis passer la <xref:System.Drawing.Imaging.ImageAttributes> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="23d53-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d53-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="23d53-111">Example</span></span>  
 <span data-ttu-id="23d53-112">L’exemple suivant crée un <xref:System.Drawing.Image> objet à partir du fichier RemapInput.bmp.</span><span class="sxs-lookup"><span data-stu-id="23d53-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="23d53-113">Le code crée une table de remappage des couleurs qui se compose d’un seul <xref:System.Drawing.Imaging.ColorMap> objet.</span><span class="sxs-lookup"><span data-stu-id="23d53-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="23d53-114">Le <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> propriété de la `ColorRemap` objet est rouge et le <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> propriété est bleue.</span><span class="sxs-lookup"><span data-stu-id="23d53-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="23d53-115">L’image est dessinée une fois sans le remappage et une autre fois avec le remappage.</span><span class="sxs-lookup"><span data-stu-id="23d53-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="23d53-116">Le processus de remappage modifie tous les pixels rouges bleu.</span><span class="sxs-lookup"><span data-stu-id="23d53-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="23d53-117">L’illustration suivante montre l’image d’origine sur la gauche et l’image remappée sur la droite.</span><span class="sxs-lookup"><span data-stu-id="23d53-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="23d53-118">![Remappage des couleurs](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="23d53-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23d53-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="23d53-119">Compiling the Code</span></span>  
 <span data-ttu-id="23d53-120">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="23d53-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d53-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23d53-121">See Also</span></span>  
 [<span data-ttu-id="23d53-122">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="23d53-122">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="23d53-123">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="23d53-123">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
