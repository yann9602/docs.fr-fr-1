---
title: "Deciding When to Implement the Event-based Asynchronous Pattern | Microsoft Docs"
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
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "AsyncOperation class"
  - "AsyncCompletedEventArgs class"
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Deciding When to Implement the Event-based Asynchronous Pattern
Le modèle asynchrone basé sur les événements fournit un modèle visant à exposer le comportement asynchrone d'une classe.  Avec l'introduction de ce modèle, le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] définit deux modèles pour exposer le comportement asynchrone : le modèle asynchrone basé sur l'interface <xref:System.IAsyncResult?displayProperty=fullName> et le modèle basé sur les événements.  Cette rubrique décrit les circonstances dans lesquelles implémenter chacun des deux modèles.  
  
 Pour plus d'informations sur la programmation asynchrone avec l'interface <xref:System.IAsyncResult>, consultez [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
## Principes généraux  
 En général, vous devez exposer des fonctionnalités asynchrones à l'aide du modèle asynchrone basé sur les événements chaque fois que c'est possible.  Toutefois, le modèle basé sur les événements ne peut répondre à certaines exigences.  Dans de tels cas, vous devez parfois implémenter le modèle <xref:System.IAsyncResult> en plus du modèle basé sur les événements.  
  
> [!NOTE]
>  Il est rare d'implémenter le modèle <xref:System.IAsyncResult> sans implémenter également le modèle basé sur les événements.  
  
## Indications  
 La liste suivante décrit les indications à respecter lorsque vous devez implémenter le modèle asynchrone basé sur les événements :  
  
-   Utilisez le modèle basé sur les événements comme API par défaut pour exposer le comportement asynchrone de votre classe.  
  
-   N'exposez pas le modèle <xref:System.IAsyncResult> lorsque votre classe est principalement utilisée dans une application cliente, par exemple Windows Forms.  
  
-   Exposez uniquement le modèle <xref:System.IAsyncResult> lorsque vos besoins l'exigent.  Par exemple,il se peut que vous deviez exposer le modèle <xref:System.IAsyncResult> à des fins de compatibilité avec une API existante.  
  
-   N'exposez pas le modèle <xref:System.IAsyncResult> sans exposer également le modèle basé sur les événements.  
  
-   Si vous devez exposer le modèle <xref:System.IAsyncResult>, faites\-le en tant qu'option avancée.  Par exemple, si vous générez un objet proxy, générez le modèle basé sur les événements par défaut, avec une option pour générer le modèle <xref:System.IAsyncResult>.  
  
-   Créez votre implémentation du modèle basé sur les événements sur votre implémentation du modèle <xref:System.IAsyncResult>.  
  
-   Évitez d'exposer le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur la même classe.  Exposez le modèle basé sur les événements sur les classes de « niveau supérieur » et le modèle <xref:System.IAsyncResult> sur les classes de « niveau inférieur ».  Comparez, par exemple, le modèle basé sur les événements sur le composant <xref:System.Net.WebClient> au modèle <xref:System.IAsyncResult> sur la classe <xref:System.Web.HttpRequest>.  
  
    -   Exposez le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur la même classe lorsque la compatibilité l'exige.  Si, par exemple, vous avez déjà publié une API qui utilise le modèle <xref:System.IAsyncResult>, vous devez conserver le modèle <xref:System.IAsyncResult> à des fins de compatibilité descendante.  
  
    -   Exposez le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur la même classe si la complexité du modèle d'objet résultant neutralise l'avantage conféré par la séparation des implémentations.  Il est préférable d'exposer les deux modèles sur une même classe que de ne pas pouvoir exposer le modèle basé sur les événements.  
  
    -   Si vous devez exposer le modèle basé sur les événements et le modèle <xref:System.IAsyncResult> sur une même classe, utilisez <xref:System.ComponentModel.EditorBrowsableAttribute> avec la valeur <xref:System.ComponentModel.EditorBrowsableState> pour marquer l'implémentation du modèle <xref:System.IAsyncResult> comme une fonctionnalité avancée.  La définition de cet attribut indique aux environnements de design, tels que [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] IntelliSense, de ne pas afficher les propriétés et les méthodes <xref:System.IAsyncResult>.  Ces propriétés et méthodes sont toujours utilisables mais le développeur qui se sert d'IntelliSense possède une vue plus claire de l'API.  
  
## Critères justifiant l'exposition du modèle IAsyncResult en plus du modèle basé sur les événements  
 Si le modèle asynchrone basé sur les événements comporte de nombreux avantages dans les scénarios précités, il présente toutefois quelques inconvénients dont vous devez être conscient si les performances sont essentielles pour vous.  
  
 Le modèle basé sur les événements s'avère moins adapté que le modèle <xref:System.IAsyncResult> dans trois cas de figure :  
  
-   Blocage de l'attente sur un objet <xref:System.IAsyncResult>  
  
-   Blocage de l'attente sur de nombreux objets <xref:System.IAsyncResult>  
  
-   Interrogation de <xref:System.IAsyncResult> quant à son achèvement  
  
 Vous pouvez, certes, utiliser le modèle basé sur les événements dans ces scénarios mais c'est plus fastidieux qu'avoir recours au modèle <xref:System.IAsyncResult>.  
  
 Les développeurs utilisent souvent le modèle <xref:System.IAsyncResult> pour les services qui exigent des performances élevées.  Par exemple, le scénario d'interrogation sur l'achèvement est une technique serveur hautes performances.  
  
 En outre, le modèle basé sur les événements est moins efficace que le modèle <xref:System.IAsyncResult> parce qu'il crée davantage d'objets, surtout des objets <xref:System.EventArgs> et qu'il effectue une synchronisation entre les threads.  
  
 La liste suivante affiche quelques recommandations à suivre si vous décidez d'utiliser le modèle <xref:System.IAsyncResult> :  
  
-   Exposez uniquement le modèle <xref:System.IAsyncResult> lorsque vous avez spécifiquement besoin d'une prise en charge des objets <xref:System.Threading.WaitHandle> ou <xref:System.IAsyncResult>.  
  
-   Exposez uniquement le modèle <xref:System.IAsyncResult> lorsqu'une API existante utilise le modèle <xref:System.IAsyncResult>.  
  
-   Si vous avez une API existante basée sur le modèle <xref:System.IAsyncResult>, envisagez d'exposer également le modèle basé sur les événements dans votre prochaine version.  
  
-   Exposez uniquement le modèle <xref:System.IAsyncResult> si vous avez des exigences élevées en termes de performances qui s'avèrent, après vérification, impossibles à satisfaire avec le modèle basé sur les événements mais bien avec le modèle <xref:System.IAsyncResult>.  
  
## Voir aussi  
 [Walkthrough: Implementing a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)   
 [Implementing the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)   
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)