---
title: "Comment : utiliser un menu contextuel personnalisé avec un TextBox"
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
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4552031a08680af2f4d41702d2f76ed0c44af21b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="7bf91-102">Comment : utiliser un menu contextuel personnalisé avec un TextBox</span><span class="sxs-lookup"><span data-stu-id="7bf91-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="7bf91-103">Cet exemple montre comment définir et implémenter un menu contextuel personnalisé simple pour un <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7bf91-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bf91-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bf91-104">Example</span></span>  
 <span data-ttu-id="7bf91-105">Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemple définit un <xref:System.Windows.Controls.TextBox> contrôle qui inclut un menu contextuel personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7bf91-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="7bf91-106">Le menu contextuel est défini en utilisant un <xref:System.Windows.Controls.ContextMenu> élément.</span><span class="sxs-lookup"><span data-stu-id="7bf91-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="7bf91-107">Le menu contextuel lui-même est constitué d’une série de <xref:System.Windows.Controls.MenuItem> éléments et <xref:System.Windows.Controls.Separator> éléments.</span><span class="sxs-lookup"><span data-stu-id="7bf91-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="7bf91-108">Chaque <xref:System.Windows.Controls.MenuItem> élément définit une commande dans le menu contextuel ; le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribut définit le texte affiché de la commande de menu et le <xref:System.Windows.Controls.MenuItem.Click> attribut spécifie une méthode de gestionnaire pour chaque élément de menu.</span><span class="sxs-lookup"><span data-stu-id="7bf91-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="7bf91-109">Le <xref:System.Windows.Controls.Separator> élément entraîne simplement une ligne de séparation doit être restitué entre les éléments de menu précédents et suivants.</span><span class="sxs-lookup"><span data-stu-id="7bf91-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="7bf91-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bf91-110">Example</span></span>  
 <span data-ttu-id="7bf91-111">L’exemple suivant montre le code d’implémentation pour la définition du menu contexte précédent, ainsi que le code qui active et désactive le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7bf91-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="7bf91-112">Le <xref:System.Windows.Controls.ContextMenu.Opened> événement est utilisé pour activer ou désactiver certaines commandes selon l’état actuel de manière dynamique le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7bf91-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="7bf91-113">Pour restaurer le menu de contexte par défaut, utilisez le <xref:System.Windows.DependencyObject.ClearValue%2A> méthode pour effacer la valeur de la <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7bf91-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="7bf91-114">Pour désactiver le menu contextuel complètement, définissez la <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriété à une référence null (`Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7bf91-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="7bf91-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bf91-115">See Also</span></span>  
 [<span data-ttu-id="7bf91-116">Utiliser la vérification de l'orthographe avec un menu contextuel</span><span class="sxs-lookup"><span data-stu-id="7bf91-116">Use Spell Checking with a Context Menu</span></span>](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [<span data-ttu-id="7bf91-117">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="7bf91-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="7bf91-118">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="7bf91-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
