---
title: "Mod&#232;les d&#39;&#233;v&#233;nement faible | Microsoft Docs"
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
  - "gestionnaires d'événements, modèle d'événement faible"
  - "IWeakEventListener (interface)"
  - "implémentation de modèle d'événement faible"
  - "WeakEventManager (classe)"
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Mod&#232;les d&#39;&#233;v&#233;nement faible
Il est possible que les gestionnaires attachés à des sources d'événement dans les applications ne soient pas détruits en coordination avec l'objet écouteur qui a attaché le gestionnaire à la source.  Cette situation peut entraîner des fuites de mémoire.  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] introduit un modèle de conception qui permet de traiter ce problème en fournissant une classe de gestionnaire dédiée pour des événements particuliers et en implémentant une interface sur les écouteurs de ces événements.  Ce modèle de conception est appelé *modèle d'événement faible*.  
  
## Pourquoi implémenter le modèle d'événement faible ?  
 L'écoute des événements peut générer des fuites de mémoire.  La technique standard pour écouter un événement consiste à utiliser la syntaxe du langage qui attache un gestionnaire à un événement d'une source.  Par exemple, en [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], cette syntaxe est `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Cette technique crée une référence forte entre la source d'événement et l'écouteur d'événement.  En général, lorsque vous attachez un gestionnaire d'événements pour un écouteur, la durée de vie d'objet de l'écouteur est influencée par celle de la source \(à moins que le gestionnaire d'événement ne soit explicitement supprimé\).  Toutefois, dans certains cas, il peut s'avérer utile de contrôler la durée de vie d'objet de l'écouteur par des facteurs tels que son appartenance actuelle à l'arborescence d'éléments visuels de l'application, et non pas par la durée de vie de la source.  Chaque fois que la durée de vie d'objet de la source est plus longue que celle de l'écouteur, le modèle d'événement normal génère une fuite de mémoire ; l'écouteur reste actif plus longtemps que prévu.  
  
 Le modèle d'événement faible est conçu pour résoudre ce problème de fuite de mémoire.  Il peut être utilisé chaque fois qu'un écouteur doit s'inscrire pour un événement et qu'il ne sait pas explicitement quand l'inscription doit être annulée.  Il peut également être employé chaque fois que la durée de vie d'objet de la source dépasse la durée de vie d'objet utile de l'écouteur.  \(Dans ce cas, c'est vous qui déterminez la notion d'*utilité*.\) Le modèle d'événement faible permet à l'écouteur de s'inscrire pour l'événement et de le recevoir sans affecter, de quelque manière que ce soit, les caractéristiques de durée de vie d'objet de l'écouteur.  En fait, la référence implicite de la source ne détermine pas si l'écouteur est disponible pour le garbage collection.  La référence est une référence faible, d'où le nom donné au modèle et aux [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] associées.  L'écouteur peut être récupéré par le garbage collector ou détruit, et la source peut continuer sans conserver des références de gestionnaire non\-collectable à un objet détruit.  
  
## Qui doit implémenter le modèle d'événement faible ?  
 L'implémentation du modèle d'événement faible concerne principalement les auteurs de contrôle.  En tant qu'auteur de contrôle, vous êtes principalement responsable du comportement et de la relation contenant\-contenu de votre contrôle, ainsi que de son impact sur les applications dans lesquelles il est inséré.  Cela inclut le comportement de durée de vie d'objet du contrôle, et notamment la gestion du problème de fuite de mémoire décrit.  
  
 Certains scénarios se prêtent par nature à l'application du modèle d'événement faible.  La liaison de données fait partie de ces scénarios.  Dans une liaison de données, l'objet source est en général complètement indépendant de l'objet écouteur, qui est une cible de la liaison.  Le modèle d'événement faible s'applique déjà à nombreux aspects de la liaison de données [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] quant la façon dont les événements sont implémentés.  
  
## Comment implémenter le modèle d'événement faible ?  
 Il existe trois façons d'implémenter le modèle d'événement faible.  Le tableau suivant répertorie les trois méthodes et fournit de l'aide lorsque vous devez utiliser chacun.  
  
|Approche|Lors de l'implémentation|  
|--------------|------------------------------|  
|utilisez une classe faible existante de gestionnaire d'événement|si l'événement que vous souhaitez abonner a <xref:System.Windows.WeakEventManager>correspondant, utilisent le gestionnaire faible existant d'événement.  Pour une liste des gestionnaires faibles d'événement qui sont inclus avec WPF, consultez la hiérarchie d'héritage dans la classe d' <xref:System.Windows.WeakEventManager> .  Notez, cependant, qu'il existe très peu de gestionnaires faibles d'événement qui sont inclus avec WPF, vous devrez probablement choisir une des autres approches.|  
|utilisez une classe faible générique de gestionnaire d'événement|Utilisez <xref:System.Windows.WeakEventManager%602> générique lorsque <xref:System.Windows.WeakEventManager> existant est pas disponible, vous voulez un moyen simple d'implémenter, et vous ne souhaitez pas transmettre l'efficacité.  <xref:System.Windows.WeakEventManager%602> générique est moins efficace que existant ou un gestionnaire faible personnalisé d'événement.  Par exemple, la classe générique envoie plus de réflexion pour découvrir l'événement donné au nom de l'événement.  En outre, le code pour stocker l'événement à l'aide de <xref:System.Windows.WeakEventManager%602> générique est plus documentée que d'utiliser ou existantes <xref:System.Windows.WeakEventManager>personnalisé.|  
|Créez une classe faible personnalisée du gestionnaire d'événement|Créez <xref:System.Windows.WeakEventManager> personnalisé lorsque vous <xref:System.Windows.WeakEventManager> existant est pas disponible et que vous souhaitez que la meilleure efficacité.  À l'aide d'un personnalisé <xref:System.Windows.WeakEventManager> abonner à un événement sera plus efficace, mais vous entraînez le coût d'écrire du code supplémentaire au début.|  
  
 les sections suivantes décrivent comment implémenter le modèle d'événement faible.  Pour les besoins de cette discussion, l'événement à l'abonner possède les caractéristiques suivantes.  
  
-   le nom de l'évènement est `SomeEvent`.  
  
-   l'événement est déclenché par la classe d' `EventSource` .  
  
-   le gestionnaire d'événements a le type : `SomeEventEventHandler` \(ou `EventHandler<SomeEventEventArgs>`\).  
  
-   l'événement passe un paramètre de type `SomeEventEventArgs` aux gestionnaires d'événements.  
  
### À l'aide d'une classe faible existante de gestionnaire d'événement  
  
1.  recherchez un gestionnaire faible existant d'événement.  
  
     Pour une liste des gestionnaires faibles d'événement qui sont inclus avec WPF, consultez la hiérarchie d'héritage dans la classe d' <xref:System.Windows.WeakEventManager> .  
  
2.  Utilisez le nouveau gestionnaire d'événement faible au lieu de la liaison normale d'événement.  
  
     Par exemple, si votre code utilise le modèle suivant pour s'abonner à un événement :  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     modifiez\-la au modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De même, si votre code utilise le modèle suivant pour annuler un abonnement à un événement :  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     modifiez\-la au modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### À l'aide de la classe faible générique de gestionnaire d'événement  
  
1.  utilisez la classe générique d' <xref:System.Windows.WeakEventManager%602> au lieu de la liaison normale d'événement.  
  
     Lorsque vous utilisez <xref:System.Windows.WeakEventManager%602> pour stocker des écouteurs d'événements, vous fournissez une source d'événements et le type d' <xref:System.EventArgs> comme paramètres de type à la classe et appelez <xref:System.Windows.WeakEventManager%602.AddHandler%2A> comme indiqué dans le code suivant :  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### Créer une classe faible personnalisée du gestionnaire d'événement  
  
1.  copiez le modèle de classe suivant à votre projet.  
  
     Cette classe hérite de la classe <xref:System.Windows.WeakEventManager>.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  remplacez le nom d' `SomeEventWeakEventManager` par votre propre nom.  
  
3.  Remplacez les trois étiquettes décrits précédemment par les noms correspondants pour votre événement.  \(`SomeEvent`, `EventSource`, et `SomeEventEventArgs`\)  
  
4.  Définissez la visibilité \(publique\/interne\/privée\) de la classe faible de gestionnaire d'événements à la même visibilité que l'événement il gère.  
  
5.  Utilisez le nouveau gestionnaire d'événement faible au lieu de la liaison normale d'événement.  
  
     Par exemple, si votre code utilise le modèle suivant pour s'abonner à un événement :  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     modifiez\-le au modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     De même, si votre code utilise le modèle suivant pour annuler un abonnement à un événement :  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     modifiez\-la au modèle suivant :  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## Voir aussi  
 <xref:System.Windows.WeakEventManager>   
 <xref:System.Windows.IWeakEventListener>   
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)