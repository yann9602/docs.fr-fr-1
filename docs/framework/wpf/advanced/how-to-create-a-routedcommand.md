---
title: "Comment : créer un RoutedCommand"
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
helpviewer_keywords: RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dad0cd8aaa81e6a458307ec69ec60ed369ca6b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="c735c-102">Comment : créer un RoutedCommand</span><span class="sxs-lookup"><span data-stu-id="c735c-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="c735c-103">Cet exemple montre comment créer un personnalisé <xref:System.Windows.Input.RoutedCommand> et comment implémenter la commande personnalisée en créant un <xref:System.Windows.Input.ExecutedRoutedEventHandler> et un <xref:System.Windows.Input.CanExecuteRoutedEventHandler> et les joindre à un <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="c735c-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="c735c-104">Pour plus d’informations sur l’exécution des commandes, consultez le [vue d’ensemble de l’exécution des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c735c-104">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c735c-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c735c-105">Example</span></span>  
 <span data-ttu-id="c735c-106">La première étape de création d’un <xref:System.Windows.Input.RoutedCommand> est la définition de la commande et l’instancier.</span><span class="sxs-lookup"><span data-stu-id="c735c-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="c735c-107">Pour utiliser la commande dans une application, les gestionnaires d’événements qui définissent ce que fait la commande doivent être créées.</span><span class="sxs-lookup"><span data-stu-id="c735c-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="c735c-108">Ensuite, un <xref:System.Windows.Input.CommandBinding> est créé qui associe la commande avec les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="c735c-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="c735c-109">Le <xref:System.Windows.Input.CommandBinding> est créé sur un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="c735c-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="c735c-110">Cet objet définit l’étendue de la <xref:System.Windows.Input.CommandBinding> dans l’arborescence d’éléments</span><span class="sxs-lookup"><span data-stu-id="c735c-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="c735c-111">L’étape finale consiste à appeler la commande.</span><span class="sxs-lookup"><span data-stu-id="c735c-111">The final step is invoking the command.</span></span>  <span data-ttu-id="c735c-112">La première consiste à appeler une commande à associer à un <xref:System.Windows.Input.ICommandSource>, comme un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="c735c-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="c735c-113">Lorsque le bouton est activé, le <xref:System.Windows.Input.RoutedCommand.Execute%2A> méthode personnalisée <xref:System.Windows.Input.RoutedCommand> est appelée.</span><span class="sxs-lookup"><span data-stu-id="c735c-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="c735c-114">Le <xref:System.Windows.Input.RoutedCommand> déclenche le <xref:System.Windows.Input.CommandManager.PreviewExecuted> et <xref:System.Windows.Input.CommandManager.Executed> les événements routés.</span><span class="sxs-lookup"><span data-stu-id="c735c-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="c735c-115">Ces événements parcourent l’arborescence d’éléments recherchant un <xref:System.Windows.Input.CommandBinding> pour cette commande particulière.</span><span class="sxs-lookup"><span data-stu-id="c735c-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="c735c-116">Si un <xref:System.Windows.Input.CommandBinding> est trouvée, le <xref:System.Windows.Input.ExecutedRoutedEventHandler> associés <xref:System.Windows.Input.CommandBinding> est appelée.</span><span class="sxs-lookup"><span data-stu-id="c735c-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c735c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c735c-117">See Also</span></span>  
 <xref:System.Windows.Input.RoutedCommand>  
 [<span data-ttu-id="c735c-118">Vue d’ensemble des commandes</span><span class="sxs-lookup"><span data-stu-id="c735c-118">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
