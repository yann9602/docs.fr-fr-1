---
title: "Vue d&#39;ensemble du focus | Microsoft Docs"
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
  - "applications, focus"
  - "focus dans des applications"
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Vue d&#39;ensemble du focus
Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il existe deux concepts principaux associés au focus : le focus clavier et le focus logique.  Le focus clavier fait référence à l'élément qui reçoit une entrée au clavier, tandis que le focus logique fait référence à l'élément d'une portée de focus qui a le focus.  Ces concepts sont présentés en détail dans cette vue d'ensemble.  Il est important de bien comprendre les différences entre ces concepts lors de la création d'applications complexes qui comportent plusieurs régions où le focus peut être obtenu.  
  
 Les principales classes impliquées par la gestion du focus sont les classes <xref:System.Windows.Input.Keyboard> et <xref:System.Windows.Input.FocusManager>, ainsi que les classes d'élément de base telles que <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement>.  Pour plus d'informations sur les éléments de base, consultez [Vue d'ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  
  
 La classe <xref:System.Windows.Input.Keyboard> est principalement responsable du focus clavier et la classe <xref:System.Windows.Input.FocusManager> du focus logique. Il ne s'agit toutefois pas d'une distinction absolue.  En effet, un élément qui a le focus clavier possède également le focus logique, tandis qu'un élément qui a le focus logique ne possède pas nécessairement le focus clavier.  Ce principe se vérifie lorsque vous utilisez la classe <xref:System.Windows.Input.Keyboard> pour définir l'élément qui a le focus clavier, car elle définit également le focus logique sur l'élément.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Keyboard_Focus"></a>   
## Focus clavier  
 Le focus clavier fait référence à l'élément qui reçoit actuellement l'entrée au clavier.  Un seul élément de l'ordinateur peut avoir le focus clavier.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.IInputElement.IsKeyboardFocused%2A>, l'élément qui a le focus clavier sera affecté de `true`.  La propriété statique <xref:System.Windows.Input.Keyboard.FocusedElement%2A> de la classe <xref:System.Windows.Input.Keyboard> obtient l'élément qui a actuellement le focus clavier.  
  
 Pour qu'un élément puisse obtenir le focus clavier, les propriétés <xref:System.Windows.UIElement.Focusable%2A> et <xref:System.Windows.UIElement.IsVisible%2A> doivent avoir la valeur `true` pour les éléments de base.  Pour certaines classes, comme la classe de base <xref:System.Windows.Controls.Panel>, <xref:System.Windows.UIElement.Focusable%2A> a par défaut la valeur `false`. Par conséquent, vous devez définir <xref:System.Windows.UIElement.Focusable%2A> sur la valeur `true` si vous souhaitez que ce type d'élément puisse obtenir le focus clavier.  
  
 Le focus clavier peut être obtenu par intervention de l'utilisateur à l'aide de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] \(tabulation vers un élément ou clic de souris sur certains éléments, par exemple\).  Le focus clavier peut également être obtenu par programmation en utilisant la méthode <xref:System.Windows.Input.Keyboard.Focus%2A> sur la classe <xref:System.Windows.Input.Keyboard>.  La méthode <xref:System.Windows.Input.Keyboard.Focus%2A> tente d'accorder le focus clavier à l'élément spécifié.  L'élément retourné correspond à l'élément qui a le focus clavier. Il peut s'agir d'un autre élément que celui demandé si l'objet de focus précédent ou le nouveau bloque la demande.  
  
 L'exemple suivant utilise la méthode <xref:System.Windows.Input.Keyboard.Focus%2A> pour placer le focus clavier sur un <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 La propriété <xref:System.Windows.UIElement.IsKeyboardFocused%2A> des classes d'élément de base obtient une valeur qui indique si l'élément a le focus clavier.  La propriété <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> des classes d'élément de base obtient une valeur qui indique si l'élément ou l'un de ses éléments enfants visuels a le focus clavier.  
  
 Lors de la configuration du focus initial au démarrage de l'application, l'élément devant recevoir le focus doit se situer dans l'arborescence d'éléments visuels de la fenêtre initiale chargée par l'application, et la valeur `true` doit être affectée à <xref:System.Windows.UIElement.Focusable%2A> et <xref:System.Windows.UIElement.IsVisible%2A>.  Il est recommandé de définir le focus initial dans le gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded>.  Un rappel <xref:System.Windows.Threading.Dispatcher> peut également être utilisé en appelant <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## Focus logique  
 Le focus logique fait référence à l'<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=fullName> dans une portée de focus.  Une portée de focus est un élément qui effectue le suivi de <xref:System.Windows.Input.FocusManager.FocusedElement%2A> dans sa portée.  Lorsque le focus clavier quitte une portée de focus, l'élément ayant le focus perd le focus clavier, mais il conserve le focus logique.  Lorsque le focus clavier revient dans la portée de focus, l'élément ayant le focus obtient le focus clavier.  Cela permet au focus clavier de changer entre des portées de focus et de s'assurer que l'élément ayant le focus dans la portée de focus retrouve le focus clavier lorsque le focus revient dans la portée de focus.  
  
 Plusieurs éléments d'une application peuvent avoir le focus logique, mais un seul élément peut avoir le focus logique dans une portée de focus donnée.  
  
 Un élément ayant le focus clavier a également le focus logique pour la portée de focus à laquelle il appartient.  
  
 Un élément peut être converti en portée de focus en langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en affectant à la propriété jointe <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> de <xref:System.Windows.Input.FocusManager> la valeur `true`.  Dans le code, cette conversion peut être réalisée en appelant <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 L'exemple suivant convertit un <xref:System.Windows.Controls.StackPanel> en portée de focus en définissant la propriété attachée <xref:System.Windows.Input.FocusManager.IsFocusScope%2A>.  
  
 [!code-xml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> retourne la portée de focus pour l'élément spécifié.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les classes ayant des portées de focus par défaut sont <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar> et <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> reçoit l'élément ayant le focus pour la portée de focus spécifiée.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> définit l'élément ayant le focus dans la portée de focus spécifiée.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> est généralement utilisé pour définir l'élément ayant le focus initial.  
  
 L'exemple suivant définit l'élément ayant le focus dans une portée de focus et obtient l'élément ayant le focus d'une portée de focus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## Navigation au clavier  
 La classe <xref:System.Windows.Input.KeyboardNavigation> est chargée d'implémenter la navigation du focus clavier par défaut lorsque l'utilisateur appuie sur l'une des touches de navigation.  Les touches de navigation sont les suivantes : TAB, MAJ\+TAB, CTRL\+TAB, CTRL\+MAJ\+TAB, FLÈCHE HAUT, FLÈCHE BAS, FLÈCHE GAUCHE et FLÈCHE DROITE.  
  
 Le comportement de navigation d'un conteneur de navigation peut être modifié en définissant les propriétés attachées <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> et <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> de <xref:System.Windows.Input.KeyboardNavigation>.  Ces propriétés sont du type <xref:System.Windows.Input.KeyboardNavigationMode> et les valeurs possibles sont <xref:System.Windows.Input.KeyboardNavigationMode>, <xref:System.Windows.Input.KeyboardNavigationMode>, <xref:System.Windows.Input.KeyboardNavigationMode>, <xref:System.Windows.Input.KeyboardNavigationMode>, <xref:System.Windows.Input.KeyboardNavigationMode> et <xref:System.Windows.Input.KeyboardNavigationMode>.  La valeur par défaut \(<xref:System.Windows.Input.KeyboardNavigationMode>\) indique que l'élément ne correspond pas à un conteneur de navigation.  
  
 L'exemple suivant crée un <xref:System.Windows.Controls.Menu> contenant plusieurs objets <xref:System.Windows.Controls.MenuItem>.  La propriété attachée <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> a la valeur <xref:System.Windows.Input.KeyboardNavigationMode> dans <xref:System.Windows.Controls.Menu>.  Lorsque le focus est modifié à l'aide de la touche Tab dans <xref:System.Windows.Controls.Menu>, il se détache de chaque élément, puis retourne au premier élément une fois qu'il a atteint le dernier.  
  
 [!code-xml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## Navigation du focus par programme  
 <xref:System.Windows.UIElement.MoveFocus%2A> et <xref:System.Windows.UIElement.PredictFocus%2A> constituent des [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] supplémentaires permettant d'utiliser le focus.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> fait passer le focus à l'élément suivant dans l'application.  Un <xref:System.Windows.Input.TraversalRequest> est utilisé pour spécifier la direction.  Le <xref:System.Windows.Input.FocusNavigationDirection> passé à <xref:System.Windows.UIElement.MoveFocus%2A> spécifie les différentes directions du focus, comme <xref:System.Windows.Input.FocusNavigationDirection>, <xref:System.Windows.Input.FocusNavigationDirection>, <xref:System.Windows.Input.FocusNavigationDirection> et <xref:System.Windows.Input.FocusNavigationDirection>.  
  
 L'exemple suivant utilise <xref:System.Windows.FrameworkElement.MoveFocus%2A> pour modifier l'élément ayant le focus.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> retourne l'objet qui recevrait le focus si celui\-ci venait à changer.  Actuellement, seuls <xref:System.Windows.Input.FocusNavigationDirection>, <xref:System.Windows.Input.FocusNavigationDirection>, <xref:System.Windows.Input.FocusNavigationDirection> et <xref:System.Windows.Input.FocusNavigationDirection> sont pris en charge par <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## Événements de focus  
 Les événements liés au focus clavier sont <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> et <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Les événements sont définis en tant qu'événements attachés dans la classe <xref:System.Windows.Input.Keyboard>. Il est toutefois plus facile d'y accéder s'ils correspondent à des événements routés équivalents dans les classes d'élément de base.  Pour plus d'informations sur les événements, consultez [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> est déclenché lorsque l'élément obtient le focus clavier.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> est déclenché lorsque l'élément perd le focus clavier.  Le focus ne change pas si l'événement <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> ou <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> est géré et que <xref:System.Windows.RoutedEventArgs.Handled%2A> a la valeur `true`.  
  
 L'exemple suivant attache les gestionnaires d'événements <xref:System.Windows.UIElement.GotKeyboardFocus> et <xref:System.Windows.UIElement.LostKeyboardFocus> à un <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Lorsque <xref:System.Windows.Controls.TextBox> obtient le focus clavier, la propriété <xref:System.Windows.Controls.Control.Background%2A> de <xref:System.Windows.Controls.TextBox> est remplacée par <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Lorsque <xref:System.Windows.Controls.TextBox> perd le focus clavier, la propriété <xref:System.Windows.Controls.Control.Background%2A> de <xref:System.Windows.Controls.TextBox> reprend la couleur blanche.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Les événements liés au focus logique sont <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.  Ces événements sont définis dans le <xref:System.Windows.Input.FocusManager> en tant qu'événements attachés. Toutefois, le <xref:System.Windows.Input.FocusManager> n'expose pas les wrappers d'événement CLR.  <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement> exposent ces événements sous une forme plus pratique.  
  
## Voir aussi  
 <xref:System.Windows.Input.FocusManager>   
 <xref:System.Windows.UIElement>   
 <xref:System.Windows.ContentElement>   
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [Vue d'ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)