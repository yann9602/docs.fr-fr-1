---
title: "Comment : répertorier les encodeurs installés"
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
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70f913acb2620b5c01e1aec1f1eb98b041b82a59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="53fb8-102">Comment : répertorier les encodeurs installés</span><span class="sxs-lookup"><span data-stu-id="53fb8-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="53fb8-103">Vous souhaiterez répertorier les encodeurs d’image disponibles sur un ordinateur, pour déterminer si votre application peut enregistrer dans un format de fichier d’image spécifique.</span><span class="sxs-lookup"><span data-stu-id="53fb8-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="53fb8-104">Le <xref:System.Drawing.Imaging.ImageCodecInfo> classe fournit le <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> méthodes statiques afin que vous puissiez déterminer quelle image encodeurs sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="53fb8-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="53fb8-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>Retourne un tableau de <xref:System.Drawing.Imaging.ImageCodecInfo> objets.</span><span class="sxs-lookup"><span data-stu-id="53fb8-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53fb8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="53fb8-106">Example</span></span>  
 <span data-ttu-id="53fb8-107">L’exemple de code suivant génère la liste des encodeurs installés et leurs valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="53fb8-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53fb8-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="53fb8-108">Compiling the Code</span></span>  
 <span data-ttu-id="53fb8-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="53fb8-109">This example requires:</span></span>  
  
-   <span data-ttu-id="53fb8-110">une application Windows Forms ;</span><span class="sxs-lookup"><span data-stu-id="53fb8-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="53fb8-111">A <xref:System.Windows.Forms.PaintEventArgs>, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="53fb8-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fb8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53fb8-112">See Also</span></span>  
 [<span data-ttu-id="53fb8-113">Guide pratique pour répertorier les décodeurs installés</span><span class="sxs-lookup"><span data-stu-id="53fb8-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="53fb8-114">Utilisation d’encodeurs et de décodeurs d’images dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="53fb8-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
