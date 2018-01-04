---
title: "Comment : répertorier les décodeurs installés"
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
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7993345a39a24c770fdd717580d428968dae836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="edea8-102">Comment : répertorier les décodeurs installés</span><span class="sxs-lookup"><span data-stu-id="edea8-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="edea8-103">Vous souhaiterez répertorier les décodeurs d’image disponibles sur un ordinateur, pour déterminer si votre application peut lire un format de fichier d’image spécifique.</span><span class="sxs-lookup"><span data-stu-id="edea8-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="edea8-104">Le <xref:System.Drawing.Imaging.ImageCodecInfo> classe fournit le <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> méthodes statiques afin que vous pouvez déterminer quelle image décodeurs sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="edea8-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="edea8-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>Retourne un tableau de <xref:System.Drawing.Imaging.ImageCodecInfo> objets.</span><span class="sxs-lookup"><span data-stu-id="edea8-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edea8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="edea8-106">Example</span></span>  
 <span data-ttu-id="edea8-107">L’exemple de code suivant génère la liste des décodeurs installés et leurs valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="edea8-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="edea8-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="edea8-108">Compiling the Code</span></span>  
 <span data-ttu-id="edea8-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="edea8-109">This example requires:</span></span>  
  
-   <span data-ttu-id="edea8-110">une application Windows Forms ;</span><span class="sxs-lookup"><span data-stu-id="edea8-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="edea8-111">A <xref:System.Windows.Forms.PaintEventArgs>, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="edea8-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edea8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edea8-112">See Also</span></span>  
 [<span data-ttu-id="edea8-113">Guide pratique pour répertorier les encodeurs installés</span><span class="sxs-lookup"><span data-stu-id="edea8-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="edea8-114">Utilisation d’encodeurs et de décodeurs d’images dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="edea8-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
