---
title: "Comment : récupérer une sélection de texte"
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
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32be79811de4b8056449c2c6d6c53eca8cc063f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="7023d-102">Comment : récupérer une sélection de texte</span><span class="sxs-lookup"><span data-stu-id="7023d-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="7023d-103">Cet exemple montre une manière d’utiliser la <xref:System.Windows.Controls.TextBox.SelectedText%2A> propriété à récupérer le texte que l’utilisateur a sélectionné dans une <xref:System.Windows.Controls.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="7023d-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7023d-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7023d-104">Example</span></span>  
 <span data-ttu-id="7023d-105">Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemple illustre la définition d’un <xref:System.Windows.Controls.TextBox> contrôle contenant du texte à sélectionner, et un <xref:System.Windows.Controls.Button> contrôle avec un <xref:System.Windows.Controls.Button.OnClick%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="7023d-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="7023d-106">Dans cet exemple, un bouton avec associé à un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Gestionnaire d’événements est utilisé pour récupérer la sélection de texte.</span><span class="sxs-lookup"><span data-stu-id="7023d-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="7023d-107">Lorsque l’utilisateur clique sur le bouton, le <xref:System.Windows.Controls.Button.OnClick%2A> méthode copie le texte sélectionné dans la zone de texte dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="7023d-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="7023d-108">Circonstances particulières auxquelles la sélection de texte est récupérée (en cliquant sur un bouton), ainsi que l’action effectuée avec cette sélection (copie la sélection de texte en une chaîne), peut facilement être modifié pour prendre en charge un large éventail de scénarios.</span><span class="sxs-lookup"><span data-stu-id="7023d-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="7023d-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7023d-109">Example</span></span>  
 <span data-ttu-id="7023d-110">Les éléments suivants [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] exemple illustre une <xref:System.Windows.Controls.Button.OnClick%2A> Gestionnaire d’événements pour le bouton défini dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="7023d-110">The following [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="7023d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7023d-111">See Also</span></span>  
 [<span data-ttu-id="7023d-112">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="7023d-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="7023d-113">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="7023d-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
