---
title: "Comment : ajouter un gestionnaire d'événements à l'aide de code"
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
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abcd441219e58df2e5a0d4b66447e255c6aabd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="bec5e-102">Comment : ajouter un gestionnaire d'événements à l'aide de code</span><span class="sxs-lookup"><span data-stu-id="bec5e-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="bec5e-103">Cet exemple montre comment ajouter un gestionnaire d’événements à un élément à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="bec5e-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="bec5e-104">Si vous souhaitez ajouter un gestionnaire d’événements à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] élément et la page de balisage qui contient l’élément a déjà été chargé, vous devez ajouter le gestionnaire à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="bec5e-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="bec5e-105">Vous pouvez également, si vous développez l’arborescence d’éléments pour une application entièrement à l’aide de code et ne déclare ne pas tous les éléments à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez appeler des méthodes spécifiques pour ajouter des gestionnaires d’événements à l’arborescence d’éléments construite.</span><span class="sxs-lookup"><span data-stu-id="bec5e-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bec5e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="bec5e-106">Example</span></span>  
 <span data-ttu-id="bec5e-107">L’exemple suivant ajoute un nouveau <xref:System.Windows.Controls.Button> à une page existante définie initialement dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bec5e-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="bec5e-108">Un fichier code-behind implémente une méthode de gestionnaire d’événements et puis ajoute cette méthode comme un gestionnaire d’événements sur le <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="bec5e-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="bec5e-109">Le [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] exemple utilise le `+=` opérateur pour assigner un gestionnaire à un événement.</span><span class="sxs-lookup"><span data-stu-id="bec5e-109">The [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="bec5e-110">C’est le même opérateur qui est utilisé pour affecter un gestionnaire dans le [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] modèle de gestion d’événements.</span><span class="sxs-lookup"><span data-stu-id="bec5e-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]<span data-ttu-id="bec5e-111">ne prend pas en charge cet opérateur comme un moyen d’ajouter des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="bec5e-111"> does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="bec5e-112">Au lieu de cela, il requiert une des deux techniques :</span><span class="sxs-lookup"><span data-stu-id="bec5e-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="bec5e-113">Utilisez le <xref:System.Windows.UIElement.AddHandler%2A> méthode, avec un `AddressOf` (opérateur), pour faire référence à l’implémentation de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="bec5e-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="bec5e-114">Utilisez le `Handles` mot clé dans le cadre de la définition de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="bec5e-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="bec5e-115">Cette technique n’est pas indiquée ici ; consultez [Visual Basic et la gestion des événements de WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="bec5e-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="bec5e-116">Ajout d’un gestionnaire d’événements dans analysée initialement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page est beaucoup plus simple.</span><span class="sxs-lookup"><span data-stu-id="bec5e-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="bec5e-117">Dans l’élément d’objet sur lequel vous souhaitez ajouter le Gestionnaire d’événements, ajoutez un attribut qui correspond au nom de l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="bec5e-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="bec5e-118">Puis spécifiez la valeur de cet attribut comme nom de la méthode de gestionnaire d’événements que vous avez définie dans le fichier code-behind de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span><span class="sxs-lookup"><span data-stu-id="bec5e-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="bec5e-119">Pour plus d’informations, consultez [vue d’ensemble du XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) ou [vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bec5e-119">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec5e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bec5e-120">See Also</span></span>  
 [<span data-ttu-id="bec5e-121">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="bec5e-121">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="bec5e-122">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="bec5e-122">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
