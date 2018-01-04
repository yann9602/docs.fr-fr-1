---
title: "Comment : rogner une image"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 084e3dc7fad2bcb3b7ab787302f55c824ff3739d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="187dd-102">Comment : rogner une image</span><span class="sxs-lookup"><span data-stu-id="187dd-102">How to: Crop an Image</span></span>
<span data-ttu-id="187dd-103">Cet exemple montre comment rogner une image à l’aide de <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="187dd-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="187dd-104"><xref:System.Windows.Media.Imaging.CroppedBitmap>est principalement utilisé lors de l’encodage de version d’une image rognée à enregistrer dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="187dd-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="187dd-105">Pour rogner une image à des fins d’affichage, consultez la [créer une zone de découpage](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376) rubrique.</span><span class="sxs-lookup"><span data-stu-id="187dd-105">To crop an image for display purposes see the [Create a Clip Region](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="187dd-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="187dd-106">Example</span></span>  
 <span data-ttu-id="187dd-107">Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] définit les ressources utilisées dans les exemples ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="187dd-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="187dd-108">L’exemple suivant crée une image en utilisant un <xref:System.Windows.Media.Imaging.CroppedBitmap> comme source.</span><span class="sxs-lookup"><span data-stu-id="187dd-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="187dd-109">Le <xref:System.Windows.Media.Imaging.CroppedBitmap> peut également être utilisé comme source d’un autre <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaînage le rognage.</span><span class="sxs-lookup"><span data-stu-id="187dd-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="187dd-110">Notez que le <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> utilise les valeurs par rapport à la bitmap source rogné et non pas l’image initiale.</span><span class="sxs-lookup"><span data-stu-id="187dd-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="187dd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="187dd-111">See Also</span></span>  
 [<span data-ttu-id="187dd-112">Créer une zone de découpage</span><span class="sxs-lookup"><span data-stu-id="187dd-112">Create a Clip Region</span></span>](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376)
