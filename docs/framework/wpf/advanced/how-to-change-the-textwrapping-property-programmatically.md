---
title: "Guide pratique pour changer la propriété TextWrapping par programmation"
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
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca87d651f66edba00280a57ca1468af33657a329
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="d7bd7-102">Guide pratique pour changer la propriété TextWrapping par programmation</span><span class="sxs-lookup"><span data-stu-id="d7bd7-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="d7bd7-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="d7bd7-103">Example</span></span>  
 <span data-ttu-id="d7bd7-104">L’exemple de code suivant montre comment modifier la valeur de la <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> propriété par programmation.</span><span class="sxs-lookup"><span data-stu-id="d7bd7-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="d7bd7-105">Trois <xref:System.Windows.Controls.Button> éléments sont placés dans un <xref:System.Windows.Controls.StackPanel> élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7bd7-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="d7bd7-106">Chaque <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour un <xref:System.Windows.Controls.Button> correspond à un gestionnaire d’événements dans le code.</span><span class="sxs-lookup"><span data-stu-id="d7bd7-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="d7bd7-107">Les gestionnaires d’événements utilisent le même nom que le <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> valeur s’appliquera à `txt2` lorsque le bouton est activé.</span><span class="sxs-lookup"><span data-stu-id="d7bd7-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="d7bd7-108">En outre, le texte de `txt1` (un <xref:System.Windows.Controls.TextBlock> ne pas indiqué dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) est mis à jour pour refléter les modifications de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d7bd7-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d7bd7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7bd7-109">See Also</span></span>  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
