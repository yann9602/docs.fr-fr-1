---
title: "Choix du moment auquel implémenter le modèle asynchrone basé sur les événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48de1b736c251a61a2ad34975c77bc2bca139626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Choix du moment auquel implémenter le modèle asynchrone basé sur les événements
Le modèle asynchrone basé sur événement fournit un modèle pour exposer le comportement asynchrone d’une classe. Avec l’introduction de ce modèle, le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] définit deux modèles pour exposer le comportement asynchrone : le modèle asynchrone basé sur le <xref:System.IAsyncResult?displayProperty=nameWithType> interface et le modèle basé sur les événements. Cette rubrique explique quand il convient pour pouvoir implémenter les deux modèles.  
  
 Pour plus d’informations sur la programmation asynchrone avec le <xref:System.IAsyncResult> l’interface, consultez [modèle asynchrone basé sur des événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
## <a name="general-principles"></a>Principes généraux  
 En règle générale, vous devez exposer des fonctionnalités asynchrones à l’aide du modèle asynchrone basé sur les événements chaque fois que possible. Toutefois, il existe certaines exigences qui ne satisfait pas le modèle basé sur les événements. Dans ce cas, vous devez implémenter la <xref:System.IAsyncResult> modèle en plus du modèle basé sur les événements.  
  
> [!NOTE]
>  Il est rare pour la <xref:System.IAsyncResult> modèle à mettre en œuvre sans l’implémenter également le modèle basé sur des événements.  
  
## <a name="guidelines"></a>Recommandations  
 La liste suivante décrit les instructions pour lorsque vous devez implémenter le modèle asynchrone basé sur des événements :  
  
-   Utiliser le modèle basé sur les événements que l’API par défaut pour exposer le comportement asynchrone pour votre classe.  
  
-   N’exposez pas le <xref:System.IAsyncResult> de modèle lorsque votre classe est principalement utilisée dans une application cliente, par exemple Windows Forms.  
  
-   Exposer uniquement les <xref:System.IAsyncResult> modèle lorsqu’il est nécessaire pour répondre à vos besoins. Par exemple, la compatibilité avec une API existante peut nécessiter vous permettent d’exposer le <xref:System.IAsyncResult> modèle.  
  
-   N’exposez pas le <xref:System.IAsyncResult> modèle sans exposer également le modèle basé sur les événements.  
  
-   Si vous devez exposer le <xref:System.IAsyncResult> de modèle, faire une option avancée. Par exemple, si vous générez un objet proxy, générez le modèle basé sur les événements par défaut, avec une option pour générer la <xref:System.IAsyncResult> modèle.  
  
-   Générer votre implémentation d’un modèle basé sur les événements sur votre <xref:System.IAsyncResult> implémentation du modèle.  
  
-   Évitez d’exposer à la fois le modèle basé sur les événements et les <xref:System.IAsyncResult> modèle sur la même classe. Exposer le modèle basé sur les événements sur les classes de « niveau supérieur » et le <xref:System.IAsyncResult> sur « niveau inférieur » des classes de modèle. Par exemple, de comparer le modèle basé sur les événements sur le <xref:System.Net.WebClient> composant portant le <xref:System.IAsyncResult> de modèle sur le <xref:System.Web.HttpRequest> classe.  
  
    -   Exposer le modèle basé sur les événements et les <xref:System.IAsyncResult> modèle sur la même classe lorsque la compatibilité l’exige. Par exemple, si vous avez déjà publié une API qui utilise le <xref:System.IAsyncResult> modèle, vous devez conserver le <xref:System.IAsyncResult> modèle pour la compatibilité descendante.  
  
    -   Exposer le modèle basé sur les événements et les <xref:System.IAsyncResult> si la complexité du modèle objet résultant neutralise l’avantage de séparer les implémentations de modèle sur la même classe. Il est préférable d’exposer les deux modèles sur une même classe que de ne pas exposer le modèle basé sur des événements.  
  
    -   Si vous devez exposer à la fois le modèle basé sur les événements et <xref:System.IAsyncResult> modèle sur une seule classe, utilisez <xref:System.ComponentModel.EditorBrowsableAttribute> la valeur <xref:System.ComponentModel.EditorBrowsableState.Advanced> pour marquer le <xref:System.IAsyncResult> implémentation du modèle comme une fonctionnalité avancée. Cela indique aux environnements de conception, telles que [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] IntelliSense, de ne pas afficher le <xref:System.IAsyncResult> propriétés et méthodes. Ces propriétés et méthodes sont toujours utilisables, mais le développeur progresse-t-elle dans IntelliSense dispose d’une vue plus claire de l’API.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Critères pour l’exposition du modèle IAsyncResult en plus du modèle basé sur des événements  
 Le modèle asynchrone basé sur événement présente de nombreux avantages dans les cas mentionnés précédemment, mais il dispose des inconvénients, vous devez être conscient de si les performances sont essentielles.  
  
 Il existe trois scénarios qui ne traite pas du modèle basé sur des événements, ainsi que les <xref:System.IAsyncResult> modèle :  
  
-   Blocage de l’attente sur un<xref:System.IAsyncResult>  
  
-   Blocage de l’attente sur de nombreux <xref:System.IAsyncResult> objets  
  
-   Interrogation de l’achèvement de la<xref:System.IAsyncResult>  
  
 Vous pouvez gérer ces scénarios à l’aide du modèle basé sur des événements, mais c’est plus lourd que l’utilisation de la <xref:System.IAsyncResult> modèle.  
  
 Les développeurs utilisent souvent le <xref:System.IAsyncResult> modèle pour les services qui exigent des performances très élevées. Par exemple, l’interrogation pour le scénario de saisie semi-automatique est une technique serveur hautes performances.  
  
 En outre, le modèle basé sur les événements est moins efficace que la <xref:System.IAsyncResult> , car il crée davantage d’objets, en particulier de modèle <xref:System.EventArgs>, et parce que la synchronisation entre les threads.  
  
 La liste suivante présente quelques recommandations à suivre si vous décidez d’utiliser le <xref:System.IAsyncResult> modèle :  
  
-   Exposer uniquement les <xref:System.IAsyncResult> de modèle lorsque vous avez besoin en particulier la prise en charge de <xref:System.Threading.WaitHandle> ou <xref:System.IAsyncResult> objets.  
  
-   Exposer uniquement les <xref:System.IAsyncResult> de modèle lorsque vous avez une API existante qui utilise le <xref:System.IAsyncResult> modèle.  
  
-   Si vous avez une API existante basée sur le <xref:System.IAsyncResult> de modèle, vous pouvez également exposer le modèle basé sur les événements dans votre prochaine version.  
  
-   Exposez uniquement <xref:System.IAsyncResult> modèle si vous avez des exigences de hautes performances qui vous avez vérifié ne peuvent pas être satisfaite par le modèle basé sur des événements, mais il peut être remplie par la <xref:System.IAsyncResult> modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : implémenter un composant qui prend en charge le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Programmation multithread avec le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Implémentation du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
