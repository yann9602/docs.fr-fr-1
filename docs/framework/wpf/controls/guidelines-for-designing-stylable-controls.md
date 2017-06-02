---
title: "Recommandations pour la conception de contr&#244;les auxquels un style peut &#234;tre appliqu&#233; | Microsoft Docs"
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
  - "contrôles, conception de style"
  - "conception de style pour des contrôles"
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Recommandations pour la conception de contr&#244;les auxquels un style peut &#234;tre appliqu&#233;
Ce document récapitule un ensemble de meilleures pratiques à prendre en compte lors de la conception d'un contrôle auquel il soit facile d'appliquer un style et un modèle.  Ces meilleures pratiques font suite aux nombreux tâtonnements que nous avons expérimentés lors de nos travaux sur les styles de contrôles de thème pour le jeu de contrôles intégré de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Nous avons découvert que la réussite de l'application d'un style dépend autant de la qualité de conception d'un modèle d'objet que du style lui\-même.  Ce document s'adresse aux auteurs de contrôles et non aux auteurs de styles.  
  
   
  
<a name="Terminology"></a>   
## Terminologie  
 On appelle « styles et modèles » la suite de technologies qui permettent à l'auteur d'un contrôle de conditionner les aspects visuels du contrôle au style et au modèle de ce contrôle.  Cette suite de technologies inclut les éléments suivants :  
  
-   Styles \(accesseurs Set de propriétés, déclencheurs et tables de montage séquentiel\).  
  
-   Ressources.  
  
-   Modèles de contrôle.  
  
-   Modèles de données.  
  
 Pour une introduction aux styles et aux modèles, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## Avant de commencer : bien comprendre le contrôle que vous créez  
 Avant de passer à ces recommandations, il importe de bien comprendre l'utilisation courante de votre contrôle et de l'avoir définie.  L'application d'un style ouvre un ensemble de possibilités souvent non maîtrisées.  Les contrôles écrits pour être utilisés à grande échelle \(dans de nombreuses applications, par beaucoup de développeurs\) courent le risque d'être soumis à des styles qui en modifient profondément l'aspect.  En fait, il peut même arriver que le contrôle auquel un style a été appliqué ne ressemble plus à ce que souhaitait son auteur.  Les possibilités offertes par l'application de styles étant infinies, vous pouvez vous appuyer sur la notion d'utilisation courante pour vous aider à cerner vos décisions.  
  
 Pour bien appréhender l'utilisation courante de votre contrôle, il peut être utile de réfléchir à son intérêt.  Qu'est\-ce que votre contrôle apporte de plus que les autres ?  L'utilisation courante d'un contrôle fait référence à son principe et aux usages possibles auquel on peut s'attendre, et n'a aucun rapport avec son apparence visuelle.  Cette réflexion vous permet de faire des hypothèses sur le modèle de composition et sur les comportements du contrôle définis par le style dans les cas les plus fréquents.  Par exemple, dans le cas d'un <xref:System.Windows.Controls.ComboBox>, comprendre l'utilisation courante ne vous aidera pas à savoir si tel ou tel <xref:System.Windows.Controls.ComboBox> a des angles arrondis. En revanche, vous saurez qu'il faudra prévoir une fenêtre indépendante et une forme quelconque de basculement à l'ouverture pour ce <xref:System.Windows.Controls.ComboBox>.  
  
<a name="General_Guidelines"></a>   
## Indications générales  
  
-   **N'appliquez pas à la lettre les contrats de modèles.** Le contrat de modèle d'un contrôle peut se composer d'éléments, de commandes, de liaisons, de déclencheurs, voire de paramètres de propriétés qui sont requis ou attendus pour que le contrôle fonctionne correctement.  
  
    -   Minimisez les contrats le plus possible.  
  
    -   Ne perdez pas de vue que pendant la conception \(à savoir, pendant l'utilisation d'un outil de conception\), il est fréquent qu'un modèle de contrôle ne soit pas complet.  Comme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n'offre pas d'infrastructure d'état « en cours de composition », il convient de créer les contrôles en espérant que cet état soit valide.  
  
    -   Ne levez pas d'exceptions lorsqu'un aspect du contrat de modèle n'est pas suivi.  Par exemple, les panneaux ne doivent pas lever d'exceptions s'ils possèdent trop ou trop peu d'enfants.  
  
-   **Placez les fonctionnalités périphériques dans les éléments d'assistance du modèle.** Chaque contrôle doit être centré sur ses fonctionnalités principales ainsi que sur l'intérêt qu'il offre réellement, et doit être défini par son utilisation courante.  À cet effet, recourez aux éléments de composition et d'assistance du modèle pour activer les comportements et visualisations périphériques, c'est\-à\-dire qui ne contribuent pas à la fonctionnalité principale du contrôle.  Les éléments d'assistance appartiennent à trois catégories :  
  
    -   Les types d'éléments d'assistance **autonomes** sont des contrôles ou des primitives publics et réutilisables employés de manière "anonyme" dans un modèle, c'est\-à\-dire que ni l'élément d'assistance ni le contrôle auquel est appliqué le style ne sont conscients l'un de l'autre.  Techniquement, tout élément peut être de type anonyme mais, dans ce contexte, ce terme désigne les types qui encapsulent des fonctionnalités spéciales dans le but d'activer des scénarios ciblés.  
  
    -   Les éléments d'assistance **fondés sur un type** sont des nouveaux types qui encapsulent des fonctionnalités spéciales.  Ils sont généralement conçus avec une gamme de fonctionnalités plus étroite que les contrôles ou les primitives communs.  Contrairement aux éléments d'assistance autonomes, les éléments d'assistance fondés sur un type ont connaissance du contexte où ils sont utilisés et doivent généralement partager des données avec le contrôle associé au modèle dont ils font partie.  
  
    -   Les éléments d'assistance **nommés** sont des contrôles communs ou des primitives qu'un contrôle s'attend à trouver dans son modèle par nom. Ces éléments portent un nom connu dans le modèle, ce qui permet à un contrôle de trouver l'élément et d'interagir avec lui par programmation.  Il ne peut exister qu'un seul élément du même nom dans un modèle donné.  
  
     Le tableau suivant répertorie les éléments d'assistance actuellement utilisés par les styles de contrôle \(cette liste n'est pas exhaustive\) :  
  
    |Élément|Type|Utilisé par|  
    |-------------|----------|-----------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Fondé sur un type|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame> etc., \(tous les types de <xref:System.Windows.Controls.ContentControl>\)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Fondé sur un type|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, etc. \(tous les types de <xref:System.Windows.Controls.ItemsControl>\)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nommé|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Autonome|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>, etc.|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|Nommé|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>, etc.|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|Nommé|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Autonome|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>, etc.|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Autonome|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|Nommé|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Fondé sur un type|<xref:System.Windows.Controls.Slider>|  
  
-   **Minimisez le nombre requis de liaisons spécifiées par l'utilisateur ou de paramètres de propriétés dans les éléments d'assistance**.  Il arrive fréquemment qu'un élément d'assistance requière certaines liaisons ou certains paramètres de propriété pour fonctionner correctement dans le modèle de contrôle.  L'élément d'assistance et le contrôle basé sur un modèle doivent établir ces paramètres dans la mesure du possible.  Lors du paramétrage des propriétés ou de l'établissement des liaisons, il faut veiller à ne pas écraser les valeurs définies par l'utilisateur.  En particulier, il est conseillé d'appliquer les meilleures pratiques suivantes :  
  
    -   Les éléments d'assistance nommés doivent être identifiés par le parent et le parent doit établir tout paramètre requis sur l'élément d'assistance.  
  
    -   Les éléments d'assistance fondés sur un type doivent établir les paramètres requis directement sur eux\-mêmes.  Cela peut amener l'élément d'assistance à demander des informations sur son contexte d'utilisation, notamment son `TemplatedParent` \(le type de contrôle du modèle où il est employé\).  Par exemple, <xref:System.Windows.Controls.ContentPresenter> lie automatiquement la propriété `Content` de son `TemplatedParent` à sa propriété <xref:System.Windows.Controls.ContentPresenter.Content%2A> lorsqu'il est utilisé dans un type dérivé de <xref:System.Windows.Controls.ContentControl>.  
  
    -   Il est impossible d'optimiser les éléments d'assistance autonomes de cette façon puisque, par définition, l'élément d'assistance et le parent ne se connaissent pas.  
  
-   **Utilisez la propriété Name pour marquer des éléments dans un modèle**.  Lorsqu'un contrôle a besoin de trouver un élément dans son style pour y accéder par programme, il doit utiliser pour ce faire la propriété `Name` et le paradigme `FindName`.  Un contrôle ne doit pas lever d'exception lorsqu'il ne trouve pas un élément, mais désactiver silencieusement et correctement la fonctionnalité qui requérait cet élément.  
  
-   **Recourez aux meilleures pratiques pour exprimer l'état et le comportement d'un contrôle dans un style.** Voici une liste classée des meilleures pratiques pour exprimer les changements d'état et le comportement d'un contrôle dans un style.  Vous devez utiliser le premier élément de la liste qui correspond à votre scénario.  
  
    1.  Liaison de propriété.  Exemple : liaison entre <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=fullName> et <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=fullName>.  
  
    2.  Modifications ou animations de propriétés déclenchées.  Exemple : l'état pointé d'un <xref:System.Windows.Controls.Button>.  
  
    3.  Commande.  Exemple : <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> \/ <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> dans <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4.  Éléments d'assistance autonomes.  Exemple : <xref:System.Windows.Controls.Primitives.TabPanel> dans <xref:System.Windows.Controls.TabControl>.  
  
    5.  Types d'éléments d'assistance fondés sur un type.  Exemple : <xref:System.Windows.Controls.ContentPresenter> dans <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> dans <xref:System.Windows.Controls.Slider>.  
  
    6.  Éléments d'assistance nommés.  Exemple : <xref:System.Windows.Controls.TextBox> dans <xref:System.Windows.Controls.ComboBox>.  
  
    7.  Événements propagés à partir de types d'éléments d'assistance nommés.  Si vous écoutez des événements propagés à partir d'un élément de style, vous devez demander que l'élément qui génère cet événement soit identifié de manière univoque.  Exemple : <xref:System.Windows.Controls.Primitives.Thumb> dans <xref:System.Windows.Controls.ToolBar>.  
  
    8.  Comportement `OnRender` personnalisé.  Exemple : <xref:Microsoft.Windows.Themes.ButtonChrome> dans <xref:System.Windows.Controls.Button>.  
  
-   **Utilisez les déclencheurs de style \(par opposition aux déclencheurs de modèle\) avec parcimonie**.  Les déclencheurs qui influent sur les propriétés des éléments du modèle doivent être déclarés dans le modèle.  Ceux qui influent sur les propriétés du contrôle \(sans `TargetName`\) doivent être déclarés dans le système excepté si vous savez que modifier le modèle détruirait également le déclencheur.  
  
-   **Soyez cohérents avec les modèles d'application de styles existants.** Il existe très souvent plusieurs façons de résoudre un problème.  Prenez connaissance des modèles existants pour l'application de styles aux contrôles et suivez\-les dans la mesure du possible.  C'est particulièrement important pour les contrôles dérivés du même type de base \(par exemple <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>, etc.\).  
  
-   **Exposez les propriétés de manière à permettre des scénarios de personnalisation courants sans avoir à recréer un modèle.** Comme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prend pas en charge les composants enfichables\/personnalisables, l'utilisateur d'un contrôle ne dispose que de deux méthodes de personnalisation : définir les propriétés soit directement, soit à l'aide de styles.  Dans ces conditions, il convient d'apprêter un nombre limité de propriétés destinées à des scénarios de personnalisation prioritaires très courants qui nécessiteraient sinon de créer un nouveau modèle.  Voici une liste de meilleures pratiques concernant le moment et la façon d'activer les scénarios de personnalisation :  
  
    -   Les personnalisations très courantes doivent être exposées en tant que propriétés sur le contrôle et consommées par le modèle.  
  
    -   Les personnalisations moins courantes \(mais pas rares\) doivent être exposées en tant que propriétés attachées et consommées par le modèle.  
  
    -   Pour les personnalisations connues mais rares, il est acceptable d'exiger la création d'un nouveau modèle.  
  
<a name="Theme_Considerations"></a>   
## Considérations relatives aux thèmes  
  
-   **Les styles de thème doivent tendre à l'homogénéité de la sémantique des propriétés entre tous les thèmes, mais sans garantie**.  Dans le cadre de sa documentation, votre contrôle doit posséder un document décrivant la sémantique de ses propriétés, c'est\-à\-dire leur « signification ».  Par exemple, le contrôle <xref:System.Windows.Controls.ComboBox> pourrait définir la signification de la propriété <xref:System.Windows.Controls.Control.Background%2A> dans le <xref:System.Windows.Controls.ComboBox>.  Les styles par défaut de votre contrôle doivent tenter de suivre la sémantique définie dans ce document pour tous les thèmes.  Les utilisateurs du contrôle, pour leur part, doivent savoir que la sémantique des propriétés peut varier d'un thème à l'autre.  Dans certains cas, une propriété donnée peut ne pas être exprimable en raison des contraintes visuelles imposées par un thème particulier.  \(Le thème classique, par exemple, n'a pas de bordure simple à laquelle appliquer la propriété `Thickness` dans le cas de nombreux contrôles.\)  
  
-   **Les styles de thème n'exigent pas que la sémantique des déclencheurs soit homogène sur l'ensemble des thèmes**.  Le comportement exposé par un style de contrôle au travers des déclencheurs ou des animations peut varier d'un thème à l'autre.  Les utilisateurs d'un contrôle doivent savoir qu'un contrôle ne va pas nécessairement employer le même mécanisme pour réaliser un comportement particulier sur l'ensemble des thèmes.  Par exemple, un thème peut utiliser une animation pour exprimer un comportement de pointage, tandis qu'un autre thème utilisera un déclencheur à cet effet.  Cela peut entraîner des disparités dans la préservation des comportements au niveau des contrôles personnalisés.  \(Par exemple, changer la propriété d'arrière\-plan n'aura pas d'effet sur l'état pointé du contrôle si celui\-ci est exprimé à l'aide d'un déclencheur.  Toutefois, si l'état pointé est implémenté à l'aide d'une animation, la modification de l'arrière\-plan pourrait altérer irrémédiablement l'animation et donc, le changement d'état.\)  
  
-   **Les styles de thème n'exigent pas que la sémantique de « disposition » soit homogène sur l'ensemble des thèmes**.  Par exemple, il n'est pas nécessaire que le style par défaut garantisse qu'un contrôle occupe le même volume d'espace ou qu'il possède les mêmes propriétés de marge \/ remplissage dans tous les thèmes.  
  
## Voir aussi  
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)