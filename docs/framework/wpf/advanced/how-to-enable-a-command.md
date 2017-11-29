---
title: "Comment : activer une commande"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e90f7f69aebf48bbc27321d3808468a2df49f793
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="d7e67-102">Comment : activer une commande</span><span class="sxs-lookup"><span data-stu-id="d7e67-102">How to: Enable a Command</span></span>
<span data-ttu-id="d7e67-103">L’exemple suivant montre comment utiliser l’exécution de commandes dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7e67-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="d7e67-104">L’exemple montre comment associer un <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Button>, créez un <xref:System.Windows.Input.CommandBinding>et créer les gestionnaires d’événements qui implémentent la <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="d7e67-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="d7e67-105">Pour plus d’informations sur l’exécution des commandes, consultez le [vue d’ensemble de l’exécution des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d7e67-105">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7e67-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="d7e67-106">Example</span></span>  
 <span data-ttu-id="d7e67-107">La première section de code crée la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], qui se compose d’un <xref:System.Windows.Controls.Button> et un <xref:System.Windows.Controls.StackPanel>et crée un <xref:System.Windows.Input.CommandBinding> qui associe les gestionnaires de commandes avec la <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="d7e67-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="d7e67-108">Le <xref:System.Windows.Input.ICommandSource.Command%2A> propriété de la <xref:System.Windows.Controls.Button> est associé le <xref:System.Windows.Input.ApplicationCommands.Close%2A> commande.</span><span class="sxs-lookup"><span data-stu-id="d7e67-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="d7e67-109">Le <xref:System.Windows.Input.CommandBinding> est ajouté à la <xref:System.Windows.Input.CommandBindingCollection> de la racine de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="d7e67-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d7e67-110">Le <xref:System.Windows.Input.CommandBinding.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute> gestionnaires d’événements sont attachés à cette liaison et associés à la <xref:System.Windows.Input.ApplicationCommands.Close%2A> commande.</span><span class="sxs-lookup"><span data-stu-id="d7e67-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="d7e67-111">Sans le <xref:System.Windows.Input.CommandBinding> il n’existe aucune commande logique, uniquement un mécanisme pour appeler la commande.</span><span class="sxs-lookup"><span data-stu-id="d7e67-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="d7e67-112">Lorsque le <xref:System.Windows.Controls.Button> est activé, le <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> est déclenché sur la cible de commande suivie par le <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span><span class="sxs-lookup"><span data-stu-id="d7e67-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="d7e67-113">Ces événements parcourent l’arborescence d’éléments recherchant un <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.</span><span class="sxs-lookup"><span data-stu-id="d7e67-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="d7e67-114">Il est important de noter que, car <xref:System.Windows.RoutedEvent> tunnel et se propagent dans l’arborescence d’éléments, soyez prudent en où le <xref:System.Windows.Input.CommandBinding> est placé.</span><span class="sxs-lookup"><span data-stu-id="d7e67-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="d7e67-115">Si le <xref:System.Windows.Input.CommandBinding> se trouve sur un frère de la cible de commande ou un autre nœud qui n’est pas sur l’itinéraire de le <xref:System.Windows.RoutedEvent>, le <xref:System.Windows.Input.CommandBinding> n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="d7e67-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="d7e67-116">La section suivante du code implémente le <xref:System.Windows.Input.CommandManager.Executed> et <xref:System.Windows.Input.CommandBinding.CanExecute> gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="d7e67-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="d7e67-117">Le <xref:System.Windows.Input.CommandManager.Executed> gestionnaire appelle une méthode pour fermer le fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="d7e67-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="d7e67-118">Le <xref:System.Windows.Input.CommandBinding.CanExecute> appelle une méthode pour déterminer si un fichier est ouvert.</span><span class="sxs-lookup"><span data-stu-id="d7e67-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="d7e67-119">Si un fichier est ouvert, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> a la valeur `true`; sinon, elle est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="d7e67-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="d7e67-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7e67-120">See Also</span></span>  
 [<span data-ttu-id="d7e67-121">Vue d’ensemble des commandes</span><span class="sxs-lookup"><span data-stu-id="d7e67-121">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
