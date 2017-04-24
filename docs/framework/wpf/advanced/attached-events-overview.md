---
title: "Vue d&#39;ensemble des &#233;v&#233;nements attach&#233;s | Microsoft Docs"
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
  - "événements attachés (WPF), définition"
  - "événements attachés (WPF), scénarios pour"
  - "événements attachés comparés aux événements routés (WPF)"
  - "soutenir des événements attachés avec des événements routés (WPF)"
  - "définir des événements attachés en tant qu'événements routés (WPF)"
  - "gérer des événements attachés (WPF)"
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble des &#233;v&#233;nements attach&#233;s
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] définit un composant de langage et un type d'événement appelé *événement attaché*.  Le concept d'un événement attaché vous permet d'ajouter un gestionnaire pour un événement particulier à un élément arbitraire plutôt qu'à un élément qui définit réellement l'événement ou qui en hérite.  Dans ce cas, ni l'objet qui déclenche potentiellement l'événement ni l'instance de gestion de destination ne définit ou "possède" l'événement.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous avez lu [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md) et [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## Syntaxe d'événement attaché  
 Les événements attachés ont une syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et un modèle de codage qui doivent être utilisés par le code de stockage afin de prendre en charge l'utilisation des événements attachés.  
  
 Dans la syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], l'événement attaché est spécifié non seulement par son nom d'évènement, mais aussi par son type propriétaire, les deux étant séparés par un point \(.\).  Comme le nom de l'évènement est qualifié avec le nom de son type propriétaire, la syntaxe de l'événement attaché permet à celui\-ci d'être attaché à tout élément pouvant être instancié.  
  
 Par exemple, vous trouverez ci\-dessous la syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] requise pour joindre un gestionnaire pour un événement attaché `NeedsCleaning` personnalisé :  
  
 [!code-xml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Notez le préfixe `aqua:`; ce préfixe est nécessaire dans ce cas parce que l'événement attaché est un événement personnalisé qui provient d'un fichier xmlns mappé personnalisé.  
  
<a name="WPFImplements"></a>   
## Comment WPF implémente des événements attachés  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les événements attachés sont stockés par un champ <xref:System.Windows.RoutedEvent> et sont routés à travers l'arborescence après leur déclenchement.  En général, la source de l'événement attaché \(l'objet qui déclenche l'événement\) est une source système ou de service, et l'objet qui exécute le code qui déclenche l'événement ne fait pas par conséquent directement partie de l'arborescence d'éléments.  
  
<a name="Scenarios"></a>   
## Scénarios pour les événements attachés  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les événements attachés sont présent dans certaines fonctionnalités où figure l'abstraction de niveau de service, comme pour les événements activés par la classe statique <xref:System.Windows.Input.Mouse> ou la classe <xref:System.Windows.Controls.Validation>.  Les classes qui interagissent avec le service ou qui l'utilisent peuvent utiliser l'événement dans la syntaxe d'événement attaché, ou choisir de surfacer l'événement attaché comme un événement routé faisant partie de la manière dont la classe intègre les fonctionnalités du service.  
  
 Bien que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définisse plusieurs événements attachés, les scénarios où vous utiliserez ou gérerez directement l'événement attaché sont très limités.  En général, l'objet de l'événement attaché est architectural, mais il est ensuite transmis à un événement routé non attaché \(stocké avec un wrapper d'événement [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]\).  
  
 Par exemple, l'événement <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName> attaché sous\-jacent peut être plus facilement géré sur tout <xref:System.Windows.UIElement> donné en utilisant <xref:System.Windows.UIElement.MouseDown> sur ce <xref:System.Windows.UIElement> plutôt que de se servir de la syntaxe d'événement attaché dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou dans le code.  L'événement attaché a une fonction dans l'architecture parce qu'il permet dans l'avenir une extension des périphériques d'entrée.  Le périphérique hypothétique n'aurait qu'à déclencher <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=fullName> pour simuler une entrée par le biais de la souris et n'aurait pas besoin de dériver de <xref:System.Windows.Input.Mouse> pour ce faire.  Toutefois, ce scénario implique une gestion du code des événements, et une gestion [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de l'événement attaché n'est pas pertinente pour ce scénario.  
  
<a name="Handling"></a>   
## Gestion d'un événement attaché dans WPF  
 Le processus de gestion d'un événement attaché, et le code du gestionnaire que vous écrirez, est essentiellement le même que pour un événement routé.  
  
 En général, un événement attaché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n'est pas très différent d'un événement routé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Les différences portent sur la manière dont l'événement est alimenté et comment il est exposé par une classe comme un membre \(ce qui affecte également la syntaxe du gestionnaire [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]\).  
  
 Toutefois, comme noté précédemment, les événements attachés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existants ne sont pas prévus en particulier pour une gestion dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Plus souvent, le but de l'événement est de permettre à un élément composé de signaler un état à un élément parent dans la composition, auquel cas l'événement est généralement déclenché dans le code et compte également sur la gestion de classe dans la classe parente pertinente.  Par exemple, les éléments dans un <xref:System.Windows.Controls.Primitives.Selector> sont supposés déclencher l'événement <xref:System.Windows.Controls.Primitives.Selector.Selected> attaché, qui est ensuite géré par classe par la classe <xref:System.Windows.Controls.Primitives.Selector> , puis potentiellement converti par la classe <xref:System.Windows.Controls.Primitives.Selector> en un événement routé différent, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>.  Pour plus d'informations sur les événements routés la et gestion de classe, consultez [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## Définition de vos propres événements attachés comme événements routés  
 Si vous dérivez de classes de base [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] communes, vous pouvez implémenter vos propres événements attachés en incluant certaines méthodes de modèle dans votre classe et en utilisant des méthodes utilitaires déjà présentes sur les classes de base.  
  
 Le modèle est le suivant :  
  
-   Une méthode `Add*Handler` avec deux paramètres.  Le premier paramètre doit identifier l'événement, et l'événement identifié doit correspondre aux noms avec le \* dans le nom de méthode.  Le second paramètre est le gestionnaire à ajouter.  La méthode doit être publique et statique, sans valeur de retour.  
  
-   Une méthode `Remove*Handler` avec deux paramètres.  Le premier paramètre doit identifier l'événement, et l'événement identifié doit correspondre aux noms avec le \* dans le nom de méthode.  Le second paramètre est le gestionnaire à supprimer.  La méthode doit être publique et statique, sans valeur de retour.  
  
 La méthode d'accesseur `Add*Handler` facilite le traitement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lorsque les attributs de gestionnaire d'événements attachés sont déclarés sur un élément.  Les méthodes `Add*Handler` et `Remove*Handler` activent également l'accès du code au magasin de gestionnaires d'événements pour l'événement attaché.  
  
 Ce modèle général n'est pas encore assez précis pour une implémentation pratique dans une infrastructure, parce que toute implémentation donnée de lecteur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peut avoir des méthodes différentes pour identifier des événements sous\-jacents dans le langage et l'architecture de prise en charge.  C'est l'une des raisons pour lesquelles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémente les événements attachés comme des événements routés ; l'identificateur à utiliser pour un événement \(<xref:System.Windows.RoutedEvent>\) est déjà défini par le système d'événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  De plus, router un événement est une extension d'implémentation naturelle sur le concept de niveau de langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d'un événement attaché.  
  
 L'implémentation de `Add*Handler` pour un événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] attaché consiste à appeler le <xref:System.Windows.UIElement.AddHandler%2A> avec l'événement routé et le gestionnaire comme arguments.  
  
 Cette stratégie d'implémentation et le système d'événement routé en général restreignent la gestion pour les événements attachés aux classes dérivées <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement>, parce que seules ces classes possèdent des implémentations <xref:System.Windows.UIElement.AddHandler%2A>.  
  
 Par exemple, le code suivant définit l'événement attaché `NeedsCleaning` sur la classe propriétaire `Aquarium` à l'aide de la stratégie d'événement attaché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui consiste à déclarer l'événement attaché comme un événement routé.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Notez que la méthode utilisée pour établir le champ de l'identificateur de l'événement attaché, <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, est en fait la même méthode que celle utilisée pour enregistrer un événement routé non attaché.  Les événements attachés et les événements routés sont tous enregistrés dans un magasin interne centralisé.  Cette implémentation du magasin d'événements active la considération conceptuelle "événements comme une interface" traitée dans [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## Déclenchement d'un événement WPF attaché  
 Vous n'avez généralement pas besoin de déclencher des événements attachés définis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir de votre code.  Ces événements suivent le modèle conceptuel général de "service", et des classes de service telles que <xref:System.Windows.Input.InputManager> sont chargées de déclencher les événements.  
  
 Toutefois, si vous définissez un événement attaché personnalisé basé sur le modèle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui consiste à baser des événements attachés sur <xref:System.Windows.RoutedEvent>, vous pouvez utiliser <xref:System.Windows.UIElement.RaiseEvent%2A> pour déclencher un événement attaché à partir de tout <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement>.  Le déclenchement d'un événement routé \(attaché ou non\) nécessite que vous déclariez un élément particulier dans l'arborescence d'éléments comme source de l'événement ; cette source est signalée comme appelant <xref:System.Windows.UIElement.RaiseEvent%2A>.  Il incombe à votre service de déterminer quel élément est signalé comme source dans l'arborescence.  
  
## Voir aussi  
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)   
 [XAML et classes personnalisées pour WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)