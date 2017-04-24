---
title: "Architecture de WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affinité de thread"
  - "architecture"
  - "propriétés jointes"
  - "classes, System.Object"
  - "classes, System.Threading.DispatcherObject"
  - "classes, System.Windows.Controls.Control"
  - "classes, System.Windows.DependencyObject"
  - "classes, System.Windows.FrameworkElement"
  - "classes, System.Windows.Media.Visual"
  - "classes, System.Windows.UIElement"
  - "CommandBindings"
  - "composants, unmanaged"
  - "Control (classe)"
  - "modèles de données"
  - "DependencyObject (classe)"
  - "DispatcherObject (classe)"
  - "FrameworkElement (classe)"
  - "INotifyPropertyChange (interface)"
  - "interfaces, INotifyPropertyChange"
  - "milcore"
  - "algorithme du peintre"
  - "propriétés, attachées"
  - "Animations"
  - "System.Object (classe)"
  - "System.Threading.DispatcherObject (classe)"
  - "System.Windows.Controls.Control (classe)"
  - "System.Windows.DependencyObject (classe)"
  - "System.Windows.FrameworkElement (classe)"
  - "System.Windows.Media.Visual (classe)"
  - "System.Windows.UIElement (classe)"
  - "thread, affinité"
  - "UIElement (classe)"
  - "composants non managés"
  - "Visual (classe)"
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Architecture de WPF
Cette rubrique propose une visite guidée de la hiérarchie des classes [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  Elle couvre la plupart des principaux sous\-systèmes de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], et décrit la façon dont ils interagissent.  Elle passe également en revue certains choix opérés par les architectes de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
   
  
<a name="System_Object"></a>   
## System.Object  
 Le modèle de programmation [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] principal est exposé via le code managé.  Très tôt dans la phase de conception de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], il y a eu un certain nombre de débats quant à l'endroit où tracer la ligne de démarcation entre les composants managés du système et les composants non managés.  Le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] fournit un certain nombre de fonctions qui rendent le développement plus productif et robuste \(notamment la gestion de la mémoire, la gestion des erreurs, le système de type commun \(CTS, Common Type System\), etc.\), mais elles ne sont pas sans coût.  
  
 Les principaux composants de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont illustrés dans la figure ci\-dessous.  Les sections rouges du diagramme \(PresentationFramework, PresentationCore et milcore\) sont les principales parties du code de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Parmi celles\-ci, une seule correspond à un composant non managé – milcore.  Milcore est écrit en code non managé afin de permettre une forte intégration avec [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)].  Tout l'affichage dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] s'effectue via le moteur [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], pour un rendu matériel et logiciel efficace.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nécessitait également un contrôle renforcé sur la mémoire et l'exécution.  Le moteur de composition dans milcore est extrêmement sensible aux performances, et nécessitait le renoncement à de nombreux avantages de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pour réaliser un gain de performances.  
  
 ![Position de WPF dans le .NET Framework.](../../../../docs/framework/wpf/advanced/media/wpf-architect1.png "wpf\_architect1")  
  
 La communication entre les parties managée et non managée de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est abordée plus loin dans cette rubrique.  Le reste du modèle de programmation managé est décrit ci\-dessous.  
  
<a name="System_Threading_DispatcherObject"></a>   
## System.Threading.DispatcherObject  
 La plupart des objets dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dérivent de <xref:System.Windows.Threading.DispatcherObject>, qui fournit les constructions de base pour la gestion de la concurrence et des threads.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est basé sur un système de messagerie implémenté par le répartiteur.  Ceci fonctionne un peu à l'image de la bien connue pompe de messages [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ; en fait, le répartiteur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise des messages User32 pour effectuer des appels à travers les threads.  
  
 Il existe en fait deux concepts fondamentaux qu'il faut bien comprendre quand il s'agit de l'accès concurrentiel [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – le répartiteur et l'affinité de thread.  
  
 Pendant la phase de conception [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], le but était de passer à un thread unique  d'exécution, mais un modèle « affinitisé » non\-thread.  L'affinité de thread se produit quand un composant utilise l'identité du thread d'exécution pour stocker un type d'état.  Sa forme la plus courante est d'utiliser le stockage local des threads ou TLS \(Thread Local Store\) pour stocker l'état.  L'affinité de thread requiert que chaque thread logique d'exécution soit la propriété d'un seul thread physique dans le système d'exploitation, qui peut devenir à forte intensité de mémoire.  Au final, le modèle de thread WPF est resté synchronisé avec le modèle existant de thread User32 d'exécution thread unique avec affinité de thread.  La raison principale de ceci est l'interopérabilité – des systèmes comme [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], le Presse\-papiers et Internet Explorer qui exigent tous une exécution de type STA \(Single Thread Affinity\).  
  
 Dans la mesure où vous avez des objets avec des threads STA, vous avez besoin d'un mode de communication entre les threads, et de valider que vous êtes sur le thread approprié.  C'est là que se situe le rôle du répartiteur.  Le répartiteur est un système de répartition de messages de base, avec plusieurs files d'attente de priorités différentes.  Les exemples de messages incluent les notifications d'entrée brute \(souris déplacée\), des fonctions d'infrastructure \(disposition\) ou des commandes utilisateur \(exécuter cette méthode\).  En dérivant de <xref:System.Windows.Threading.DispatcherObject>, vous créez un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] doté d'un comportement STA , et obtenez un pointeur vers un répartiteur au moment de la création.  
  
<a name="System_Windows_DependencyObject"></a>   
## System.Windows.DependencyObject  
 L'une des principales philosophies d'architecture utilisées dans la construction de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reposait sur une préférence pour les propriétés par rapport aux méthodes ou événements.  Les propriétés sont déclaratives et permettent de spécifier plus facilement l'intention au lieu de l'action.  Cela prenait également en charge un système piloté par un modèle, ou piloté par des données, pour afficher le contenu de l'interface utilisateur.  Cette philosophie produisait l'effet voulu de créer davantage de propriétés qu'il n'en fallait pour établir des liaisons, afin de mieux contrôler le comportement d'une application.  
  
 Pour que le système soit davantage piloté par les propriétés, un système de propriétés plus riche que celui fourni par [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] était nécessaire.  Un exemple simple de cette richesse est celui des notifications des modifications.  Pour permettre une liaison bidirectionnelle, les deux côtés de la liaison doivent prendre en charge la notification de changement.  Pour que le comportement soit lié aux valeurs de propriétés, vous devez être notifié en cas de changement d'une valeur de propriété.  Le [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] possède une interface, **INotifyPropertyChange**, qui permet à un objet de publier des notifications de changement, même s'il s'agit d'une option.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit un système de propriétés plus riche, dérivé du type <xref:System.Windows.DependencyObject>.  Le système de propriétés est véritablement un système de propriétés de « dépendance » dans la mesure où il suit les dépendances entre les expressions de propriété et revalide automatiquement les valeurs des propriétés lorsque les dépendances changent.  Par exemple, si vous avez une propriété qui hérite \(comme <xref:System.Windows.Controls.Control.FontSize%2A>\), le système est automatiquement mis à jour si la propriété change sur un parent d'un élément qui hérite de la valeur.  
  
 La fondation du système de propriétés [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est le concept d'une expression de propriété.  Lors de la première version de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], le système d'expressions de propriété est fermé, et les expressions sont toutes fournies dans le cadre de l'infrastructure.  Les expressions expliquent pourquoi le système de propriétés n'a pas de liaison de données, de styles ou d'héritage codé en dur, mais tout ceci est fourni par des couches ultérieures dans l'infrastructure.  
  
 Le système de propriétés fournit également un stockage limité des valeurs de propriétés.  Dans la mesure où les objets ont des douzaines \(voire des centaines\) de propriétés, et que la plupart des valeurs conservent leur état par défaut \(hérité, défini par les styles, etc.\), toutes les instances d'un objet n'ont pas besoin d'avoir tout le poids de chaque propriété défini sur elles.  
  
 La nouvelle fonctionnalité définitive du système de propriétés est la notion de [propriétés jointes](GTMT).  Les éléments [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reposent sur le principe de composition et de réutilisation des composants.  Il arrive souvent qu'un élément conteneur \(par exemple, un élément de disposition <xref:System.Windows.Controls.Grid>\) ait besoin de données supplémentaires sur des éléments enfants pour contrôler son comportement \(informations Ligne\/Colonne, par exemple\).  Au lieu d'associer toutes ces propriétés dans chaque élément, tout objet est autorisé à fournir des définitions de propriétés pour tout autre objet.  Ceci est similaire aux fonctions « expando » de JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## System.Windows.Media.Visual  
 Lorsqu'un système est défini, la prochaine étape est l'obtention de pixels dessinés sur l'écran.  La classe <xref:System.Windows.Media.Visual> assure la génération d'une arborescence d'objets visuels, chacun contenant éventuellement des instructions de dessin et des métadonnées relatives au rendu de ces instructions \(découpage, transformation, etc.\).  <xref:System.Windows.Media.Visual> est conçu pour être extrêmement léger et flexible. Par conséquent, la plupart des fonctionnalités n'ont pas d'exposition d'[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] publique et dépendent fortement des fonctions de rappel protégées.  
  
 <xref:System.Windows.Media.Visual> est vraiment le point d'entrée du système de composition [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  <xref:System.Windows.Media.Visual> est le point de connexion entre ces deux sous\-systèmes, les [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] managées et le milcore non managé.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] affiche les données en parcourant les structures de données non managées managées par le milcore.  Ces structures, appelées nœuds de composition, représentent un arborescence d'affichage hiérarchique avec des instructions de rendu à chaque nœud.  Cette arborescence, illustrée côté droit de la figure ci\-dessus, est accessible uniquement par l'intermédiaire d'un protocole de messagerie.  
  
 Lors de la programmation de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous créez des éléments <xref:System.Windows.Media.Visual>, et des types dérivés, qui communiquent en interne avec l'arborescence de composition par le biais du protocole de messagerie.  Chaque <xref:System.Windows.Media.Visual> dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] peut créer un ou plusieurs nœuds de composition, ou aucun.  
  
 ![Arborescence d'éléments visuels de Windows Presentation Foundation.](../../../../docs/framework/wpf/advanced/media/wpf-architecture2.png "wpf\_architecture2")  
  
 Il convient de noter un détail architectural très important ici – toute l'arborescence des objets visuels et des instructions de dessin est mise en cache.  En termes graphiques, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise un système de rendu conservé.  Cela permet au système de se régénérer à des fréquences d'actualisation plus élevées sans que le système de composition se bloque lors de rappels au code utilisateur.  Cela aide à prévenir l'apparition d'une application qui ne répond pas.  
  
 Un autre détail important qui n'est pas vraiment évident dans le diagramme est la façon dont le système exécute réellement la composition.  
  
 Dans User32 et [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], le système fonctionne sur un système de découpage en mode immédiat.  Quand un composant doit être rendu, le système établit des limites de découpage en dehors desquelles le composant n'a pas le droit de toucher aux pixels, puis il est demandé au composant de peindre les pixels dans cette zone.  Cette approche fonctionne très bien sur les systèmes soumis à des contraintes de mémoire car lorsque quelque chose change, vous devez intervenir uniquement au niveau du composant concerné – deux composants ne contribuent jamais ensemble à la couleur d'un pixel unique.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utilise le modèle de peinture « algorithme du peintre ».  Cela signifie qu'au lieu de découper chaque composant, il est demandé à chaque composant d'effectuer un rendu de l'arrière vers l'avant de l'affichage.  Chaque composant peut ainsi peindre par\-dessus l'affichage du précédent composant.  L'avantage de ce modèle est que vous pouvez avoir des formes complexes partiellement transparentes.  Grâce au matériel graphique moderne d'aujourd'hui, ce modèle est relativement rapide \(ce qui n'était pas le cas lors de la création de User32\/ [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]\).  
  
 Comme indiqué plus haut, une philosophie de base de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est de passer à un modèle de programmation plus déclaratif, plus « axé sur les propriétés ».  Dans le système visuel, ceci apparaît à deux emplacements intéressants.  
  
 Tout d'abord, si vous réfléchissez au système graphique retenu, cela revient en fait à s'éloigner d'un modèle de type DrawLine\/DrawLine, pour aller vers un modèle orienté données – new Line\(\)\/new Line\(\).  Ce transfert vers un rendu piloté par les données permet d'exprimer des opérations plus complexes sur les instructions de dessin en utilisant des propriétés.  Les types dérivés de <xref:System.Windows.Media.Drawing> sont effectivement le modèle de l'objet pour le rendu.  
  
 Ensuite, si vous évaluez le système d'animation, vous verrez qu'il est presque entière déclaratif.  Au lieu d'obliger un développeur à calculer l'emplacement suivant, ou la couleur suivante, vous pouvez exprimer des animations en tant que jeu de propriétés sur un objet d'animation.  Ces animations peuvent alors exprimer l'intention du développeur ou du concepteur \(déplacer ce bouton d'ici à là en 5 secondes\), et le système peut déterminer la façon la plus efficace d'accomplir cela.  
  
<a name="System_Windows_UIElement"></a>   
## System.Windows.UIElement  
 <xref:System.Windows.UIElement> définit les sous\-systèmes de base, y compris Layout, Input et Events.  
  
 Layout est un concept fondamental dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Dans de nombreux systèmes, il existe soit un jeu fixe de modèles de disposition \(le HTML prend en charge trois modèles de disposition : fluide, absolu, et par tables\) ou aucun modèle de disposition \(User32 prend uniquement en charge le positionnement absolu\).  Aux débuts de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l'hypothèse était que les développeurs et concepteurs souhaitaient un modèle de disposition flexible et extensible qui pourrait reposer sur des valeurs de propriété plutôt que sur la logique impérative.  Au niveau de <xref:System.Windows.UIElement>, le contrat de base de disposition est introduit – un modèle à double phase avec des passes <xref:System.Windows.UIElement.Measure%2A> et <xref:System.Windows.UIElement.Arrange%2A>.  
  
 <xref:System.Windows.UIElement.Measure%2A> permet à un composant de déterminer la taille qu'il souhaite prendre.  Il s'agit d'une phase distincte de <xref:System.Windows.UIElement.Arrange%2A> car il existe de nombreuses situations où un élément parent demandera à un enfant de mesurer plusieurs fois afin de déterminer sa position et sa taille optimales.  Le fait que les éléments parents demandent aux éléments enfants de mesurer illustre une autre philosophie clé de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – la taille par rapport au contenu.  Tous les contrôles [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prennent en charge la possibilité de se dimensionner selon la taille naturelle de leur contenu.  Cela facilite la localisation, et permet une disposition dynamique des éléments lors du redimensionnement.  La phase <xref:System.Windows.UIElement.Arrange%2A> permet à un parent de se positionner et de déterminer la taille finale de chaque enfant.  
  
 Une bonne partie du temps est consacrée à la discussion à propos du côté sortie de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> et des objets connexes.  Cependant, il existe également une extraordinaire quantité d'innovations côté entrée.  Le changement le plus fondamental dans le modèle d'entrée pour [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est probablement le modèle homogène par l'intermédiaire duquel les événements d'entrée sont routés dans le système.  
  
 L'entrée est générée en tant que signal sur un pilote de périphérique en mode noyau et est routée vers le processus et le thread appropriés via un processus complexe impliquant le noyau Windows et User32.  Une fois le message User32 qui correspond à l'entrée routé vers [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], il est converti en message d'entrée brut [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] et envoyé au répartiteur.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet de convertir les événements d'entrée bruts en différents événements réels. Ce faisant, certaines fonctionnalités telles que « MouseEnter » peuvent être implémentées à un niveau inférieur du système afin de garantir leur transmission.  
  
 Chaque événement d'entrée est converti au moins en deux événements – un événement « aperçu » et l'événement actuel.  Tous les événements dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ont une notion de routage via l'arborescence des éléments.  Les événements « se propagent » quand ils passent d'une cible en haut de l'arborescence à la racine, et « passent dans un tunnel » quand ils commencent à la racine et passent à une cible.  Le tunnel des événements d'aperçu d'entrée, qui donne à tout élément dans l'arborescence la possibilité de filtrer ou de prendre une action sur l'événement.  Les événements ordinaires \(sans aperçu\) se propagent de la cible en remontant vers la racine.  
  
 Cette différence entre les phases de tunnel et de propagation fait que l'implémentation de fonctions comme les accélérateurs de clavier fonctionne de façon homogène dans un monde composite.  Dans User32, vous pouvez implémenter les accélérateurs de clavier en ayant une seule table globale contenant tous les accélérateurs  que vous voulez prendre en charge \(Ctrl\+N correspondant à « Nouveau »\).  Dans le répartiteur de votre application, vous pouvez appeler **TranslateAccelerator** qui « renifle » les messages d'entrée dans User32 et détermine si l'un d'eux correspond à un accélérateur enregistré.  Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ceci ne fonctionnerait pas car le système est entièrement « composable » – tout élément peut gérer et utiliser un accélérateur de clavier.  Le fait d'avoir ce modèle à deux phases pour l'entrée permet aux composants d'implémenter leur propre  « TranslateAccelerator ».  
  
 Pour aller une étape plus loin, <xref:System.Windows.UIElement> introduit également la notion de CommandBindings.  Le système de commandes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux développeurs de définir les fonctionnalités en termes de point de terminaison de commande – quelque chose qui implémente <xref:System.Windows.Input.ICommand>.  Les liaisons de commande permettent à un élément de définir un mappage entre un mouvement d'entrée \(Ctrl\+N\) et une commande \(Nouveau\).  Les mouvements d'entrée et les définitions de commande sont extensibles, et peuvent être liés ensemble au moment de l'utilisation.  Cela rend banal le fait, par exemple, pour un utilisateur final de personnaliser les liaisons de clés qu'il veut utiliser dans une application.  
  
 À ce stade de la rubrique, les fonctions « fondamentales » de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], les fonctions implémentées dans l'assembly PresentationCore, ont monopolisé toute l'attente.  Lors de la génération de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], une séparation nette entre les éléments fondamentaux \(comme le contrat de disposition avec **Mesurer** et **Disposer**\) et les éléments d'infrastructure \(comme l'implémentation d'une disposition spécifique de type <xref:System.Windows.Controls.Grid>\) était le résultat voulu.  L'objectif était de fournir un point d'extensibilité bas dans la pile qui permettrait aux développeurs externes de créer leurs propres infrastructures, en cas de besoin.  
  
<a name="System_Windows_FrameworkElement"></a>   
## System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> peut être considéré de deux façons différentes.  Il introduit un ensemble de stratégies et de personnalisations sur les sous\-systèmes présents dans les couches inférieures de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Il introduit également un ensemble de nouveaux sous\-systèmes.  
  
 La stratégie principale présentée dans <xref:System.Windows.FrameworkElement> porte sur la disposition d'application.  <xref:System.Windows.FrameworkElement> tire parti du contrat de disposition de base présenté par <xref:System.Windows.UIElement> et lui ajoute la notion d'« emplacement » de disposition qui aide les auteurs de disposition à bénéficier d'un jeu cohérent de sémantiques de disposition orientées propriété.  Des propriétés comme <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A> et <xref:System.Windows.FrameworkElement.Margin%2A> \(pour n'en citer que quelques\-unes\) fournissent à tous les composants dérivés de <xref:System.Windows.FrameworkElement> un comportement homogène dans les conteneurs de disposition.  
  
 <xref:System.Windows.FrameworkElement> fournit également une exposition [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] plus facile pour de nombreuses fonctions qui se situent dans les couches centrales de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  Par exemple, <xref:System.Windows.FrameworkElement> permet un accès direct à l'animation via la méthode <xref:System.Windows.FrameworkElement.BeginStoryboard%2A>.  Un <xref:System.Windows.Media.Animation.Storyboard> permet d'écrire le script de plusieurs animations par rapport à un ensemble de propriétés.  
  
 Les deux choses les plus critiques introduite par <xref:System.Windows.FrameworkElement> sont les liaisons de données et les styles.  
  
 Le sous\-système de liaison de données dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] devrait être relativement familier à quiconque a utilisé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] pour la création d'une application [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  Dans chacun de ces systèmes, il existe une méthode simple pour exprimer que vous souhaitez lier une ou plusieurs propriétés d'un élément spécifique à une donnée.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assure la prise en charge complète de la liaison de propriété, de la transformation et de la liaison de liste.  
  
 L'une des fonctions les plus intéressantes de la liaison des données dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est l'introduction des modèles de données.  Les modèles de données vous permettent de spécifier de manière déclarative comment les données peuvent être visualisées.  Au lieu de créer une interface utilisateur personnalisée pouvant être liée à des données, vous pouvez plutôt contourner le problème et laisser les données déterminer l'affichage qui sera créé.  
  
 Les styles constituent une forme légère de liaison de données.  En utilisant les styles, vous pouvez lier un ensemble de propriétés à partir d'une définition partagée avec une ou plusieurs instances d'un élément.  Les styles sont appliqués à un élément soit par référence explicite \(en définissant la propriété <xref:System.Windows.FrameworkElement.Style%2A>\) soit implicitement en associant un style avec le type [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] de l'élément.  
  
<a name="System_Windows_Controls_Control"></a>   
## System.Windows.Controls.Control  
 La fonction la plus importante du contrôle est la création de modèles.  Si vous considérez le système de composition WPF comme un système de rendu en mode Conservation, la création de modèles permet à un contrôle de décrire son rendu d'une manière déclarative et paramétrable.  Un <xref:System.Windows.Controls.ControlTemplate> n'est vraiment rien d'autre qu'un ensemble d'éléments enfants, avec des liaisons aux propriétés offertes par le contrôle.  
  
 <xref:System.Windows.Controls.Control> fournit un ensemble de propriétés stock, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, pour n'en citer que quelques\-unes, que les créateurs de modèles peuvent utiliser pour personnaliser l'affichage d'un contrôle.  L'implementation d'un contrôle fournit un modèle de données et un modèle d'interaction.  Le modèle d'interaction définit un jeu de commandes \(Fermer une fenêtre, par exemple\) et des liaisons aux mouvements d'entrée \(comme le fait de cliquer sur le X rouge dans l'angle droit supérieur d'une fenêtre\).  Le modèle de données fournit un ensemble de propriétés soit pour personnaliser le modèle d'interaction soit pour personnaliser l'affichage \(déterminé par le modèle\).  
  
 Cet écart entre le modèle de données \(propriétés\), le modèle d'interaction \(commandes et événements\) et le modèle d'affichage \(modèles\) permet une personnalisation complète de l'apparence et du comportement d'un contrôle.  
  
 Un aspect commun des contrôles de modèle de données est le modèle de contenu.  Si vous considérez un contrôle comme un <xref:System.Windows.Controls.Button>, vous verrez qu'il a une propriété nommée « Content » de type <xref:System.Object>.  Dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], cette propriété est généralement une chaîne – cependant, cela limite le type de contenu que vous pouvez mettre dans un bouton.  Le contenu d'un bouton peut être une simple chaîne, un objet données complexe ou une arborescence complète d'éléments.  Dans le cas d'un objet de données, le modèle de données permet de construire un affichage.  
  
<a name="Summary"></a>   
## Résumé  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est conçu de manière à vous permettre de créer des systèmes de présentation dynamiques, pilotés par données.  Chaque partie du système est destinée à créer des objets via des ensembles de propriétés qui pilotent le comportement.  La liaison de données est une partie fondamentale du système, et est intégrée au niveau de chaque couche.  
  
 Les applications classiques créent un affichage, puis effectuent une liaison avec certaines données.  Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tout ce qui concerne le contrôle, chaque aspect de l'affichage, est généré par un certain type de liaison de données.  Le texte placé dans un bouton est affiché en créant un contrôle composé à l'intérieur du bouton et en liant son affichage à la propriété de contenu du bouton.  
  
 Lorsque vous commencez à développer des applications basées sur [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], l'opération devrait sembler très familière.  Vous pouvez définir des propriétés, utiliser des objets et lier de données, un peu de la même façon que vous pouvez utiliser [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)].  Avec un examen plus approfondi de l'architecture de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vous trouverez qu'il existe la possibilité de créer des applications plus riches qui traitent fondamentalement les données en tant qu'élément moteur de l'application.  
  
## Voir aussi  
 <xref:System.Windows.Media.Visual>   
 <xref:System.Windows.UIElement>   
 <xref:System.Windows.Input.ICommand>   
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.Threading.DispatcherObject>   
 <xref:System.Windows.Input.CommandBinding>   
 <xref:System.Windows.Controls.Control>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)