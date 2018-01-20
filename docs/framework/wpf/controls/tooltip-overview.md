---
title: Vue d'ensemble de l'info-bulle
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
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c945d23def3bbf6284e7e0db95d391066256df6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="tooltip-overview"></a><span data-ttu-id="66769-102">Vue d'ensemble de l'info-bulle</span><span class="sxs-lookup"><span data-stu-id="66769-102">ToolTip Overview</span></span>
<span data-ttu-id="66769-103">Une info-bulle est une petite fenêtre contextuelle qui apparaît lorsqu’un utilisateur place le pointeur de la souris au-dessus d’un élément, tel qu’un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="66769-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="66769-104">Cette rubrique présente l’info-bulle et explique comment créer et personnaliser son contenu.</span><span class="sxs-lookup"><span data-stu-id="66769-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="66769-105">Qu’est-ce qu’une info-bulle ?</span><span class="sxs-lookup"><span data-stu-id="66769-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="66769-106">Lorsqu’un utilisateur déplace le pointeur de la souris sur un élément qui contient une info-bulle, une fenêtre qui renferme le contenu de l’info-bulle (par exemple, le contenu texte qui décrit la fonction d’un contrôle) apparaît pendant un laps de temps spécifié.</span><span class="sxs-lookup"><span data-stu-id="66769-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="66769-107">Si l’utilisateur éloigne le pointeur de la souris du contrôle, la fenêtre disparaît car le contenu de l’info-bulle ne peut pas recevoir le focus.</span><span class="sxs-lookup"><span data-stu-id="66769-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="66769-108">Une info-bulle peut contenir une ou plusieurs lignes de texte, des images, des formes ou un autre contenu visuel.</span><span class="sxs-lookup"><span data-stu-id="66769-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="66769-109">Pour définir une info-bulle pour un contrôle, vous devez définir l’une des propriétés suivantes pour le contenu de l’info-bulle.</span><span class="sxs-lookup"><span data-stu-id="66769-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="66769-110">Propriété que vous utilisez varie selon que le contrôle qui définit l’info-bulle hérite le <xref:System.Windows.FrameworkContentElement> ou <xref:System.Windows.FrameworkElement> classe.</span><span class="sxs-lookup"><span data-stu-id="66769-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="66769-111">Création d’une info-bulle</span><span class="sxs-lookup"><span data-stu-id="66769-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="66769-112">L’exemple suivant montre comment créer une info-bulle simple en définissant le <xref:System.Windows.FrameworkElement.ToolTip%2A> propriété pour un <xref:System.Windows.Controls.Button> contrôle à une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="66769-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="66769-113">Vous pouvez également définir une info-bulle comme un <xref:System.Windows.Controls.ToolTip> objet.</span><span class="sxs-lookup"><span data-stu-id="66769-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="66769-114">L’exemple suivant utilise [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier un <xref:System.Windows.Controls.ToolTip> objet en tant que l’info-bulle d’un <xref:System.Windows.Controls.TextBox> élément.</span><span class="sxs-lookup"><span data-stu-id="66769-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="66769-115">Notez que l’exemple spécifie le <xref:System.Windows.Controls.ToolTip> en définissant le <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="66769-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="66769-116">L’exemple suivant utilise le code pour générer un <xref:System.Windows.Controls.ToolTip> objet.</span><span class="sxs-lookup"><span data-stu-id="66769-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="66769-117">L’exemple crée un <xref:System.Windows.Controls.ToolTip> (`tt`) et l’associe à un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="66769-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="66769-118">Vous pouvez également créer le contenu d’info-bulle qui n’est pas défini comme un <xref:System.Windows.Controls.ToolTip> objet en mettant le contenu de l’info-bulle dans un élément de disposition, comme un <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="66769-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="66769-119">L’exemple suivant montre comment définir la <xref:System.Windows.FrameworkElement.ToolTip%2A> propriété d’un <xref:System.Windows.Controls.TextBox> au contenu qui est inclu dans un <xref:System.Windows.Controls.DockPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="66769-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="66769-120">Utilisation des propriétés de l’info-bulle et des classes ToolTipService</span><span class="sxs-lookup"><span data-stu-id="66769-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="66769-121">Vous pouvez personnaliser le contenu de l’info-bulle en définissant des propriétés visuelles et en appliquant des styles.</span><span class="sxs-lookup"><span data-stu-id="66769-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="66769-122">Si vous définissez l’info-bulle contenu comme un <xref:System.Windows.Controls.ToolTip> de l’objet, vous pouvez définir les propriétés visuelles de la <xref:System.Windows.Controls.ToolTip> objet.</span><span class="sxs-lookup"><span data-stu-id="66769-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="66769-123">Dans le cas contraire, vous devez définir des propriétés jointes équivalentes sur le <xref:System.Windows.Controls.ToolTipService> classe.</span><span class="sxs-lookup"><span data-stu-id="66769-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="66769-124">Pour obtenir un exemple montrant comment définir des propriétés pour spécifier la position du contenu de l’info-bulle à l’aide de la <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ToolTipService> propriétés, consultez [positionner une info-bulle](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="66769-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="66769-125">Application d’un style à une info-bulle</span><span class="sxs-lookup"><span data-stu-id="66769-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="66769-126">Vous pouvez appliquer un style un <xref:System.Windows.Controls.ToolTip> en définissant une personnalisée <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="66769-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="66769-127">L’exemple suivant définit un <xref:System.Windows.Style> appelé `Simple` qui montre comment compenser le placement de la <xref:System.Windows.Controls.ToolTip> et modifier son apparence en définissant le <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, et <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="66769-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="66769-128">Utilisation des propriétés d’intervalle de temps de ToolTipService</span><span class="sxs-lookup"><span data-stu-id="66769-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="66769-129">Le <xref:System.Windows.Controls.ToolTipService> classe fournit les propriétés suivantes pour vous permettre de définir des info-bulle affichent des heures : <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, et <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="66769-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="66769-130">Utilisez le <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> et <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> propriétés pour spécifier un délai, généralement bref, avant qu’un <xref:System.Windows.Controls.ToolTip> s’affiche et également pour spécifier la durée pendant laquelle un <xref:System.Windows.Controls.ToolTip> reste visible.</span><span class="sxs-lookup"><span data-stu-id="66769-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="66769-131">Pour plus d’informations, consultez la page [Comment : différer l’affichage d’une info-bulle](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span><span class="sxs-lookup"><span data-stu-id="66769-131">For more information, see [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span></span>  
  
 <span data-ttu-id="66769-132">Le <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété détermine si les info-bulles des différents contrôles apparaissent sans délai initial lorsque vous déplacez le pointeur de souris rapidement entre eux.</span><span class="sxs-lookup"><span data-stu-id="66769-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="66769-133">Pour plus d’informations sur la <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété, consultez [utiliser la propriété BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="66769-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="66769-134">L’exemple suivant montre comment définir ces propriétés pour une info-bulle.</span><span class="sxs-lookup"><span data-stu-id="66769-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="66769-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66769-135">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [<span data-ttu-id="66769-136">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="66769-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
