---
title: "Comment : utiliser une matrice de couleurs pour transformer une couleur unique"
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
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60da29b60d2b9b5b98c76a0a9c3ae73ac9142bbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="8921d-102">Comment : utiliser une matrice de couleurs pour transformer une couleur unique</span><span class="sxs-lookup"><span data-stu-id="8921d-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="8921d-103">Fournit la <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> classes pour le stockage et la manipulation d’images.</span><span class="sxs-lookup"><span data-stu-id="8921d-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="8921d-104"><xref:System.Drawing.Image>et <xref:System.Drawing.Bitmap> objets stockent la couleur de chaque pixel comme un nombre 32 bits : 8 bits pour le rouge, vert, bleu et alpha.</span><span class="sxs-lookup"><span data-stu-id="8921d-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="8921d-105">Chacun des quatre composants est un nombre compris entre 0 et 255, où 0 représente aucune intensité et une intensité maximale de 255.</span><span class="sxs-lookup"><span data-stu-id="8921d-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="8921d-106">Le composant alpha spécifie la transparence de la couleur : 0 est totalement transparent et 255 est complètement opaque.</span><span class="sxs-lookup"><span data-stu-id="8921d-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="8921d-107">Un vecteur de couleur est un 4-tuple de forme (rouge, vert, bleu, alpha).</span><span class="sxs-lookup"><span data-stu-id="8921d-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="8921d-108">Par exemple, le vecteur de couleur (0, 255, 0, 255) représente une couleur opaque qui n’a ni rouge bleu, mais a vert à intensité complète.</span><span class="sxs-lookup"><span data-stu-id="8921d-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="8921d-109">Une autre convention de représentation des couleurs utilise le numéro 1 pour l’intensité maximale.</span><span class="sxs-lookup"><span data-stu-id="8921d-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="8921d-110">À l’aide de cette convention, la couleur décrite dans le paragraphe précédent va être représentée par le vecteur (0, 1, 0, 1).</span><span class="sxs-lookup"><span data-stu-id="8921d-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="8921d-111">utilise la convention de 1 comme intensité complète lorsqu’il exécute des transformations de couleur.</span><span class="sxs-lookup"><span data-stu-id="8921d-111"> uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="8921d-112">Vous pouvez appliquer des transformations linéaires (rotation, mise à l’échelle, etc.) aux vecteurs de couleurs en multipliant ces vecteurs par une matrice 4 × 4.</span><span class="sxs-lookup"><span data-stu-id="8921d-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="8921d-113">Toutefois, vous ne pouvez pas utiliser une matrice 4 × 4 pour effectuer une traduction (non linéaire).</span><span class="sxs-lookup"><span data-stu-id="8921d-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="8921d-114">Si vous ajoutez une cinquième coordonnée fictive (par exemple, le nombre 1) à chaque vecteur de couleur, vous pouvez utiliser une matrice 5 x 5 pour appliquer des combinaisons de transformations linéaires et les traductions.</span><span class="sxs-lookup"><span data-stu-id="8921d-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="8921d-115">Une transformation comprenant une transformation linéaire suivie d’une traduction est appelée une transformation affine.</span><span class="sxs-lookup"><span data-stu-id="8921d-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="8921d-116">Par exemple, supposons que vous souhaitez démarrer avec la couleur (0.2, 0.0, 0,4, 1.0) et appliquer les transformations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8921d-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="8921d-117">Doubler la composante rouge</span><span class="sxs-lookup"><span data-stu-id="8921d-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="8921d-118">Ajouter 0,2 aux composants rouges, verts et bleus</span><span class="sxs-lookup"><span data-stu-id="8921d-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="8921d-119">La multiplication des matrices suivante va effectuer la paire de transformations dans l’ordre indiqué.</span><span class="sxs-lookup"><span data-stu-id="8921d-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="8921d-120">![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="8921d-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="8921d-121">Les éléments d’une matrice de couleurs sont indexés (base zéro) par ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="8921d-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="8921d-122">Par exemple, l’entrée dans la cinquième ligne et la troisième colonne de la matrice M est représentée par M [4] [2].</span><span class="sxs-lookup"><span data-stu-id="8921d-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="8921d-123">La matrice d’identité 5 x 5 (indiqué dans l’illustration suivante) a 1 sur la diagonale et 0 partout ailleurs.</span><span class="sxs-lookup"><span data-stu-id="8921d-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="8921d-124">Si vous multipliez un vecteur de couleur par la matrice d’identité, le vecteur de couleur ne change pas.</span><span class="sxs-lookup"><span data-stu-id="8921d-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="8921d-125">Un moyen pratique de former la matrice d’une transformation de couleur consiste à commencer par la matrice d’identité et d’apporter une petite modification qui produit la transformation souhaitée.</span><span class="sxs-lookup"><span data-stu-id="8921d-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="8921d-126">![Recoloriage](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="8921d-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="8921d-127">Pour obtenir une présentation plus détaillée des matrices et des transformations, consultez [systèmes de coordonnées et Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="8921d-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8921d-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="8921d-128">Example</span></span>  
 <span data-ttu-id="8921d-129">L’exemple suivant prend une image qui est une couleur (0.2, 0.0, 0,4, 1.0) et applique la transformation décrite dans les paragraphes précédents.</span><span class="sxs-lookup"><span data-stu-id="8921d-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="8921d-130">L’illustration suivante montre l’image d’origine sur la gauche et l’image transformée sur la droite.</span><span class="sxs-lookup"><span data-stu-id="8921d-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="8921d-131">![Couleurs](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="8921d-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="8921d-132">Le code dans l’exemple suivant utilise les étapes suivantes pour effectuer le recoloriage :</span><span class="sxs-lookup"><span data-stu-id="8921d-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="8921d-133">Initialiser un <xref:System.Drawing.Imaging.ColorMatrix> objet.</span><span class="sxs-lookup"><span data-stu-id="8921d-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="8921d-134">Créer un <xref:System.Drawing.Imaging.ImageAttributes> de l’objet et de passer le <xref:System.Drawing.Imaging.ColorMatrix> de l’objet à la <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> méthode de la <xref:System.Drawing.Imaging.ImageAttributes> objet.</span><span class="sxs-lookup"><span data-stu-id="8921d-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="8921d-135">Passer la <xref:System.Drawing.Imaging.ImageAttributes> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="8921d-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8921d-136">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8921d-136">Compiling the Code</span></span>  
 <span data-ttu-id="8921d-137">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="8921d-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8921d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8921d-138">See Also</span></span>  
 [<span data-ttu-id="8921d-139">Recoloriage des images</span><span class="sxs-lookup"><span data-stu-id="8921d-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="8921d-140">Systèmes de coordonnées et transformations</span><span class="sxs-lookup"><span data-stu-id="8921d-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
