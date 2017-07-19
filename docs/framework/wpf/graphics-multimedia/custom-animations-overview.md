---
title: "Vue d&#39;ensemble des animations personnalis&#233;es | Microsoft Docs"
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
  - "animation, classes personnalisées"
  - "classes d'animation personnalisées"
  - "classes personnalisées, animation"
  - "images clés personnalisées"
  - "images clés, personnalisé"
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble des animations personnalis&#233;es
Cette rubrique décrit comment et quand étendre le système d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en créant des images clés personnalisées, des classes d'animation ou en utilisant un rappel image par image pour l'ignorer.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les différents types d'animations fournis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour plus d'informations, consultez [Vue d'ensemble des animations From\/To\/By](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md), [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) et [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Étant donné que les classes d'animation héritent de la classe <xref:System.Windows.Freezable>, vous devez être familiarisé avec les objets <xref:System.Windows.Freezable> et savoir comment hériter du <xref:System.Windows.Freezable>.  Pour plus d'informations, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## Amélioration du système d'animation  
 Il existe plusieurs façons d'étendre le système d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en fonction du niveau de fonctionnalités intégrées que vous souhaitez utiliser.  Le moteur d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comporte trois points d'extensibilité principaux :  
  
-   Créer un objet d'image clé personnalisée à partir d'un héritage d'une des classes *\<Type\>*KeyFrame, telles que <xref:System.Windows.Media.Animation.DoubleKeyFrame>.  Cette approche utilise la plupart des fonctionnalités intégrées du moteur d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Créer votre propre classe d'animation à partir d'un héritage d'un <xref:System.Windows.Media.Animation.AnimationTimeline> ou d'une des classes *\<Type\>*AnimationBase.  
  
-   Utiliser un rappel image par image pour générer des animations par image.  Cette approche ignore entièrement le système de minutage et d'animation.  
  
 Le tableau suivant décrit certains des scénarios permettant d'étendre le système d'animation.  
  
|Si vous souhaitez…|Utilisez cette approche|  
|------------------------|-----------------------------|  
|Personnaliser l'interpolation entre les valeurs d'un type qui possède un *\<Type\>*AnimationUsingKeyFrames correspondant|Créer une image clé personnalisée.  Pour plus d'informations, consultez [Créer une image clé personnalisée](#createacustomkeyframe).|  
|Personnaliser plus que l'interpolation entre les valeurs d'un type qui possède un *\<Type\>*Animation correspondant.|Créer une classe d'animation personnalisée qui hérite de la classe *\<Type\>*AnimationBase correspondant au type à animer.  Pour plus d'informations, consultez [Créer une classe d'animation personnalisée](#createcustomanimationtype).|  
|Animer un type qui n'a pas d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondante|Utiliser un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> ou créer une classe qui hérite de <xref:System.Windows.Media.Animation.AnimationTimeline>.  Pour plus d'informations, consultez [Créer une classe d'animation personnalisée](#createcustomanimationtype).|  
|Animer plusieurs objets avec des valeurs calculées à chaque trame et basées sur le dernier jeu d'interactions d'objets|Utiliser le rappel image par image.  Pour plus d'informations, consultez [Utiliser un rappel image par image](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>   
## Créer une image clé personnalisée  
 La façon la plus simple d'étendre le système d'animation consiste à créer une classe d'image clé personnalisée.  Utilisez cette approche si vous souhaitez appliquer une autre méthode d'interpolation à une animation par trame.  Comme décrit dans [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), une animation d'image clé utilise des objets d'images clés pour générer ses valeurs de sortie.  Chaque objet d'image clé exécute les fonctions suivantes :  
  
-   Spécifie une valeur cible à l'aide de sa propriété <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
-   Spécifie l'heure à laquelle la valeur doit être atteinte à l'aide de sa propriété <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>.  
  
-   Interpole entre la valeur de l'image clé précédente et sa propre valeur en implémentant la méthode InterpolateValueCore.  
  
 **Instructions d'implémentation**  
  
 Dérivez de la classe abstraite *\<Type\>*KeyFrame et implémentez la méthode InterpolateValueCore.  La méthode InterpolateValueCore retourne la valeur actuelle de l'image clé.  Il prend deux paramètres : la valeur de l'image clé précédente et une valeur de progression qui varie de 0 à 1.  Une progression de 0 indique que l'image clé vient de démarrer, et une valeur de 1 indique que l'image clé vient de se terminer et doit retourner la valeur spécifiée par sa propriété <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>.  
  
 Étant donné que les classes *\<Type\>*KeyFrame héritent de la classe <xref:System.Windows.Freezable>, vous devez substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour retourner une nouvelle instance de votre classe.  Si la classe n'utilise pas de [propriétés de dépendance](GTMT) pour stocker ses données ou si elle nécessite une initialisation supplémentaire une fois créée, vous devrez peut\-être remplacer d'autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) pour plus d'informations.  
  
 Après avoir créé votre propre animation *\<Type\>*KeyFrame, vous pouvez l'utiliser avec le *\<Type\>*AnimationUsingKeyFrames pour ce type.  
  
<a name="createacustomanimationtype"></a>   
## Créer une classe d'animation personnalisée  
 En créant votre propre type d'animation, vous disposez de davantage de contrôle sur l'animation d'un objet.  Il est recommandé d'utiliser les deux méthodes suivantes pour créer votre propre type d'animation : vous pouvez dériver de la classe <xref:System.Windows.Media.Animation.AnimationTimeline> ou de la classe *\<Type\>*AnimationBase.  La dérivation des classes *\<Type\>*Animation et *\<Type\>*AnimationUsingKeyFrames est déconseillée.  
  
### Dériver de \<Type\>AnimationBase  
 La dérivation de la classe *\<Type\>*AnimationBase est le moyen le plus simple pour créer un nouveau type d'animation.  Utilisez cette approche si vous souhaitez créer une animation pour un type qui a déjà une classe *\<Type\>*AnimationBase correspondante.  
  
 **Instructions d'implémentation**  
  
 Dérivez d'une classe *\<Type\>*Animation et implémentez la méthode GetCurrentValueCore.  La méthodeGetCurrentValueCore retourne la valeur actuelle de l'animation.  Elle utilise trois paramètres : une valeur de début suggérée, une valeur de fin suggérée et un <xref:System.Windows.Media.Animation.AnimationClock>, que vous utilisez pour déterminer la progression de l'animation.  
  
 Étant donné que les classes *\<Type\>*AnimationBase héritent de la classe <xref:System.Windows.Freezable>, vous devez substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour retourner une nouvelle instance de votre classe.  Si la classe n'utilise pas de [propriétés de dépendance](GTMT) pour stocker ses données ou si elle nécessite une initialisation supplémentaire une fois créée, vous devrez peut\-être remplacer d'autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) pour plus d'informations.  
  
 Pour plus d'informations, consultez la documentation sur la méthode GetCurrentValueCore pour la classe *\<Type\>*AnimationBase du type à animer.  Pour obtenir un exemple, consultez [Animation personnalisée, exemple](http://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Autres approches**  
  
 Si vous souhaitez simplement modifier la façon dont les valeurs d'animation sont interpolées, envisagez de dériver une des classes *\<Type\>*KeyFrame.  L'image clé créée peut être utilisée avec le *\<Type\>*AnimationUsingKeyFrames correspondant fourni par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Dériver de AnimationTimeline  
 Dérivez de la classe <xref:System.Windows.Media.Animation.AnimationTimeline> si vous souhaitez créer une animation pour un type qui ne dispose pas encore d'une animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondante, ou si vous souhaitez créer une animation qui n'est pas fortement typée.  
  
 **Instructions d'implémentation**  
  
 Dérivez de la classe <xref:System.Windows.Media.Animation.AnimationTimeline> et substituez les membres suivants :  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A> : si votre nouvelle classe est concrète, vous devez remplacer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour obtenir une nouvelle instance de votre classe.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> : remplacez cette méthode pour obtenir la valeur actuelle de votre animation.  Trois paramètres sont nécessaires : valeur d'origine par défaut, valeur de destination par défaut et <xref:System.Windows.Media.Animation.AnimationClock>.  Utilisez l'horloge <xref:System.Windows.Media.Animation.AnimationClock> pour obtenir le décompte actuel ou l'état d'avancement de l'animation.  Vous pouvez choisir d'utiliser les valeurs d'origine et les valeurs de destination par défaut.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> : remplacez cette propriété pour indiquer si votre animation doit utiliser les valeurs de destination par défaut spécifiées par la méthode <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> : remplacez cette propriété pour indiquer le type <xref:System.Type> de sortie que votre animation doit générer.  
  
 Si la classe n'utilise pas de [propriétés de dépendance](GTMT) pour stocker ses données ou si elle nécessite une initialisation supplémentaire une fois créée, vous devrez peut\-être remplacer d'autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) pour plus d'informations.  
  
 Le paradigme recommandé \(utilisé par les animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]\) consiste à utiliser deux niveaux d'héritage :  
  
1.  Créez une classe abstraite *\<Type\>*AnimationBase qui dérive de <xref:System.Windows.Media.Animation.AnimationTimeline>.  Cette classe se substitue à la méthode <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>.  Elle doit aussi introduire une nouvelle méthode abstraite, GetCurrentValueCore, et se substituer à <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> afin de valider les types des paramètres des valeurs d'origine par défaut et des valeurs de destination par défaut, et appeler GetCurrentValueCore.  
  
2.  Créez une autre classe qui hérite de votre nouvelle classe *\<Type\>*AnimationBase et se substitue à la méthode <xref:System.Windows.Freezable.CreateInstanceCore%2A>, la méthode GetCurrentValueCore introduite, et à la propriété <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>.  
  
 **Autres approches**  
  
 Si vous souhaitez animer un type qui n'a pas d'animation From\/To\/By ou d'animation d'image clé, envisagez d'utiliser un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>.  Étant donné qu'il est très peu typé, un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> peut animer n'importe quel type de valeur.  L'inconvénient de cette approche est que <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> prend uniquement en charge une [interpolation discrète](GTMT).  
  
<a name="useperframecallback"></a>   
## Utiliser un rappel image par image  
 Utilisez cette approche si vous devez ignorer entièrement le système d'animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Cette approche est utilisée pour les scénarios d'animations physiques dans lesquels à chaque étape de l'animation une nouvelle direction ou position des objets animés doit être recalculée en fonction du dernier jeu d'interactions d'objets.  
  
 **Instructions d'implémentation**  
  
 Contrairement aux autres approches décrites dans cette vue d'ensemble, pour utiliser un rappel image par image il n'est pas nécessaire de créer une animation personnalisée ou une classe d'image clé.  
  
 À la place, vous vous inscrivez à l'événement <xref:System.Windows.Media.CompositionTarget.Rendering> de l'objet qui contient les objets à animer.  Cette méthode du gestionnaire d'événements est appelée une fois par trame.  À chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l'[arborescence visuelle](GTMT) sur l'arborescence de composition, la méthode du gestionnaire d'événements est appelée.  
  
 Dans le gestionnaire d'événements, effectuez les calculs nécessaires à l'effet de votre animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir l'heure de la présentation de l'image actuelle, le <xref:System.EventArgs> associé à cet événement peut être casté en <xref:System.Windows.Media.RenderingEventArgs>, qui fournit une propriété <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> pouvant être utilisée pour obtenir l'heure de rendu de l'image actuelle.  
  
 Pour plus d'informations, consultez la page <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.AnimationTimeline>   
 <xref:System.Windows.Media.Animation.IKeyFrame>   
 [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [Vue d'ensemble des animations From\/To\/By](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)   
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [Animation personnalisée, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159981)