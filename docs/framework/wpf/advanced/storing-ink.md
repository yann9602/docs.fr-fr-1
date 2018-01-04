---
title: Stockage de l'encre
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
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ab04db2faafc47349d3b8d21098e9eb931cf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="storing-ink"></a><span data-ttu-id="046d0-102">Stockage de l'encre</span><span class="sxs-lookup"><span data-stu-id="046d0-102">Storing Ink</span></span>
<span data-ttu-id="046d0-103">Le <xref:System.Windows.Ink.StrokeCollection.Save%2A> méthodes fournissent la prise en charge pour le stockage d’encre comme Ink Serialized Format (ISF).</span><span class="sxs-lookup"><span data-stu-id="046d0-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="046d0-104">Les constructeurs pour la <xref:System.Windows.Ink.StrokeCollection> classe prennent en charge pour la lecture des données de l’encre.</span><span class="sxs-lookup"><span data-stu-id="046d0-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="046d0-105">Stockage d’encre et de récupération</span><span class="sxs-lookup"><span data-stu-id="046d0-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="046d0-106">Cette section explique comment stocker et récupérer d’encre dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plateforme.</span><span class="sxs-lookup"><span data-stu-id="046d0-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="046d0-107">L’exemple suivant implémente un gestionnaire d’événements de clic de bouton qui présente une boîte de dialogue Enregistrer l’utilisateur et enregistre l’encre d’un <xref:System.Windows.Controls.InkCanvas> dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="046d0-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="046d0-108">L’exemple suivant implémente un gestionnaire d’événements de clic de bouton qui présente à l’utilisateur avec une boîte de dialogue Ouvrir le fichier et lit l’encre du fichier dans un <xref:System.Windows.Controls.InkCanvas> élément.</span><span class="sxs-lookup"><span data-stu-id="046d0-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="046d0-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="046d0-109">See Also</span></span>  
 <xref:System.Windows.Controls.InkCanvas>  
 [<span data-ttu-id="046d0-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="046d0-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
