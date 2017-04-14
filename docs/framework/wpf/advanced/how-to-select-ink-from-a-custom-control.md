---
title: "Comment&#160;: s&#233;lectionner une encre &#224; partir d&#39;un contr&#244;le personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles, sélection de l'encre"
  - "contrôles personnalisés, sélection de l'encre"
  - "encre, sélectionner à partir d'un contrôle personnalisé"
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: s&#233;lectionner une encre &#224; partir d&#39;un contr&#244;le personnalis&#233;
En ajoutant un <xref:System.Windows.Ink.IncrementalLassoHitTester> à votre contrôle personnalisé, vous pouvez activer votre contrôle afin qu'un utilisateur puisse sélectionner de l'encre avec un outil lasso, semblable à la façon dont le <xref:System.Windows.Controls.InkCanvas> sélectionne l'encre avec un lasso.  
  
 Cet exemple suppose que vous sachiez créer un contrôle personnalisé prenant en charge l'écriture manuscrite.  Pour créer un contrôle personnalisé qui accepte l'entrée d'encre, consultez [Création d'un contrôle d'entrée d'encre](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
## Exemple  
 Lorsque l'utilisateur dessine un lasso, le <xref:System.Windows.Ink.IncrementalLassoHitTester> prévoit quels traits seront dans les limites du tracé du lasso lorsque l'utilisateur aura terminé le lasso.  Les traits déterminés pour être dans les limites du tracé du lasso peuvent être considérés comme sélectionnés.  Les traits sélectionnés peuvent également être désélectionnés.  Par exemple, si l'utilisateur inverse la direction lorsqu'il dessine le lasso, le <xref:System.Windows.Ink.IncrementalLassoHitTester> peut désélectionner certains traits.  
  
 Le <xref:System.Windows.Ink.IncrementalLassoHitTester> déclenche l'événement <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> qui permet à votre contrôle personnalisé de répondre pendant que l'utilisateur dessine le lasso.  Par exemple, vous pouvez modifier l'apparence des traits lorsque l'utilisateur les sélectionne et les désélectionne.  
  
## Gestion du mode d'entrée manuscrite  
 Il est utile à l'utilisateur si le lasso apparaît différemment de l'encre sur votre contrôle.  Pour cela, votre contrôle personnalisé doit déterminer si l'utilisateur écrit ou sélectionne de l'encre.  Pour ce faire, la méthode la plus simple consiste à déclarer une énumération avec deux valeurs : une pour indiquer que l'utilisateur écrit de l'encre et une pour indiquer que l'utilisateur sélectionne de l'encre.  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Ensuite, ajoutez deux <xref:System.Windows.Ink.DrawingAttributes> à la classe : un à utiliser lorsque l'utilisateur écrit de l'encre, un à utiliser lorsque l'utilisateur sélectionne de l'encre.  Dans le constructeur, initialisez <xref:System.Windows.Ink.DrawingAttributes> et attachez les deux événements <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> au même gestionnaire d'événements.  Puis, affectez la propriété <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> du <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> aux <xref:System.Windows.Ink.DrawingAttributes> de l'encre.  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Ajoutez une propriété qui expose le mode de sélection.  Lorsque l'utilisateur change le mode de sélection, affectez la propriété <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> du <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à l'objet <xref:System.Windows.Ink.DrawingAttributes> approprié, puis attachez de nouveau la Propriété <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> au <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Exposez les <xref:System.Windows.Ink.DrawingAttributes> comme propriétés pour que les applications puissent déterminer l'apparence des traits d'encre et des traits de sélection.  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Lorsqu'une propriété d'un objet <xref:System.Windows.Ink.DrawingAttributes> est modifiée, le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> doit de nouveau être attaché au <xref:System.Windows.Controls.InkPresenter>.  Dans le gestionnaire d'événements pour l'événement <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>, attachez de nouveau le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> au <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## Utilisation d'IncrementalLassoHitTester  
 Créez et initialisez un <xref:System.Windows.Ink.StrokeCollection> qui contient les traits sélectionnés.  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Lorsque l'utilisateur commence à dessiner un trait \(encre ou lasso\), désélectionnez tous les traits sélectionnés.  Puis, si l'utilisateur dessine un lasso, créez un <xref:System.Windows.Ink.IncrementalLassoHitTester> en appelant <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, abonnez\-vous à l'événement <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> et appelez <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.  Ce code peut être une méthode séparée et être appelé par les méthodes <xref:System.Windows.UIElement.OnStylusDown%2A> et <xref:System.Windows.UIElement.OnMouseDown%2A>.  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Ajoutez les points de stylet au <xref:System.Windows.Ink.IncrementalLassoHitTester> pendant que l'utilisateur dessine le lasso.  Appelez la méthode suivante à partir des méthodes <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A> et <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Gérez l'événement <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=fullName> pour répondre lorsque l'utilisateur sélectionne et désélectionne des traits.  La classe <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> dispose des propriétés <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> et <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> qui obtiennent respectivement les traits qui ont été sélectionnés et désélectionnés.  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Lorsque l'utilisateur termine de dessiner le lasso, annulez votre abonnement à l'événement <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> et appelez <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## Assemblage.  
 L'exemple suivant est un contrôle personnalisé qui permet à un utilisateur de sélectionner l'encre avec un lasso.  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>   
 <xref:System.Windows.Ink.StrokeCollection>   
 <xref:System.Windows.Input.StylusPointCollection>   
 [Création d'un contrôle d'entrée d'encre](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)