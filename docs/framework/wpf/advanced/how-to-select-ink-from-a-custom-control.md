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
# <a name="how-to-select-ink-from-a-custom-control"></a>Comment : sélectionner une encre à partir d'un contrôle personnalisé
En ajoutant un <xref:System.Windows.Ink.IncrementalLassoHitTester> à votre contrôle personnalisé, vous pouvez activer votre contrôle afin qu’un utilisateur peut sélectionner encre avec un outil lasso, semblable à la façon dont le <xref:System.Windows.Controls.InkCanvas> sélectionne l’encre avec un lasso.  
  
 Cet exemple suppose que vous êtes familiarisé avec la création d’un contrôle personnalisé d’encre compatible.  Pour créer un contrôle personnalisé qui accepte une entrée d’encre, consultez [création d’un contrôle d’entrée manuscrite](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
## <a name="example"></a>Exemple  
 Lorsque l’utilisateur dessine un lasso, le <xref:System.Windows.Ink.IncrementalLassoHitTester> prévoit quels traits seront dans les limites de ce tracé une fois que l’utilisateur termine le lasso.  Les traits déterminés pour être dans les limites de ce tracé peuvent être considérés comme étant sélectionnée.  Traits sélectionnés peuvent également être désélectionnés.  Par exemple, si l’utilisateur inverse la direction lorsqu’il dessine le lasso, le <xref:System.Windows.Ink.IncrementalLassoHitTester> peut désélectionner certains traits.  
  
 Le <xref:System.Windows.Ink.IncrementalLassoHitTester> déclenche le <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> événement, ce qui permet à votre contrôle personnalisé répondre quand l’utilisateur dessine le lasso.  Par exemple, vous pouvez modifier l’apparence des traits lorsque l’utilisateur sélectionne et désélectionne les.  
  
## <a name="managing-the-ink-mode"></a>Gestion du Mode d’encre  
 Il est utile de l’utilisateur si le lasso apparaît différemment de l’encre sur votre contrôle. Pour ce faire, votre contrôle personnalisé doit de savoir si l’utilisateur est l’écriture ou en sélectionnant manuscrit. La façon la plus simple consiste à déclarer une énumération avec deux valeurs : une pour indiquer que l’utilisateur est l’écriture manuscrite et l’autre pour indiquer que l’utilisateur sélectionne de l’encre.  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Ensuite, ajoutez deux <xref:System.Windows.Ink.DrawingAttributes> à la classe : l’application à utiliser lorsque l’utilisateur écrit encre, un à utiliser lorsque l’utilisateur sélectionne l’encre.  Dans le constructeur, initialisez le <xref:System.Windows.Ink.DrawingAttributes> et attachez les deux <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> événements au même gestionnaire d’événements. Définissez ensuite le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriété de la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à l’encre <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Ajouter une propriété qui expose le mode de sélection. Lorsque l’utilisateur modifie le mode de sélection, définissez la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriété de la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> approprié <xref:System.Windows.Ink.DrawingAttributes> de l’objet, puis reconnectez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> propriété le <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Exposer le <xref:System.Windows.Ink.DrawingAttributes> comme propriétés pour que les applications puissent déterminer l’apparence des traits d’encre et des traits de sélection.  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Lorsqu’une propriété d’un <xref:System.Windows.Ink.DrawingAttributes> l’objet de modifications, la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> doit être rattachée à la <xref:System.Windows.Controls.InkPresenter>.  Dans le Gestionnaire d’événements pour le <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> événement, rattachez la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> à la <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>Utilisation d’IncrementalLassoHitTester  
 Créer et initialiser un <xref:System.Windows.Ink.StrokeCollection> qui contient les traits sélectionnés.  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Lorsque l’utilisateur commence à dessiner un tracé, d’encre ou le lasso, désélectionnez tous les traits sélectionnés. Puis, si l’utilisateur dessine un lasso, créez un <xref:System.Windows.Ink.IncrementalLassoHitTester> en appelant <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, s’abonner à la <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> événement, puis appelez <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Ce code peut être une méthode distincte et appelé à partir de la <xref:System.Windows.UIElement.OnStylusDown%2A> et <xref:System.Windows.UIElement.OnMouseDown%2A> méthodes.  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Ajoutez les points du stylet à le <xref:System.Windows.Ink.IncrementalLassoHitTester> pendant que l’utilisateur dessine le lasso.  Appelez la méthode suivante à partir de la <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, et <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> méthodes.  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Gérer les <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> événement répondre quand l’utilisateur sélectionne et désélectionne des traits.  Le <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> classe a la <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> et <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> qui obtiennent les traits qui ont été sélectionnés et désélectionnés, respectivement.  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Lorsque l’utilisateur termine de dessiner le lasso, annuler l’abonnement à la <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> événements et les appels <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Montage.  
 L’exemple suivant est un contrôle personnalisé qui permet à un utilisateur de sélectionner l’encre avec un lasso.  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [Création d'un contrôle d'entrée d'encre](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
