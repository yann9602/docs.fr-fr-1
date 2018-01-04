---
title: "Comment : charger et afficher des métafichiers"
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
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7d0f2f15fc9e1dce77b9d8183e2e17b7c35b928
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="b474c-102">Comment : charger et afficher des métafichiers</span><span class="sxs-lookup"><span data-stu-id="b474c-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="b474c-103">Le <xref:System.Drawing.Imaging.Metafile> (classe), qui hérite de la <xref:System.Drawing.Image> de classe, fournit des méthodes pour l’enregistrement, l’affichage et examen d’images vectorielles.</span><span class="sxs-lookup"><span data-stu-id="b474c-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b474c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b474c-104">Example</span></span>  
 <span data-ttu-id="b474c-105">Pour afficher une image vectorielle (métafichier) à l’écran, vous devez un <xref:System.Drawing.Imaging.Metafile> objet et un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="b474c-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="b474c-106">Passez le nom d’un fichier (ou un flux de données) à un <xref:System.Drawing.Imaging.Metafile> constructeur.</span><span class="sxs-lookup"><span data-stu-id="b474c-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="b474c-107">Après avoir créé un <xref:System.Drawing.Imaging.Metafile> d’objet, qui <xref:System.Drawing.Imaging.Metafile> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="b474c-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="b474c-108">L’exemple crée un <xref:System.Drawing.Imaging.Metafile> objet à partir d’un fichier EMF (métafichier amélioré), puis dessine l’image avec son coin supérieur gauche à (60, 10).</span><span class="sxs-lookup"><span data-stu-id="b474c-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="b474c-109">L’illustration suivante montre le métafichier dessiné à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="b474c-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="b474c-110">![Position de l’image](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="b474c-110">![Image Position](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b474c-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b474c-111">Compiling the Code</span></span>  
 <span data-ttu-id="b474c-112">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="b474c-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b474c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b474c-113">See Also</span></span>  
 [<span data-ttu-id="b474c-114">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="b474c-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
