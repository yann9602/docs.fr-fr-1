---
title: "Comment : sélectionner une encre à partir d'un contrôle personnalisé"
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
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd9693209cc35ecd3c0473133b7c21639a239ff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-ink-from-a-custom-control"></a><span data-ttu-id="70785-102">Comment : sélectionner une encre à partir d'un contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="70785-102">How to: Select Ink from a Custom Control</span></span>
<span data-ttu-id="70785-103">En ajoutant un <xref:System.Windows.Ink.IncrementalLassoHitTester> à votre contrôle personnalisé, vous pouvez activer votre contrôle afin qu’un utilisateur peut sélectionner encre avec un outil lasso, semblable à la façon dont le <xref:System.Windows.Controls.InkCanvas> sélectionne l’encre avec un lasso.</span><span class="sxs-lookup"><span data-stu-id="70785-103">By adding an <xref:System.Windows.Ink.IncrementalLassoHitTester> to your custom control, you can enable your control so that a user can select ink with a lasso tool, similar to the way the <xref:System.Windows.Controls.InkCanvas> selects ink with a lasso.</span></span>  
  
 <span data-ttu-id="70785-104">Cet exemple suppose que vous êtes familiarisé avec la création d’un contrôle personnalisé d’encre compatible.</span><span class="sxs-lookup"><span data-stu-id="70785-104">This example assumes you are familiar with creating an ink-enabled custom control.</span></span>  <span data-ttu-id="70785-105">Pour créer un contrôle personnalisé qui accepte une entrée d’encre, consultez [création d’un contrôle d’entrée manuscrite](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="70785-105">To create a custom control that accepts ink input, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70785-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="70785-106">Example</span></span>  
 <span data-ttu-id="70785-107">Lorsque l’utilisateur dessine un lasso, le <xref:System.Windows.Ink.IncrementalLassoHitTester> prévoit quels traits seront dans les limites de ce tracé une fois que l’utilisateur termine le lasso.</span><span class="sxs-lookup"><span data-stu-id="70785-107">When the user draws a lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> predicts which strokes will be within the lasso path's boundaries after the user completes the lasso.</span></span>  <span data-ttu-id="70785-108">Les traits déterminés pour être dans les limites de ce tracé peuvent être considérés comme étant sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="70785-108">Strokes that are determined to be within the lasso path's boundaries can be thought of as being selected.</span></span>  <span data-ttu-id="70785-109">Traits sélectionnés peuvent également être désélectionnés.</span><span class="sxs-lookup"><span data-stu-id="70785-109">Selected strokes can also become unselected.</span></span>  <span data-ttu-id="70785-110">Par exemple, si l’utilisateur inverse la direction lorsqu’il dessine le lasso, le <xref:System.Windows.Ink.IncrementalLassoHitTester> peut désélectionner certains traits.</span><span class="sxs-lookup"><span data-stu-id="70785-110">For example, if the user reverses direction while drawing the lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> may unselect some strokes.</span></span>  
  
 <span data-ttu-id="70785-111">Le <xref:System.Windows.Ink.IncrementalLassoHitTester> déclenche le <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> événement, ce qui permet à votre contrôle personnalisé répondre quand l’utilisateur dessine le lasso.</span><span class="sxs-lookup"><span data-stu-id="70785-111">The <xref:System.Windows.Ink.IncrementalLassoHitTester> raises the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, which enables your custom control to respond while the user is drawing the lasso.</span></span>  <span data-ttu-id="70785-112">Par exemple, vous pouvez modifier l’apparence des traits lorsque l’utilisateur sélectionne et désélectionne les.</span><span class="sxs-lookup"><span data-stu-id="70785-112">For example, you can change the appearance of strokes as the user selects and unselects them.</span></span>  
  
## <a name="managing-the-ink-mode"></a><span data-ttu-id="70785-113">Gestion du Mode d’encre</span><span class="sxs-lookup"><span data-stu-id="70785-113">Managing the Ink Mode</span></span>  
 <span data-ttu-id="70785-114">Il est utile de l’utilisateur si le lasso apparaît différemment de l’encre sur votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="70785-114">It is helpful to the user if the lasso appears differently than the ink on your control.</span></span> <span data-ttu-id="70785-115">Pour ce faire, votre contrôle personnalisé doit de savoir si l’utilisateur est l’écriture ou en sélectionnant manuscrit.</span><span class="sxs-lookup"><span data-stu-id="70785-115">To accomplish this, your custom control must keep track of whether the user is writing or selecting ink.</span></span> <span data-ttu-id="70785-116">La façon la plus simple consiste à déclarer une énumération avec deux valeurs : une pour indiquer que l’utilisateur est l’écriture manuscrite et l’autre pour indiquer que l’utilisateur sélectionne de l’encre.</span><span class="sxs-lookup"><span data-stu-id="70785-116">The easiest way to do this is to declare an enumeration with two values: one to indicate that the user is writing ink and one to indicate that the user is selecting ink.</span></span>  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 <span data-ttu-id="70785-117">Ensuite, ajoutez deux <xref:System.Windows.Ink.DrawingAttributes> à la classe : l’application à utiliser lorsque l’utilisateur écrit encre, un à utiliser lorsque l’utilisateur sélectionne l’encre.</span><span class="sxs-lookup"><span data-stu-id="70785-117">Next, add two <xref:System.Windows.Ink.DrawingAttributes> to the class: one to use when the user writes ink, one to use when the user selects ink.</span></span>  <span data-ttu-id="70785-118">Dans le constructeur, initialisez le <xref:System.Windows.Ink.DrawingAttributes> et attachez les deux <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> événements au même gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="70785-118">In the constructor, initialize the <xref:System.Windows.Ink.DrawingAttributes> and attach both <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> events to the same event handler.</span></span> <span data-ttu-id="70785-119">Définissez ensuite le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriété de la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à l’encre <xref:System.Windows.Ink.DrawingAttributes>.</span><span class="sxs-lookup"><span data-stu-id="70785-119">Then set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the ink <xref:System.Windows.Ink.DrawingAttributes>.</span></span>  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 <span data-ttu-id="70785-120">Ajouter une propriété qui expose le mode de sélection.</span><span class="sxs-lookup"><span data-stu-id="70785-120">Add a property that exposes the selection mode.</span></span> <span data-ttu-id="70785-121">Lorsque l’utilisateur modifie le mode de sélection, définissez la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriété de la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> approprié <xref:System.Windows.Ink.DrawingAttributes> de l’objet, puis reconnectez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> propriété le <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="70785-121">When the user changes the selection mode, set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the appropriate <xref:System.Windows.Ink.DrawingAttributes> object and then reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> Property to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <span data-ttu-id="70785-122">Exposer le <xref:System.Windows.Ink.DrawingAttributes> comme propriétés pour que les applications puissent déterminer l’apparence des traits d’encre et des traits de sélection.</span><span class="sxs-lookup"><span data-stu-id="70785-122">Expose the <xref:System.Windows.Ink.DrawingAttributes> as properties so applications can determine the appearance of the ink strokes and selection strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <span data-ttu-id="70785-123">Lorsqu’une propriété d’un <xref:System.Windows.Ink.DrawingAttributes> l’objet de modifications, la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> doit être rattachée à la <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="70785-123">When a property of a <xref:System.Windows.Ink.DrawingAttributes> object changes, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> must be reattached to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="70785-124">Dans le Gestionnaire d’événements pour le <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> événement, rattachez la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> à la <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="70785-124">In the event handler for the <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> event, reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a><span data-ttu-id="70785-125">Utilisation d’IncrementalLassoHitTester</span><span class="sxs-lookup"><span data-stu-id="70785-125">Using the IncrementalLassoHitTester</span></span>  
 <span data-ttu-id="70785-126">Créer et initialiser un <xref:System.Windows.Ink.StrokeCollection> qui contient les traits sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="70785-126">Create and initialize a <xref:System.Windows.Ink.StrokeCollection> that contains the selected strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 <span data-ttu-id="70785-127">Lorsque l’utilisateur commence à dessiner un tracé, d’encre ou le lasso, désélectionnez tous les traits sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="70785-127">When the user starts to draw a stroke, either ink or the lasso, unselect any selected strokes.</span></span> <span data-ttu-id="70785-128">Puis, si l’utilisateur dessine un lasso, créez un <xref:System.Windows.Ink.IncrementalLassoHitTester> en appelant <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, s’abonner à la <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> événement, puis appelez <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span><span class="sxs-lookup"><span data-stu-id="70785-128">Then, if the user is drawing a lasso, create an <xref:System.Windows.Ink.IncrementalLassoHitTester> by calling <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subscribe to the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, and call <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span></span> <span data-ttu-id="70785-129">Ce code peut être une méthode distincte et appelé à partir de la <xref:System.Windows.UIElement.OnStylusDown%2A> et <xref:System.Windows.UIElement.OnMouseDown%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="70785-129">This code can be a separate method and called from the <xref:System.Windows.UIElement.OnStylusDown%2A> and <xref:System.Windows.UIElement.OnMouseDown%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 <span data-ttu-id="70785-130">Ajoutez les points du stylet à le <xref:System.Windows.Ink.IncrementalLassoHitTester> pendant que l’utilisateur dessine le lasso.</span><span class="sxs-lookup"><span data-stu-id="70785-130">Add the stylus points to the <xref:System.Windows.Ink.IncrementalLassoHitTester> while the user draws the lasso.</span></span>  <span data-ttu-id="70785-131">Appelez la méthode suivante à partir de la <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, et <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="70785-131">Call the following method from the <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, and <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 <span data-ttu-id="70785-132">Gérer les <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> événement répondre quand l’utilisateur sélectionne et désélectionne des traits.</span><span class="sxs-lookup"><span data-stu-id="70785-132">Handle the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> event to respond when the user selects and unselects strokes.</span></span>  <span data-ttu-id="70785-133">Le <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> classe a la <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> et <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> qui obtiennent les traits qui ont été sélectionnés et désélectionnés, respectivement.</span><span class="sxs-lookup"><span data-stu-id="70785-133">The <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> class has the <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> and <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> properties that get the strokes that were selected and unselected, respectively.</span></span>  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 <span data-ttu-id="70785-134">Lorsque l’utilisateur termine de dessiner le lasso, annuler l’abonnement à la <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> événements et les appels <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span><span class="sxs-lookup"><span data-stu-id="70785-134">When the user finishes drawing the lasso, unsubscribe from the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event and call <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span></span>  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a><span data-ttu-id="70785-135">Montage.</span><span class="sxs-lookup"><span data-stu-id="70785-135">Putting it All Together.</span></span>  
 <span data-ttu-id="70785-136">L’exemple suivant est un contrôle personnalisé qui permet à un utilisateur de sélectionner l’encre avec un lasso.</span><span class="sxs-lookup"><span data-stu-id="70785-136">The following example is a custom control that enables a user to select ink with a lasso.</span></span>  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="70785-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70785-137">See Also</span></span>  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [<span data-ttu-id="70785-138">Création d'un contrôle d'entrée d'encre</span><span class="sxs-lookup"><span data-stu-id="70785-138">Creating an Ink Input Control</span></span>](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
