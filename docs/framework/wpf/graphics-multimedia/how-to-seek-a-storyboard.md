---
title: "Comment : rechercher un storyboard"
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
- Storyboards [WPF], seeking
- seeking Storyboards [WPF]
ms.assetid: 887bb39a-0c2a-4ae8-956d-1d9f6f8ebbfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c76236d8497936500989b56c816f8fe50efcc238
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="39ad8-102">Comment : rechercher un storyboard</span><span class="sxs-lookup"><span data-stu-id="39ad8-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="39ad8-103">L’exemple suivant montre comment utiliser le <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> méthode d’un <xref:System.Windows.Media.Animation.Storyboard> pour accéder à n’importe quelle position dans une animation de la table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="39ad8-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39ad8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="39ad8-104">Example</span></span>  
 <span data-ttu-id="39ad8-105">Voici le balisage XAML de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="39ad8-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="39ad8-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="39ad8-106">Example</span></span>  
 <span data-ttu-id="39ad8-107">Voici le code utilisé avec le code XAML ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="39ad8-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="39ad8-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39ad8-108">See Also</span></span>  
 [<span data-ttu-id="39ad8-109">Rechercher un storyboard de façon synchrone</span><span class="sxs-lookup"><span data-stu-id="39ad8-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
