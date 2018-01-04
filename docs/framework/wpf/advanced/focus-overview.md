---
title: Vue d'ensemble du focus
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
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d35b65f88452085e601569b9dcfc62a541a1655f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="focus-overview"></a>Vue d'ensemble du focus
Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], il existe deux concepts principaux associés au focus : le focus clavier et le focus logique.  Le focus clavier fait référence à l’élément qui reçoit une entrée au clavier, tandis que le focus logique fait référence à l’élément d’une portée de focus qui a le focus.  Ces concepts sont présentés en détail dans cette vue d’ensemble.  Il est important de bien comprendre les différences entre ces concepts lors de la création d’applications complexes qui comportent plusieurs régions où le focus peut être obtenu.  
  
 Les principales classes impliquées dans la gestion du focus sont les <xref:System.Windows.Input.Keyboard> (classe), le <xref:System.Windows.Input.FocusManager> classe et l’élément de base des classes, telles que <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement>.  Pour plus d’informations sur les éléments de base, consultez [Vue d’ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md).  
  
 Le <xref:System.Windows.Input.Keyboard> classe concerne principalement avec le focus clavier et la <xref:System.Windows.Input.FocusManager> concerne principalement avec le focus logique, mais cette distinction absolue n’est pas.  En effet, un élément qui a le focus clavier possède également le focus logique, tandis qu’un élément qui a le focus logique ne possède pas nécessairement le focus clavier.  Ces informations s’affichent lorsque vous utilisez la <xref:System.Windows.Input.Keyboard> classe pour définir l’élément qui a le focus clavier, pour qu’il définit également le focus logique sur l’élément.  
  

  
<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>Focus clavier  
 Le focus clavier fait référence à l’élément qui reçoit l’entrée au clavier.  Un seul élément de l’ordinateur peut avoir le focus clavier.  Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l’élément qui a le focus clavier possède <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> la valeur `true`.  La propriété statique <xref:System.Windows.Input.Keyboard.FocusedElement%2A> sur la <xref:System.Windows.Input.Keyboard> classe obtient l’élément qui a le focus clavier.  
  
 Dans l’ordre d’un élément obtenir le focus clavier, le <xref:System.Windows.UIElement.Focusable%2A> et <xref:System.Windows.UIElement.IsVisible%2A> propriétés sur les éléments de base doivent être définies sur `true`.  Certaines classes, telles que la <xref:System.Windows.Controls.Panel> classe de base, avoir <xref:System.Windows.UIElement.Focusable%2A> la valeur `false` par défaut ; par conséquent, vous devez définir <xref:System.Windows.UIElement.Focusable%2A> à `true` si vous souhaitez que ce type d’élément puisse obtenir le focus clavier.  
  
 Le focus clavier peut être obtenu par interaction de l’utilisateur avec l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (tabulation vers un élément ou clic de souris sur certains éléments, par exemple).  Le focus clavier peuvent également être obtenu par programmation à l’aide de la <xref:System.Windows.Input.Keyboard.Focus%2A> méthode sur la <xref:System.Windows.Input.Keyboard> classe.  Le <xref:System.Windows.Input.Keyboard.Focus%2A> méthode essaie de donner le focus clavier de l’élément spécifié.  L’élément retourné correspond à l’élément qui a le focus clavier. Il peut s’agir d’un autre élément que celui demandé si l’objet de focus précédent ou nouveau bloque la demande.  
  
 L’exemple suivant utilise le <xref:System.Windows.Input.Keyboard.Focus%2A> pour définir le focus clavier sur un <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 Le <xref:System.Windows.UIElement.IsKeyboardFocused%2A> propriété sur les classes d’élément de base Obtient une valeur qui indique si l’élément a le focus clavier.  Le <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> propriété sur les classes d’élément de base Obtient une valeur indiquant si l’élément ou l’un de ses éléments enfants visuels a le focus clavier.  
  
 Lors de la définition du focus initial au démarrage de l’application, l’élément devant recevoir le focus doit être dans l’arborescence d’éléments visuels de la fenêtre initiale chargée par l’application, et l’élément doit avoir <xref:System.Windows.UIElement.Focusable%2A> et <xref:System.Windows.UIElement.IsVisible%2A> la valeur `true`.  Est recommandé de définir le focus initial dans le <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements.  A <xref:System.Windows.Threading.Dispatcher> rappel peut également être utilisé en appelant <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>.  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>Focus logique  
 Le focus logique fait référence à la <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> dans une portée de focus.  Une portée de focus est un élément qui effectue le suivi de le <xref:System.Windows.Input.FocusManager.FocusedElement%2A> dans son étendue.  Quand le focus clavier quitte une portée de focus, l’élément ayant le focus perd le focus clavier, mais conserve le focus logique.  Quand le focus clavier revient dans la portée de focus, l’élément ayant le focus obtient le focus clavier.  Cela permet au focus clavier de changer entre des portées de focus et de s’assurer que l’élément ayant le focus dans la portée de focus retrouve le focus clavier quand le focus revient dans la portée de focus.  
  
 Plusieurs éléments d’une application peuvent avoir le focus logique, mais un seul élément peut avoir le focus logique dans une portée de focus donnée.  
  
 Un élément ayant le focus clavier a également le focus logique pour la portée de focus à laquelle il appartient.  
  
 Un élément peut être transformé en une portée de focus dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] en définissant le <xref:System.Windows.Input.FocusManager> propriété attachée <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> à `true`.  Dans le code, un élément peut être transformé en une portée de focus en appelant <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>.  
  
 L’exemple suivant effectue une <xref:System.Windows.Controls.StackPanel> dans une portée de focus en définissant le <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> propriété jointe.  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>Retourne la portée de focus pour l’élément spécifié.  
  
 Classes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ayant des portées de focus par défaut sont <xref:System.Windows.Window>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.ToolBar>, et <xref:System.Windows.Controls.ContextMenu>.  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>Obtient l’élément ayant le focus pour la portée de focus spécifié.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>définit l’élément ayant le focus dans la portée de focus spécifié.  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>est généralement utilisé pour définir l’élément ayant le focus initial.  
  
 L’exemple suivant définit l’élément ayant le focus dans une portée de focus et obtient l’élément ayant le focus d’une portée de focus.  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>Navigation au clavier  
 La <xref:System.Windows.Input.KeyboardNavigation> classe est chargée d’implémenter la navigation du focus clavier par défaut lorsque l’utilisateur appuie sur une des clés de navigation.  Les touches de navigation sont les suivantes : TAB, MAJ+TAB, CTRL+TAB, CTRL+MAJ+TAB, FLÈCHE HAUT, FLÈCHE BAS, FLÈCHE GAUCHE et FLÈCHE DROITE.  
  
 Le comportement de navigation d’un conteneur de navigation peut être modifié en définissant le fichier joint <xref:System.Windows.Input.KeyboardNavigation> propriétés <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>, <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>, et <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>.  Ces propriétés sont de type <xref:System.Windows.Input.KeyboardNavigationMode> et les valeurs possibles sont <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, <xref:System.Windows.Input.KeyboardNavigationMode.Local>, <xref:System.Windows.Input.KeyboardNavigationMode.Contained>, <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>, <xref:System.Windows.Input.KeyboardNavigationMode.Once>, et <xref:System.Windows.Input.KeyboardNavigationMode.None>.  La valeur par défaut est <xref:System.Windows.Input.KeyboardNavigationMode.Continue>, ce qui signifie que l’élément n’est pas un conteneur de navigation.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Menu> avec un nombre de <xref:System.Windows.Controls.MenuItem> objets.  Le <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> a la valeur de propriété jointe <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> sur la <xref:System.Windows.Controls.Menu>.  Lorsque le focus est modifié à l’aide de la touche tab dans le <xref:System.Windows.Controls.Menu>, se détache de chaque élément, puis retourne au premier élément qu’il est atteint le dernier élément.  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>Navigation du focus par programmation  
 Autres [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] pour travailler avec le focus sont <xref:System.Windows.UIElement.MoveFocus%2A> et <xref:System.Windows.UIElement.PredictFocus%2A>.  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>fait passer le focus à l’élément suivant dans l’application.  A <xref:System.Windows.Input.TraversalRequest> est utilisé pour spécifier la direction.   Le <xref:System.Windows.Input.FocusNavigationDirection> passé à <xref:System.Windows.UIElement.MoveFocus%2A> Spécifie le différentes directions du focus peut être déplacé, tel que <xref:System.Windows.Input.FocusNavigationDirection.First>, <xref:System.Windows.Input.FocusNavigationDirection.Last>, <xref:System.Windows.Input.FocusNavigationDirection.Up> et <xref:System.Windows.Input.FocusNavigationDirection.Down>.  
  
 L’exemple suivant utilise <xref:System.Windows.FrameworkElement.MoveFocus%2A> pour modifier l’élément ayant le focus.  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>Retourne l’objet qui recevrait le focus si celui-ci venait à être modifié.  Actuellement, seuls <xref:System.Windows.Input.FocusNavigationDirection.Up>, <xref:System.Windows.Input.FocusNavigationDirection.Down>, <xref:System.Windows.Input.FocusNavigationDirection.Left>, et <xref:System.Windows.Input.FocusNavigationDirection.Right> sont pris en charge par <xref:System.Windows.FrameworkElement.PredictFocus%2A>.  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>Événements de focus  
 Les événements liés au focus clavier sont <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>, <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> et <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>, <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>.  Les événements sont définis en tant qu’événements attachés sur le <xref:System.Windows.Input.Keyboard> de classe, mais ne sont plus accessibles en tant qu’événements routés équivalents sur les classes d’élément de base.  Pour plus d’informations sur les événements, consultez [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>est déclenché lorsque l’élément obtient le focus clavier.  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>est déclenché lorsque l’élément perd le focus clavier.  Si le <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> événement ou la <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> événement est géré et <xref:System.Windows.RoutedEventArgs.Handled%2A> est défini sur `true`, puis le focus ne change pas.  
  
 L’exemple suivant joint <xref:System.Windows.UIElement.GotKeyboardFocus> et <xref:System.Windows.UIElement.LostKeyboardFocus> gestionnaires d’événements à un <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 Lorsque le <xref:System.Windows.Controls.TextBox> Obtient le focus clavier, le <xref:System.Windows.Controls.Control.Background%2A> propriété de la <xref:System.Windows.Controls.TextBox> est remplacée par <xref:System.Windows.Media.Brushes.LightBlue%2A>.  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 Lorsque le <xref:System.Windows.Controls.TextBox> perd le focus clavier, le <xref:System.Windows.Controls.Control.Background%2A> propriété de la <xref:System.Windows.Controls.TextBox> repasse au blanc.  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 Les événements liés au focus logique sont <xref:System.Windows.UIElement.GotFocus> et <xref:System.Windows.UIElement.LostFocus>.  Ces événements sont définis sur le <xref:System.Windows.Input.FocusManager> en tant qu’événements attachés, mais la <xref:System.Windows.Input.FocusManager> n’expose pas les wrappers d’événement CLR.  <xref:System.Windows.UIElement>et <xref:System.Windows.ContentElement> exposent ces événements plus facilement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Input.FocusManager>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.ContentElement>  
 [Vue d’ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Vue d’ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
