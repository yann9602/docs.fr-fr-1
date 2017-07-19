---
title: "Vue d&#39;ensemble des objets Freezable | Microsoft Docs"
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
  - "classes, Freezable"
  - "objets Freezable, description"
  - "libérer des objets Freezable"
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Vue d&#39;ensemble des objets Freezable
Cette rubrique décrit comment utiliser efficacement et créer des objets <xref:System.Windows.Freezable>, qui offrent des fonctionnalités spéciales susceptibles de contribuer à l'amélioration des performances.  Les exemples d'objets freezable incluent les pinceaux, les stylets, les transformations, les géométries et les animations.  
  
 Cette rubrique contient les sections suivantes :  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="whatisafreezable"></a>   
## Qu'est\-ce qu'un Freezable ?  
 Un <xref:System.Windows.Freezable> est un type d'objet spécial qui possède deux états : figé et non figé.  Quand il est non figé, un objet <xref:System.Windows.Freezable> semble se comporter comme n'importe quel autre objet.  Quand il est figé, un objet <xref:System.Windows.Freezable> ne peut plus être modifié.  
  
 Un objet <xref:System.Windows.Freezable> fournit un événement <xref:System.Windows.Freezable.Changed> pour signaler aux observateurs toute modification apportée à l'objet.  Le fait de figer un objet <xref:System.Windows.Freezable> peut améliorer sa performance, car il n'a plus besoin de consacrer des ressources aux notifications des modifications.  Un objet figé <xref:System.Windows.Freezable> peut également être partagé entre plusieurs threads, ce qui n'est pas le cas d'un objet non figé <xref:System.Windows.Freezable>.  
  
 Bien que la classe <xref:System.Windows.Freezable> ait de nombreuses applications, la plupart des objets <xref:System.Windows.Freezable> dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont liés au sous\-système graphique.  
  
 La classe <xref:System.Windows.Freezable> simplifie l'utilisation de certains objets du système graphique et peut améliorer les performances de l'application.  Les exemples des types qui héritent de <xref:System.Windows.Freezable> incluent les classes <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform> et <xref:System.Windows.Media.Geometry>.  Dans la mesure où il contient certaines ressources non managées, le système doit surveiller ces objets en cas de  modifications, puis mettre à jour leurs ressources non managées correspondantes quand une modification intervient dans l'objet d'origine.  Même si vous ne modifiez pas en fait un objet du système graphique, le système doit encore consacrer une partie de ses ressources à la surveillance de l'objet, au cas où vous le modifiez.  
  
 Par exemple, supposons que vous créez un pinceau <xref:System.Windows.Media.SolidColorBrush> et que vous l'utilisez pour peindre l'arrière\-plan d'un bouton.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 Lors du rendu du bouton, le sous\-système graphique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise les informations fournies pour peindre un groupe de pixels en vue de créer l'apparence d'un bouton.  Bien que vous ayez utilisé un pinceau de couleur unie pour décrire comment le bouton doit être peint, votre pinceau de couleur unie ne peint pas vraiment.  Le système graphique génère des objets rapides de bas niveau pour le bouton et le pinceau, et ce sont ces objets qui apparaissent en fait sur l'écran.  
  
 Si vous deviez modifier le pinceau, ces objets seraient à régénérer.  La classe freezable est ce qui permet au pinceau de trouver ses objets de bas niveau générés correspondants pour les mettre à jour quand il change.  Quand cette fonctionnalité est activée, le pinceau est dit « non figé ».  
  
 Une méthode de freezable <xref:System.Windows.Freezable.Freeze%2A> permet de désactiver cette fonctionnalité d'auto\-mise à jour.  Vous pouvez utiliser cette méthode pour rendre le pinceau « figé », ou non modifiable.  
  
> [!NOTE]
>  Les objets Freezable ne peuvent tous être figés.  Pour éviter de générer un <xref:System.InvalidOperationException>, vérifiez la propriété <xref:System.Windows.Freezable.CanFreeze%2A> d'un objet Freezable afin de déterminer s'il peut être figé avant d'essayer de le figer.  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 Lorsque vous n'avez plus besoin de modifier un objet freezable, le fait de le figer présente des avantages.  Si vous deviez figer le pinceau dans cet exemple, le système graphique n'aurait plus à surveiller ses modifications.  Le système graphique peut également effectuer des optimisations, car il sait que le pinceau ne changera pas.  
  
> [!NOTE]
>  Par souci pratique, les objets de type freezable restent non figés jusqu'à ce qu'ils soient figés.  
  
<a name="frozenfreezables"></a>   
## Utilisation des Freezables  
 L'utilisation d'un Freezable non figé est similaire à l'utilisation de tout autre type d'objet.  Dans l'exemple suivant, la couleur d'un <xref:System.Windows.Media.SolidColorBrush> passe du jaune au rouge une fois qu'il a été utilisé pour peindre l'arrière\-plan d'un bouton.  Le système graphique travaille en coulisses pour modifier automatiquement le bouton en faisant passer sa couleur du jaune au rouge lors de la prochaine actualisation de son écran.  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### Figer un Freezable  
 Pour rendre <xref:System.Windows.Freezable> non modifiable, vous appelez sa méthode <xref:System.Windows.Freezable.Freeze%2A>.  Lorsque vous figez un objet qui contient des objets pouvant être figés, ces objets sont également figés.  Par exemple, si vous figez un <xref:System.Windows.Media.PathGeometry>, les figures et les segments qu'il contient seraient également figés.  
  
 Un Freezable **ne peut pas** être figé si l'une des conditions suivantes est vraie :  
  
-   Il dispose de propriétés animées ou liées aux données.  
  
-   Il dispose de propriétés définies par une ressource dynamique.  \(Pour plus d'informations sur les ressources dynamiques, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).\)  
  
-   Il contient des sous\-objets <xref:System.Windows.Freezable> qui ne peuvent pas être figés.  
  
 Si ces conditions ne sont pas réalisées, et que vous n'envisagez pas de modifier <xref:System.Windows.Freezable>, vous devez alors le figer afin de bénéficier du gain de performances décrit plus haut.  
  
 Une fois que vous appelez la méthode<xref:System.Windows.Freezable.Freeze%2A> d'un freezable, celui\-ci ne peut plus être modifié.  Toute tentative visant à modifier un objet figé provoque la levée d'une <xref:System.InvalidOperationException>.  Le code suivant lève une exception, car nous tentons de modifier le pinceau une fois qu'il a été figé.  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 Pour éviter de lever cette exception, vous pouvez utiliser la méthode <xref:System.Windows.Freezable.IsFrozen%2A> pour déterminer si <xref:System.Windows.Freezable> est figé.  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 Dans l'exemple de code précédent, une copie modifiable a été effectuée d'un objet figé à l'aide de la méthode <xref:System.Windows.Freezable.Clone%2A>.  La section traite du clonage plus en détail.  
  
 **Remarque** Dans la mesure où un Freezable figé ne peut pas être animé, le système d'animation créera automatiquement des clones modifiables des objets <xref:System.Windows.Freezable> figés lorsque vous essayez de les animer avec une <xref:System.Windows.Media.Animation.Storyboard>.  Pour éliminer la surcharge de performance liée au clonage, laissez un objet non figé si vous avez l'intention de l'animer.  Pour plus d'informations sur l'animation avec les tables de montage séquentiel, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
### Geler des objets à partir du balisage  
 Pour geler un objet <xref:System.Windows.Freezable> déclaré dans le marquage, vous utilisez l'attribut `PresentationOptions:Freeze`.  Dans l'exemple suivant, un <xref:System.Windows.Media.SolidColorBrush> est déclaré en tant que ressource de page et figé.  Il est ensuite utilisé pour définir l'arrière\-plan d'un bouton.  
  
 [!code-xml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 Pour utiliser l'attribut `Freeze`, vous devez mapper à l'espace de noms des options de présentation : `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` `PresentationOptions` est le préfixe recommandé pour le mappage de cet espace de noms :  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 Dans la mesure où les lecteurs XAML ne reconnaissent pas cet attribut, il est recommandé d'utiliser l'[mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) pour marquer l'attribut `Presentation:Freeze` comme pouvant être ignoré :  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 Pour plus d'informations, consultez la page [mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).  
  
### « Libération » d'un Freezable figé  
 Une fois figé, un <xref:System.Windows.Freezable> ne peut jamais être modifié ou libéré de son état figé ; cependant, vous pouvez créer un clone non figé à l'aide de la méthode <xref:System.Windows.Freezable.Clone%2A> ou <xref:System.Windows.Freezable.CloneCurrentValue%2A>.  
  
 Dans l'exemple suivant, l'arrière\-plan d'un bouton est défini à l'aide d'un pinceau et ce pinceau est figé.  Une copie non figée du pinceau est effectuée à l'aide de la méthode <xref:System.Windows.Freezable.Clone%2A>.  Le clone est modifié et utilisé pour changer l'arrière\-plan du bouton en faisant passer sa couleur de jaune à rouge.  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  Indépendamment de la méthode de clone que vous utilisez, les animations ne sont jamais copiées vers le nouveau <xref:System.Windows.Freezable>.  
  
 Les méthodes <xref:System.Windows.Freezable.Clone%2A> et <xref:System.Windows.Freezable.CloneCurrentValue%2A> génèrent des copies complètes du Freezable.  Si le Freezable contient d'autres objets Freezable figés, ils sont également clonés et rendus modifiables.  Par exemple, si vous clonez un <xref:System.Windows.Media.PathGeometry> figé pour le rendre modifiable, les figures et segments qu'il contient sont également copiés et rendus modifiables.  
  
<a name="createyourownfreezableclass"></a>   
## Création de votre propre classe Freezable  
 Une classe qui dérive de <xref:System.Windows.Freezable> acquiert les fonctionnalités suivantes.  
  
-   États spéciaux : en lecture seule \(figé\) et un état d'écriture.  
  
-   Sécurité des threads : un objet <xref:System.Windows.Freezable> figé peut être partagé entre plusieurs threads.  
  
-   Notification de modifications détaillée : contrairement à d'autres objets <xref:System.Windows.DependencyObject>, les objets Freezable fournissent des notifications de modifications lorsque les valeurs de sous\-propriété sont modifiées.  
  
-   Clonage facile : la classe Freezable a déjà implémenté plusieurs méthodes qui génèrent des clones complets.  
  
 Un <xref:System.Windows.Freezable> est un type de <xref:System.Windows.DependencyObject>, et utilise en conséquence le système de propriétés de dépendance.  Il n'est pas nécessaire que vos propriétés de classe soient des propriétés de dépendance, mais l'utilisation des propriétés de dépendance réduit la quantité de code que vous devez écrire, car la classe <xref:System.Windows.Freezable> a été conçue avec les propriétés de dépendance en tête.  Pour plus d'informations sur le système de propriétés de dépendance, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Chaque sous\-classe <xref:System.Windows.Freezable> doit substituer la méthode <xref:System.Windows.Freezable.CreateInstanceCore%2A>.  Si votre classe utilise des propriétés de dépendance pour toutes ses données, votre tâche est terminée.  
  
 Si votre classe contient des membres de données de propriétés de non dépendance, vous devez également substituer les méthodes suivantes :  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 Vous devez également observer les règles suivantes pour l'accès aux données membres \(et leur écriture\) qui ne correspondent pas à des propriétés de dépendance :  
  
-   Au début de toute [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] qui lit les données membres de propriétés de non dépendance, appelez la méthode <xref:System.Windows.Freezable.ReadPreamble%2A>.  
  
-   Au début de toute API qui écrit des données membres de propriétés de non dépendance, appelez la méthode <xref:System.Windows.Freezable.WritePreamble%2A>.  \(Une fois que vous avez appelé <xref:System.Windows.Freezable.WritePreamble%2A> dans une [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], vous n'avez pas besoin d'effectuer un appel supplémentaire à <xref:System.Windows.Freezable.ReadPreamble%2A> si vous lisez également les données membres de propriétés de non dépendance.\)  
  
-   Appelez la méthode <xref:System.Windows.Freezable.WritePostscript%2A> avant de quitter les méthodes qui écrivent dans les données membres de propriétés de non dépendance.  
  
 Si votre classe contient des données membres de propriétés de non dépendance qui sont des objets <xref:System.Windows.DependencyObject>, vous devez également appeler la méthode <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> chaque fois que vous changez leurs valeurs, même si vous attribuez au membre la valeur `null`.  
  
> [!NOTE]
>  Il est très important de commencer chaque méthode <xref:System.Windows.Freezable> que vous substituez avec un appel à l'implémentation de base.  
  
 Pour obtenir un exemple d'une classe <xref:System.Windows.Freezable> personnalisée, consultez [Animation personnalisée, exemple](http://go.microsoft.com/fwlink/?LinkID=159981).  
  
## Voir aussi  
 <xref:System.Windows.Freezable>   
 [Animation personnalisée, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159981)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)