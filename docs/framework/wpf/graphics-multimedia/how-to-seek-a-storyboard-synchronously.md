---
title: "Comment : rechercher un storyboard de façon synchrone"
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
- seeking Storyboards synchronously [WPF]
- Storyboards [WPF], seeking synchronously
ms.assetid: 03e06271-a946-4810-88ea-3fb4cfa9e0f1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb5f0203c80cc94d17fcfcd40ff4d79bf8ecdc85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-seek-a-storyboard-synchronously"></a><span data-ttu-id="97500-102">Comment : rechercher un storyboard de façon synchrone</span><span class="sxs-lookup"><span data-stu-id="97500-102">How to: Seek a Storyboard Synchronously</span></span>
<span data-ttu-id="97500-103">L’exemple suivant montre comment utiliser le <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> méthode d’un <xref:System.Windows.Media.Animation.Storyboard> pour rechercher une position dans une animation de la table de montage séquentiel de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="97500-103">The following example shows how to use the <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> method of a <xref:System.Windows.Media.Animation.Storyboard> to seek to any position in a storyboard animation synchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97500-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="97500-104">Example</span></span>  
 <span data-ttu-id="97500-105">Voici le balisage XAML de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="97500-105">The following is the XAML markup for the sample.</span></span>  
  
 [!code-xaml[SeekStoryboard_snip#SeekStoryboardSynchronouslyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml#seekstoryboardsynchronouslyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="97500-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="97500-106">Example</span></span>  
 <span data-ttu-id="97500-107">Voici le code utilisé avec le code XAML ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="97500-107">The following is the code used with the XAML code above.</span></span>  
  
 [!code-csharp[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SeekStoryboard_snip/CSharp/SeekStoryboardSynchronouslyExample.xaml.cs#seekstoryboardsynchronouslycodebehindexamplewholepage)]
 [!code-vb[SeekStoryboard_snip#SeekStoryboardSynchronouslyCodeBehindExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SeekStoryboard_snip/VisualBasic/SeekStoryboardSynchronouslyExample.xaml.vb#seekstoryboardsynchronouslycodebehindexamplewholepage)]
