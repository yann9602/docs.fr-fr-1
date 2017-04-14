---
title: "Gestion et d&#233;clenchement d&#39;&#233;v&#233;nements | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "développement d'applications (.NET Framework), événements"
  - "modèle délégué des événements"
  - "événements (.NET Framework)"
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Gestion et d&#233;clenchement d&#39;&#233;v&#233;nements
Dans le .NET Framework, les événements reposent sur le modèle délégué.  Le modèle délégué suit le modèle de conception observateur, qui permet à un abonné de s'inscrire pour recevoir des notifications d'un fournisseur.  Un émetteur d'événement émet une notification d'événement, et un récepteur d'événements reçoit cette notification et définit une réponse à celle\-ci.  Cet article décrit les principaux composants du modèle délégué, comment consommer des événements dans des applications, et comment implémenter des événements dans votre code.  
  
 Pour plus d'informations sur la gestion des événements dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], voir [Présentation des événements et des événements routés \(Applications Windows Store\)](http://go.microsoft.com/fwlink/p/?LinkId=261485).  
  
## Événements  
 Un événement est un message transmis par un objet pour signaler l'occurrence d'une action.  L'action peut être provoquée par une intervention de l'utilisateur, telle qu'un clic de bouton, ou peut être déclenchée par une autre logique de programme, comme modifier une valeur de propriété.  L'objet qui déclenche l'événement est appelé *émetteur d'événement*.  L'émetteur d'événement ne connaît pas l'objet ou la méthode qui recevront \(géreront\) les événements qu'elle déclenche.  L'événement est généralement un membre de l'émetteur d'événement ; par exemple, l'événement <xref:System.Web.UI.WebControls.Button.Click> est membre de la classe <xref:System.Web.UI.WebControls.Button>, et l'événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> est membre de la classe qui implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pour définir un événement, utilisez le mot clé `event` \(en C\#\) ou `Event` \(en Visual Basic\) dans la signature de votre classe d'événements, puis spécifiez le type de délégué pour l'événement.  Les délégués sont décrits dans la section suivante.  
  
 En général, pour déclencher un événement, ajoutez une méthode qui est marquée comme `protected` et `virtual` \(C\#\) ou `Protected` et `Overridable` \(en Visual Basic\).  Nommez cette méthode `On`*EventName*; par exemple, `OnDataReceived`.  La méthode doit prendre un paramètre qui spécifie un objet de données d'événement.  Vous fournissez cette méthode pour permettre aux classes dérivées de substituer la logique de déclenchement d'événement.  Une classe dérivée doit toujours appeler la méthode `On`*NomEvenementEventName* de la classe de base pour que les délégués inscrits puissent recevoir l'événement.  
  
 L'exemple suivant montre comment déclarer une fonction appelée `ThresholdReached` :  L'événement est associé au délégué <xref:System.EventHandler> et déclenché dans une méthode nommée `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## Délégués  
 Un délégué est un type contenant une référence à une méthode.  Un délégué est déclaré avec une signature qui indique le type de retour et les paramètres des méthodes qu'il référence, et peut contenir des références à des méthodes qui correspondent à sa signature.  Un délégué est par conséquent l'équivalent d'un rappel de fonction ou d'un pointeur fonction de type sécurisé.  Une déclaration delegate suffit pour définir une classe déléguée.  
  
 Les délégués ont de nombreux usages dans le .NET Framework.  Dans le contexte des événements, un délégué est un intermédiaire \(ou un mécanisme similaire aux pointeurs\) entre la source d'événements et le code qui gère l'événement.  Vous associez un délégué à un événement en incluant le type du délégué dans la déclaration de l'événement, comme indiqué dans l'exemple de la section précédente.  Pour plus d'informations sur les délégués, consultez la classe <xref:System.Delegate>.  
  
 Le .NET Framework fournit les délégués <xref:System.EventHandler> et <xref:System.EventHandler%601> pour prendre en charge la plupart des scénarios d'événement.  Utilisez le délégué <xref:System.EventHandler> pour tous les événements qui n'incluent pas de données d'événement.  Utilisez le délégué <xref:System.EventHandler%601> pour les événements qui incluent des données sur l'événement.  Ces délégués n'ont aucune valeur de type de retour et prennent deux paramètres \(un objet pour la source de l'événement et un objet pour les données d'événement\).  
  
 Les délégués sont multicast, ce qui signifie qu'ils peuvent contenir des références à plusieurs méthodes de gestion des événements.  Pour plus d'informations, consultez la page de référence de <xref:System.Delegate>.  Les délégués assurent une souplesse et un contrôle précis lors de la gestion des événements.  Un délégué joue le rôle de répartiteur d'événement pour la classe qui déclenche l'événement en tenant à jour une liste des gestionnaires d'événements inscrits pour l'événement.  
  
 Pour les scénarios dans lesquels les délégués <xref:System.EventHandler> et <xref:System.EventHandler%601> ne fonctionnent pas, vous pouvez définir un délégué.  Les scénarios qui nécessitent de définir un délégué sont très rares, par exemple lorsque vous devez utiliser du code qui ne reconnaît pas les génériques.  Vous marquez un délégué avec `delegate` dans \(C\#\) et le mot clé d'`Delegate` \(en Visual Basic\) dans la déclaration.  L'exemple suivant montre comment décmarer un délégué nommé `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## Données de l'événement  
 Les données associées à un événement peuvent être obtenues via une classe de données d'événement.  Le .NET Framework fournit plusieurs classes de données d'événement que vous pouvez utiliser dans vos applications.  Par exemple, la classe <xref:System.IO.Ports.SerialDataReceivedEventArgs> est la classe de données d'événement pour l'événement <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=fullName>.  Le .NET Framework suit un modèle de nommage qui veut que toutes les classes de données d'évènement se terminent par `EventArgs`.  Pour savoir quelle classe de données d'événement est associé à un événement, il suffit d'examiner le délégué de l'événement.  Par exemple, le délégué <xref:System.IO.Ports.SerialDataReceivedEventHandler> inclut la classe <xref:System.IO.Ports.SerialDataReceivedEventArgs> comme paramètre.  
  
 La classe <xref:System.EventArgs> est le type de base pour toutes les classes de données d'événement.  <xref:System.EventArgs> est également la classe que vous utilisez quand un événement n'a pas de données associée.  Lorsque vous créez un événement qui est uniquement destiné à notifier d'autres classes que quelque chose est advenu et n'a pas besoin de passer des données, incluez la classe <xref:System.EventArgs> comme deuxième paramètre du délégué.  Vous pouvez passer la valeur <xref:System.EventArgs.Empty?displayProperty=fullName> lorsqu'aucune donnée n'est fournie.  Le délégué <xref:System.EventHandler> inclut la classe <xref:System.EventArgs> comme paramètre.  
  
 Lorsque vous souhaitez créer une classe personnalisée de données d'événement, créez une classe qui dérive de <xref:System.EventArgs>, puis fournissez tous les membres requis pour passer les données liée à l'événement.  En général, vous devriez utiliser le même modèle d'affectation de noms que .NET Framework et terminer le nom de classe de données d'événement avec `EventArgs`.  
  
 L'exemple suivant illustre une classe de données d'événement nommée `ThresholdReachedEventArgs`..  Elle contient les propriétés spécifiques à l'événement déclenché.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## Gestionnaires d'événements  
 Pour répondre à un événement, vous définissez une méthode de gestion d'événements dans le récepteur d'événements.  Cette méthode doit correspondre à la signature du délégué pour l'événement géré.  Dans le gestionnaire, vous exécutez les actions nécessaires lorsque l'événement est déclenché, comme la collecte de l'entrée d'utilisateur après que l'utilisateur clique sur un bouton.  Pour recevoir des notifications lorsque l'événement se produit, votre méthode de gestionnaire d'événements doit s'abonner à l'événement.  
  
 L'exemple suivant présente une méthode de gestionnaire d'événements nommée `c_ThresholdReached` qui correspond à la signature du délégué <xref:System.EventHandler>.  La méthode s'abonne à l'événement `ThresholdReached`.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## Gestionnaires d'événements statiques et dynamiques  
 Le .NET Framework permet aux abonnées de s'inscrire pour recevoir des notifications d'événements statiques ou dynamiques.  Les gestionnaires d'événements statiques sont actifs pour la durée de vie complète de la classe dont ils gèrent les événements.  Les gestionnaires d'événements dynamiques sont activés et désactivés explicitement pendant l'exécution du programme, généralement en réponse à une logique de programme conditionnelle.  Ils peuvent être utilisés par exemple lorsque des notifications d'événements sont nécessaires dans certaines conditions seulement ou si une application fournit plusieurs gestionnaires d'événements et si les conditions d'exécution définissent le gestionnaire à utiliser.  L'exemple de la section précédente indique comment ajouter dynamiquement un gestionnaire d'événements.  Pour plus d’informations, consultez [Events](../Topic/Events%20\(Visual%20Basic\).md) et [Événements](../Topic/Events%20\(C%23%20Programming%20Guide\).md).  
  
## Déclenchement de plusieurs événements  
 Si votre classe déclenche plusieurs événements, le compilateur génère un champ par instance de délégué d'événement.  En cas de nombre élevé d'événements, le coût du stockage d'un champ par délégué risque de ne pas être acceptable.  Dans ce cas, le .NET Framework fournit une des propriétés d'événementque vous pouvez utiliser avec une autre structure de données de votre choix pour stocker les délégués d'événement.  
  
 Les propriétés d'événement se composent de déclarations d'événement accompagnées d'accesseurs d'événement.  Les accesseurs d'événement sont des méthodes que vous définissez pour que des instances de délégué d'événement puissent être ajoutées à la structure des données de stockage ou en être supprimées.  Notez que les propriétés d'événement sont plus lentes que les champs d'événement, car chaque délégué d'événement doit être récupéré avant de pouvoir être appelé.  Le compromis réside entre la mémoire et la vitesse.  Si votre classe définit plusieurs événements qui ne sont pas souvent déclenchés, vous pouvez alors implémenter des propriétés d'événement.  Pour plus d'informations, consultez [Comment : gérer plusieurs événements à l'aide des propriétés d'événements](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Comment : déclencher et utiliser des événements](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Contient des exemples de déclenchement et de consommation d'événements.|  
|[Comment : gérer plusieurs événements à l'aide des propriétés d'événements](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Montre comment utiliser des propriétés d'événement pour gérer plusieurs événements.|  
|[Modèle de design observateur](../../../docs/standard/events/observer-design-pattern.md)|Décrit le modèle de conception qui permet à un abonné de s'inscrire pour recevoir des notifications d'un fournisseur.|  
|[Comment : consommer des événements dans une application Web Forms](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Montre comment gérer un événement déclenché par un contrôle Web Forms.|  
  
## Voir aussi  
 <xref:System.EventHandler>   
 <xref:System.EventHandler%601>   
 <xref:System.EventArgs>   
 <xref:System.Delegate>   
 [Présentation des événements et des événements routés \(Applications Windows store\)](http://go.microsoft.com/fwlink/?LinkId=261485)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)   
 [Événements](../Topic/Events%20\(C%23%20Programming%20Guide\).md)