---
title: "Comment : gérer un événement routé"
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c491ff4e231d932b3714d2d059b52bad2502368c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="2ac0f-102">Comment : gérer un événement routé</span><span class="sxs-lookup"><span data-stu-id="2ac0f-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="2ac0f-103">Cet exemple illustre le fonctionnement des événements de propagation et indique comment écrire un gestionnaire permettant de traiter les données des événements routés.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ac0f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ac0f-104">Example</span></span>  
 <span data-ttu-id="2ac0f-105">Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les éléments sont organisés dans une structure d’arborescence d’éléments.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="2ac0f-106">L’élément parent peut participer à la gestion des événements déclenchés initialement par les éléments enfants dans l’arborescence d’éléments.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="2ac0f-107">Ceci est possible grâce au routage d’événement.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="2ac0f-108">En règle générale, les événements routés respectent l’une des deux stratégies de routage : propagation ou tunneling.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="2ac0f-109">Cet exemple se concentre sur l’événement de propagation et utilise le <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> événement pour montrer le fonctionnement du routage.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="2ac0f-110">L’exemple suivant crée deux <xref:System.Windows.Controls.Button> contrôle et utilise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe pour attacher un gestionnaire d’événements à un élément parent commun, qui est dans cet exemple d’attribut <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="2ac0f-111">Au lieu d’attacher un gestionnaire d’événements pour chaque <xref:System.Windows.Controls.Button> élément enfant, l’exemple utilise la syntaxe d’attribut pour attacher le Gestionnaire d’événements pour le <xref:System.Windows.Controls.StackPanel> élément parent.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="2ac0f-112">Ce modèle de gestion des événements indique comment utiliser le routage d’événement afin de réduire le nombre d’éléments attachés à un gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="2ac0f-113">Tous les événements de propagation pour chaque <xref:System.Windows.Controls.Button> passent par l’élément parent.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="2ac0f-114">Notez que sur le parent <xref:System.Windows.Controls.StackPanel> élément, le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> nom de l’événement spécifié comme l’attribut est partiellement qualifié en nommant le <xref:System.Windows.Controls.Button> classe.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="2ac0f-115">Le <xref:System.Windows.Controls.Button> classe est un <xref:System.Windows.Controls.Primitives.ButtonBase> classe dérivée qui a le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement dans la liste de membres.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="2ac0f-116">Cette technique de qualification partielle permettant d’attacher un gestionnaire d’événements est nécessaire si l’événement géré n’existe pas dans la liste de membres de l’élément auquel le gestionnaire d’événements routés est attaché.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="2ac0f-117">L’exemple suivant gère le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="2ac0f-118">L’exemple signale l’élément qui gère l’événement, ainsi que l’élément qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="2ac0f-119">Le gestionnaire d’événements est exécuté quand l’utilisateur clique sur l’un des boutons.</span><span class="sxs-lookup"><span data-stu-id="2ac0f-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="2ac0f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ac0f-120">See Also</span></span>  
 <xref:System.Windows.RoutedEvent>  
 [<span data-ttu-id="2ac0f-121">Vue d’ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="2ac0f-121">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="2ac0f-122">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="2ac0f-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="2ac0f-123">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2ac0f-123">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [<span data-ttu-id="2ac0f-124">Syntaxe XAML en détail</span><span class="sxs-lookup"><span data-stu-id="2ac0f-124">XAML Syntax In Detail</span></span>](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
