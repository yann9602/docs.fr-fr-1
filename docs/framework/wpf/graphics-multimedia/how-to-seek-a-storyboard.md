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
ms.workload: dotnet
ms.openlocfilehash: 521674fd735c70387f2857cd5c7c12ddea1380b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-seek-a-storyboard"></a><span data-ttu-id="11bd2-102">Comment : rechercher un storyboard</span><span class="sxs-lookup"><span data-stu-id="11bd2-102">How to: Seek a Storyboard</span></span>
<span data-ttu-id="11bd2-103">L’exemple suivant montre comment utiliser le <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> méthode d’un <xref:System.Windows.Media.Animation.Storyboard> pour accéder à n’importe quelle position dans une animation de la table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="11bd2-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to jump to any position in a storyboard animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11bd2-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="11bd2-104">Example</span></span>  
 <span data-ttu-id="11bd2-105">Voici le balisage XAML de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="11bd2-105">Below is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml#seekstoryboardexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="11bd2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="11bd2-106">Example</span></span>  
 <span data-ttu-id="11bd2-107">Voici le code utilisé avec le code XAML ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="11bd2-107">Below is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardExample.xaml.cs#seekstoryboardcodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardExample.xaml.vb#seekstoryboardcodebehindexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="11bd2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11bd2-108">See Also</span></span>  
 [<span data-ttu-id="11bd2-109">Rechercher un storyboard de façon synchrone</span><span class="sxs-lookup"><span data-stu-id="11bd2-109">Seek a Storyboard Synchronously</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)
