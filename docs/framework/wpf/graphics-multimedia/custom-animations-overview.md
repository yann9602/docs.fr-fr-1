---
title: "Vue d'ensemble des animations personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom classes [WPF], animation
- key frames [WPF], custom
- custom key frames [WPF]
- animation [WPF], custom classes
- custom animation classes [WPF]
ms.assetid: 9be69d50-3384-4938-886f-08ce00e4a7a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a206e0234f4e6365e76f73977beda1688c036a79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-animations-overview"></a>Vue d'ensemble des animations personnalisées
Cette rubrique décrit comment et quand étendre le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en créant des images clés personnalisées et des classes d’animation, ou à l’aide du rappel image par image pour l’ignorer.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez connaître les différents types d’animations offerts par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez la Vue d’ensemble des animations From/To/By, la [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) et la [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 Étant donné que les classes d’animation héritent la <xref:System.Windows.Freezable> (classe), vous devez être familiarisé avec <xref:System.Windows.Freezable> objets et comment hériter de <xref:System.Windows.Freezable>. Pour plus d’informations, consultez la [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="extendingtheanimationsystem"></a>   
## <a name="extending-the-animation-system"></a>Extension du système d’animation  
 Il existe plusieurs façons d’étendre le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], en fonction du niveau de fonctionnalités intégrées que vous souhaitez utiliser.  Il existe trois points d’extensibilité principaux dans le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
-   Créer un objet d’image clé personnalisée en héritant de la  *\<Type >*classes KeyFrame, telles que <xref:System.Windows.Media.Animation.DoubleKeyFrame>. Cette approche utilise la plupart des fonctionnalités intégrées dans le moteur d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Créer votre propre classe d’animation en héritant de <xref:System.Windows.Media.Animation.AnimationTimeline> ou l’un de le  *\<Type >*AnimationBase classes.  
  
-   Utilisez le rappel image par image pour générer des animations image par image. Cette approche ignore entièrement l’animation et le système de minutage.  
  
 Le tableau suivant décrit certains scénarios permettant d’étendre le système d’animation.  
  
|Si vous souhaitez...|Utiliser cette approche|  
|-------------------------|-----------------------|  
|Personnalisez l’interpolation entre les valeurs d’un type qui possède un *\<Type >*AnimationUsingKeyFrames correspondant|Créez une image clé personnalisée. Pour plus d’informations, consultez la section [Création d’une image clé personnalisée](#createacustomkeyframe).|  
|Personnalisez plus que l’interpolation entre les valeurs d’un type qui possède un *\<Type >*Animation correspondant.|Créez une classe d’animation personnalisée qui hérite de la classe *\<Type >*AnimationBase qui correspond au type que vous souhaitez animer. Pour plus d’informations, consultez la section [Création d’une classe d’animation personnalisée](#createacustomanimationtype).|  
|Animation d’un type qui ne possède aucune animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondante|Utilisez un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> ou créez une classe qui hérite de <xref:System.Windows.Media.Animation.AnimationTimeline>. Pour plus d’informations, consultez la section [Création d’une classe d’animation personnalisée](#createacustomanimationtype).|  
|Animer plusieurs objets avec des valeurs calculées à chaque frame et basées sur le dernier jeu d’interactions avec les objets|Utilisez un rappel image par image. Pour plus d’informations, consultez la section [Création d’un rappel image par image](#useperframecallback).|  
  
<a name="createacustomkeyframe"></a>   
## <a name="create-a-custom-key-frame"></a>Création d’une image clé personnalisée  
 La création d’une classe d’image clé personnalisée est la façon la plus simple d’étendre le système d’animation. Utilisez cette approche lorsque vous souhaitez une autre méthode d’interpolation pour une animation d’image clé.  Comme décrit dans la [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md), une animation d’image clé utilise des objets d’images clés pour générer ses valeurs de sortie. Chaque objet d’image clé remplit trois fonctions :  
  
-   Spécifie une valeur de cible à l’aide de son <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriété.  
  
-   Spécifie l’heure à laquelle cette valeur doit être atteint à l’aide de son <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriété.  
  
-   Interpole entre la valeur de l’image clé précédente et sa propre valeur en implémentant la méthode InterpolateValueCore.  
  
 **Instructions d’implémentation**  
  
 Dérivez à partir de la classe abstraite *\<Type >*KeyFrame et implémentez la méthode InterpolateValueCore. La méthode InterpolateValueCore retourne la valeur actuelle de l’image clé. Elle accepte deux paramètres : la valeur de l’image clé précédente et une valeur de progression comprise entre 0 et 1. Une progression de 0 indique l’image clé vient de démarrer, et une valeur de 1 indique que l’image clé vient de se terminer et doit retourner la valeur spécifiée par son <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriété.  
  
 Étant donné que le  *\<Type >*héritent des classes de l’image clé de la <xref:System.Windows.Freezable> (classe), vous devez également substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour retourner une nouvelle instance de la classe. Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Une fois que vous avez créé votre propre animation *\<Type >*KeyFrame, vous pouvez l’utiliser avec *\<Type >*AnimationUsingKeyFrames pour ce type.  
  
<a name="createacustomanimationtype"></a>   
## <a name="create-a-custom-animation-class"></a>Création d’une classe d’animation personnalisée  
 La création de votre propre type d’animation vous donne plus de contrôle sur la façon dont objet est animé. Il existe deux méthodes recommandées pour créer votre propre type d’animation : vous pouvez dériver de la <xref:System.Windows.Media.Animation.AnimationTimeline> classe ou la  *\<Type >*AnimationBase classe. La dérivation à partir des classes *\<Type >*Animation ou *\<Type >*AnimationUsingKeyFrames n’est pas recommandée.  
  
### <a name="derive-from-typeanimationbase"></a>Dérivation à partir de \<Type > AnimationBase  
 La dérivation d’une classe *\<Type >*AnimationBase est la méthode la plus simple pour créer un nouveau type d’animation. Utilisez cette approche lorsque vous souhaitez créer une nouvelle animation pour un type qui a déjà une classe *\<Type >*AnimationBase correspondante.  
  
 **Instructions d’implémentation**  
  
 Dérivez à partir d’une classe *\<Type >*Animation et implémentez la méthode GetCurrentValueCore. La méthode GetCurrentValueCore retourne la valeur actuelle de l’animation. Elle accepte trois paramètres : une valeur de départ suggérée, une valeur de fin suggérée et un <xref:System.Windows.Media.Animation.AnimationClock>, qui vous permet de déterminer la progression de l’animation.  
  
 Étant donné que la  *\<Type >*AnimationBase classes héritent de la <xref:System.Windows.Freezable> (classe), vous devez également substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour retourner une nouvelle instance de votre classe. Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Pour plus d’informations, consultez la documentation sur la méthode GetCurrentValueCore pour la classe *\<Type >*AnimationBase du type que vous souhaitez animer. Pour obtenir un exemple, consultez [Exemple d’animation personnalisée](http://go.microsoft.com/fwlink/?LinkID=159981)  
  
 **Autres approches**  
  
 Si vous souhaitez simplement modifier la façon dont les valeurs d’animation sont interpolées, envisagez de dériver une des classes *\<Type >*KeyFrame. L’image clé que vous créez est utilisable par les *\<Type >*AnimationUsingKeyFrames correspondants fournis par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="derive-from-animationtimeline"></a>Dérivation à partir de AnimationTimeline  
 Dériver à partir de la <xref:System.Windows.Media.Animation.AnimationTimeline> classe lorsque vous souhaitez créer une animation pour un type qui n’a pas encore une correspondance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animation, ou si vous souhaitez créer une animation qui n’est pas fortement typée.  
  
 **Instructions d’implémentation**  
  
 Dériver à partir de la <xref:System.Windows.Media.Animation.AnimationTimeline> classe et substituer les membres suivants :  
  
-   <xref:System.Windows.Freezable.CreateInstanceCore%2A>– Si votre nouvelle classe est concrète, vous devez substituer <xref:System.Windows.Freezable.CreateInstanceCore%2A> pour retourner une nouvelle instance de votre classe.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>: Remplacez cette méthode pour retourner la valeur actuelle de votre animation. Elle accepte trois paramètres : une valeur d’origine par défaut, une valeur de destination par défaut et un <xref:System.Windows.Media.Animation.AnimationClock>. Utilisez le <xref:System.Windows.Media.Animation.AnimationClock> pour obtenir l’heure actuelle ou la progression de l’animation. Vous pouvez choisir d’utiliser les valeurs d’origine et de destination par défaut.  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A>: Remplacez cette propriété pour indiquer si votre animation utilise la valeur de destination par défaut spécifiée par le <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> (méthode).  
  
-   <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A>: Remplacez cette propriété pour indiquer la <xref:System.Type> de la sortie de votre animation s’est produit.  
  
 Si la classe n’utilise pas de propriétés de dépendance pour stocker ses données ou si elle nécessite une initialisation supplémentaire après la création, vous devrez peut-être substituer d’autres méthodes. Consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md) pour plus d’informations.  
  
 Le paradigme recommandé (utilisé par les animations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) consiste à utiliser deux niveaux d’héritage :  
  
1.  Créer un résumé  *\<Type >*AnimationBase classe qui dérive de <xref:System.Windows.Media.Animation.AnimationTimeline>. Cette classe doit substituer la <xref:System.Windows.Media.Animation.AnimationTimeline.TargetPropertyType%2A> (méthode). Il doit aussi introduire une nouvelle méthode abstraite, GetCurrentValueCore et remplacer <xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A> afin qu’il valide les types de valeur d’origine par défaut et les paramètres de valeur de destination par défaut, puis appeler GetCurrentValueCore.  
  
2.  Créez une autre classe qui hérite de votre nouvelle  *\<Type >*AnimationBase classe et remplace le <xref:System.Windows.Freezable.CreateInstanceCore%2A> méthode, la méthode GetCurrentValueCore introduite, et le <xref:System.Windows.Media.Animation.AnimationTimeline.IsDestinationDefault%2A> propriété.  
  
 **Autres approches**  
  
 Si vous souhaitez animer un type qui n’a aucune animation From/To/By ou une animation d’image clé, envisagez d’utiliser un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>. Car il est faiblement typé, un <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> pouvez animer n’importe quel type de valeur. L’inconvénient de cette approche est que <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> prend uniquement en charge utilisant une interpolation discrète.  
  
<a name="useperframecallback"></a>   
## <a name="use-per-frame-callback"></a>Rappel image par image  
 Utilisez cette approche lorsque vous devez ignorer entièrement le système d’animation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Un scénario pour cette approche est l’animation physique, où pour chaque étape animation une nouvelle direction ou position doit être recalculée pour les objets animés en fonction du dernier jeu d’interactions avec les objets.  
  
 **Instructions d’implémentation**  
  
 Contrairement aux autres approches décrites dans cette vue d’ensemble, le rappel image par image ne nécessite pas de créer une animation personnalisée ou une classe d’image clé.  
  
 Au lieu de cela, vous inscrivez pour le <xref:System.Windows.Media.CompositionTarget.Rendering> événement de l’objet qui contient les objets à animer. Cette méthode de gestionnaire d’événements est appelée une fois par image. Chaque fois que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshale les données de rendu persistantes dans l’arborescence visuelle sur l’arborescence de composition, votre méthode de gestionnaire d’événements est appelée.  
  
 Dans votre gestionnaire d’événements, effectuez les calculs nécessaires pour votre effet d’animation et définissez les propriétés des objets à animer avec ces valeurs.  
  
 Pour obtenir l’heure de la présentation de l’image actuelle, le <xref:System.EventArgs> associé à cet événement peut être casté en <xref:System.Windows.Media.RenderingEventArgs>, qui fournissent un <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> heure de rendu de propriété que vous pouvez utiliser pour obtenir le frame actuel.  
  
 Pour plus d’informations, consultez le <xref:System.Windows.Media.CompositionTarget.Rendering> page.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.IKeyFrame>  
 [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Vue d'ensemble des animations de tracés](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Exemple d’animation personnalisée](http://go.microsoft.com/fwlink/?LinkID=159981)
