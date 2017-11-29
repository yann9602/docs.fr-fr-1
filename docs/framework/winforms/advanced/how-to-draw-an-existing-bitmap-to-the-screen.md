---
title: "Comment : dessiner une bitmap existante à l'écran"
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f435c397832e8f64b2bf911a59aae7578ffd3bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="26726-102">Comment : dessiner une bitmap existante à l'écran</span><span class="sxs-lookup"><span data-stu-id="26726-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="26726-103">Vous pouvez facilement dessiner une image existante à l’écran.</span><span class="sxs-lookup"><span data-stu-id="26726-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="26726-104">Vous devez d’abord créer un <xref:System.Drawing.Bitmap> objet à l’aide du constructeur de bitmap qui prend un nom de fichier <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="26726-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="26726-105">Ce constructeur accepte des images avec différents formats de fichiers, notamment BMP, GIF, JPEG, PNG et TIFF.</span><span class="sxs-lookup"><span data-stu-id="26726-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="26726-106">Après avoir créé le <xref:System.Drawing.Bitmap> d’objet, qui <xref:System.Drawing.Bitmap> de l’objet à la <xref:System.Drawing.Graphics.DrawImage%2A> méthode d’un <xref:System.Drawing.Graphics> objet.</span><span class="sxs-lookup"><span data-stu-id="26726-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26726-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="26726-107">Example</span></span>  
 <span data-ttu-id="26726-108">Cet exemple crée un <xref:System.Drawing.Bitmap> objet à partir d’un fichier JPEG, puis dessine l’image bitmap avec son coin supérieur gauche à (60, 10).</span><span class="sxs-lookup"><span data-stu-id="26726-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="26726-109">L’illustration suivante montre la bitmap dessinée à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="26726-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="26726-110">![Position de l’image](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="26726-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26726-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="26726-111">Compiling the Code</span></span>  
 <span data-ttu-id="26726-112">L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="26726-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26726-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26726-113">See Also</span></span>  
 [<span data-ttu-id="26726-114">Graphiques et dessins dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26726-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="26726-115">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="26726-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
