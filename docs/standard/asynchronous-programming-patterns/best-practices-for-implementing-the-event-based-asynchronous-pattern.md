---
title: "Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements"
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
ms.assetid: 4acd2094-4f46-4eff-9190-92d0d9ff47db
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6a98c6854bc935eb8b319bd8a26dba8f12380ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements
Le modèle asynchrone basé sur les événements vous permet d’exposer efficacement un comportement asynchrone dans les classes, en utilisant une sémantique d’événement et de délégué familière. Pour implémenter le modèle asynchrone basé sur les événements, vous devez respecter certaines contraintes liées au comportement. Les sections ci-après décrivent les exigences et les recommandations que vous devez prendre en compte quand vous implémentez une classe qui suit le modèle asynchrone basé sur les événements.  
  
 Pour une présentation, consultez [Implémentation du modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="required-behavioral-guarantees"></a>Garanties de comportement obligatoires  
 Si vous implémentez le modèle asynchrone basé sur les événements, vous devez fournir une série de garanties pour que votre classe se comporte correctement et que les clients de votre classe puissent s'appuyer sur ce comportement.  
  
### <a name="completion"></a>Achèvement  
 Appelez toujours le gestionnaire d’événements *nom_méthode*`Completed` quand l’opération s’est terminée correctement, ou bien en cas d’erreur ou d’annulation. Les applications ne doivent jamais rencontrer de situation dans laquelle elles demeurent inactives sans jamais terminer l'opération en cours. Une exception à cette règle est la situation dans laquelle l'opération asynchrone elle-même est conçue de manière à ne jamais se terminer.  
  
### <a name="completed-event-and-eventargs"></a>Événement Completed et classe EventArgs  
 Pour chaque méthode *nom_méthode*`Async` distincte, appliquez les contraintes de conception suivantes :  
  
-   Définissez un événement *nom_méthode*`Completed` sur la même classe que la méthode.  
  
-   Définissez une classe <xref:System.EventArgs> et le délégué associé pour l’événement *nom_méthode*`Completed` qui dérive de la classe <xref:System.ComponentModel.AsyncCompletedEventArgs>. Le nom de classe par défaut doit être de la forme *nom_méthode*`CompletedEventArgs`.  
  
-   Vérifiez que la classe <xref:System.EventArgs> est spécifique des valeurs de retour de la méthode *nom_méthode*. Quand vous utilisez la classe <xref:System.EventArgs>, vous ne devez jamais obliger les développeurs à effectuer un transtypage du résultat.  
  
     L'exemple de code suivant montre une bonne implémentation de cette contrainte de conception, suivie d'une mauvaise.  
  
```csharp  
// Good design  
private void Form1_MethodNameCompleted(object sender, xxxCompletedEventArgs e)   
{   
    DemoType result = e.Result;  
}  
  
// Bad design  
private void Form1_MethodNameCompleted(object sender, MethodNameCompletedEventArgs e)   
{   
    DemoType result = (DemoType)(e.Result);  
}  
```  
  
-   Ne définissez pas de classe <xref:System.EventArgs> pour les méthodes de retour qui retournent `void`. À la place, utilisez une instance de la classe <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
-   Veillez à toujours déclencher l’événement *nom_méthode*`Completed`. Cet événement doit être déclenché quand l'opération s'est terminée correctement, ou bien en cas d'erreur ou d'annulation. Les applications ne doivent jamais rencontrer de situation dans laquelle elles demeurent inactives sans jamais terminer l'opération en cours.  
  
-   Veillez à intercepter toutes les exceptions qui se produisent au cours de l'opération asynchrone et à affecter l'exception interceptée à la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
-   Si une erreur se produit pendant l'exécution de la tâche, les résultats doivent être inaccessibles. Quand la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> n'a pas pour valeur `null`, assurez-vous que l'accès à toute propriété dans la structure <xref:System.EventArgs> lève une exception. Utilisez la méthode <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> pour effectuer cette vérification.  
  
-   Modélisez un délai au terme duquel une erreur se produit. Quand un délai arrive à expiration, déclenchez l’événement *nom_méthode*`Completed` et affectez une <xref:System.TimeoutException> à la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>.  
  
-   Si votre classe prend en charge plusieurs appels simultanés, vérifiez que l’événement *nom_méthode*`Completed` contient l’objet `userSuppliedState` approprié.  
  
-   Vérifiez que l’événement *nom_méthode*`Completed` est déclenché sur le thread approprié et au moment adéquat pendant le cycle de vie de l’application. Pour plus d'informations, voir la section Thread et contextes.  
  
### <a name="simultaneously-executing-operations"></a>Exécution d'opérations simultanément  
  
-   Si votre classe prend en charge plusieurs appels simultanés, autorisez le développeur à effectuer le suivi de chaque appel séparément en définissant la surcharge de *nom_méthode*`Async` qui prend un paramètre d’état à valeur d’objet, ou un ID de tâche, appelé `userSuppliedState`. Ce paramètre doit toujours être le dernier paramètre de la signature de la méthode *nom_méthode*`Async`.  
  
-   Si votre classe définit la surcharge de *nom_méthode*`Async` qui accepte un paramètre d’état à valeur d’objet, ou un ID de tâche, veillez à effectuer le suivi de la durée de vie de l’opération avec cet ID de tâche, et à le fournir en retour au gestionnaire d’achèvement. Vous pouvez vous aider de classes d'assistance. Pour plus d’informations sur la gestion de l’accès concurrentiel, voir [Procédure pas à pas : implémentation d’un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
-   Si votre classe définit la méthode *nom_méthode*`Async` sans le paramètre d’état et qu’elle ne prend pas en charge plusieurs appels simultanés, vérifiez que toute tentative d’appel de *nom_méthode*`Async` avant que soit achevé l’appel précédent de *nom_méthode*`Async` lève une <xref:System.InvalidOperationException>.  
  
-   D’une façon générale, ne levez pas d’exception si la méthode *nom_méthode*`Async` sans le paramètre `userSuppliedState` est appelée plusieurs fois et que plusieurs opérations se trouvent ainsi en attente. Vous pouvez lever une exception quand votre classe ne peut pas explicitement gérer cette situation, mais partez du principe que les développeurs peuvent gérer ces différents rappels impossibles à distinguer.  
  
### <a name="accessing-results"></a>Accès aux résultats  
  
-   Si une erreur se produit pendant l'exécution de l'opération asynchrone, les résultats doivent être inaccessibles. Assurez-vous que l'accès à toute propriété dans la classe <xref:System.ComponentModel.AsyncCompletedEventArgs> quand <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> n'a pas pour valeur `null` lève l'exception référencée par <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>. À cette fin, la classe <xref:System.ComponentModel.AsyncCompletedEventArgs> fournit la méthode <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A>.  
  
-   Assurez-vous que toute tentative d'accéder au résultat lève une exception <xref:System.InvalidOperationException> signalant que l'opération a été annulée. Utilisez la méthode <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> pour effectuer cette vérification.  
  
### <a name="progress-reporting"></a>Rapport de progression  
  
-   Dans la mesure du possible, prenez en charge le rapport de progression. Cela permet aux développeurs de fournir une meilleure expérience utilisateur d'application quand ils utilisent votre classe.  
  
-   Si vous implémentez un événement `ProgressChanged`/*nom_méthode*`ProgressChanged`, vérifiez qu’aucun événement de ce type n’est déclenché pour une opération asynchrone particulière après que l’événement *nom_méthode*`Completed` de cette opération a été déclenché.  
  
-   Si la classe <xref:System.ComponentModel.ProgressChangedEventArgs> standard est remplie, assurez-vous que la propriété <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> peut toujours être interprétée en tant que pourcentage. La valeur de pourcentage n'a pas besoin d'être précise, mais elle doit représenter un pourcentage. Si la mesure du rapport de progression doit être autre chose qu'un pourcentage, dérivez une classe de la classe <xref:System.ComponentModel.ProgressChangedEventArgs> et laissez <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> défini sur 0. Évitez d'utiliser une mesure d'indication autre qu'un pourcentage.  
  
-   Assurez-vous que l'événement `ProgressChanged` est déclenché sur le thread approprié et au moment adéquat pendant le cycle de vie de l'application. Pour plus d'informations, voir la section Thread et contextes.  
  
### <a name="isbusy-implementation"></a>Implémentation d'IsBusy  
  
-   N'exposez pas de propriété `IsBusy` si votre classe prend en charge plusieurs appels simultanés. Par exemple, les proxys de service web XML n'exposent pas de propriété `IsBusy`, car ils prennent en charge plusieurs appels simultanés de méthodes asynchrones.  
  
-   La propriété `IsBusy` doit retourner `true` une fois que la méthode *nom_méthode*`Async` a été appelée et avant que l’événement *nom_méthode*`Completed` n’ait été déclenché. Sinon elle doit retourner `false`. Les composants <xref:System.ComponentModel.BackgroundWorker> et <xref:System.Net.WebClient> sont des exemples de classes qui exposent une propriété `IsBusy`.  
  
### <a name="cancellation"></a>Annulation  
  
-   Dans la mesure du possible, prenez en charge l'annulation. Cela permet aux développeurs de fournir une meilleure expérience utilisateur d'application quand ils utilisent votre classe.  
  
-   Dans le cas de l'annulation, définissez l'indicateur <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> dans l'objet <xref:System.ComponentModel.AsyncCompletedEventArgs>.  
  
-   Assurez-vous que toute tentative d'accéder au résultat lève une exception <xref:System.InvalidOperationException> signalant que l'opération a été annulée. Utilisez la méthode <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> pour effectuer cette vérification.  
  
-   Assurez-vous que les appels d'une méthode d'annulation réussissent toujours et qu'ils ne déclenchent jamais d'exception. En général, un client n'est pas informé qu'il peut ou non annuler une opération à tout moment, ni qu'une annulation précédemment émise a effectivement réussi. Toutefois, l'application est toujours avertie qu'une annulation a réussi, car elle est impliquée dans la gestion de l'état d'achèvement.  
  
-   Déclenchez l’événement *nom_méthode*`Completed` quand l’opération est annulée.  
  
### <a name="errors-and-exceptions"></a>Erreurs et exceptions  
  
-   Interceptez toute exception qui se produit pendant l'opération asynchrone et définissez la valeur de la propriété <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> sur cette exception.  
  
### <a name="threading-and-contexts"></a>Thread et contextes  
 Pour que votre classe fonctionne correctement, il est primordial que les gestionnaires d'événements du client soient appelés sur le thread ou contexte adéquat en fonction du modèle d'application, notamment en ce qui concerne les applications Windows Forms et [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Deux classes d'assistance importantes vous permettent de vous assurer que votre classe asynchrone se comporte correctement dans le cadre de n'importe quel modèle d'application : <xref:System.ComponentModel.AsyncOperation> et <xref:System.ComponentModel.AsyncOperationManager>.  
  
 <xref:System.ComponentModel.AsyncOperationManager> fournit une méthode, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>, qui retourne un objet <xref:System.ComponentModel.AsyncOperation>. Votre méthode *nom_méthode*`Async` appelle <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> et votre classe utilise l’objet <xref:System.ComponentModel.AsyncOperation> retourné pour effectuer le suivi de la durée de vie de la tâche asynchrone.  
  
 Pour indiquer la progression, les résultats incrémentiels et l'achèvement au client, appelez les méthodes <xref:System.ComponentModel.AsyncOperation.Post%2A> et <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> sur la classe <xref:System.ComponentModel.AsyncOperation>. <xref:System.ComponentModel.AsyncOperation> prend en charge le marshaling des appels des gestionnaires d'événements du client en thread ou contexte adéquat.  
  
> [!NOTE]
>  Vous pouvez contourner ces règles si vous souhaitez explicitement aller à l'encontre de la stratégie du modèle d'application, tout en tirant parti des autres avantages de l'utilisation du modèle asynchrone basé sur les événements. Par exemple, vous pouvez souhaiter qu'une classe fonctionnant dans Windows Forms soit libre de threads. Vous pouvez créer une classe libre de threads, sous réserve que les développeurs comprennent les restrictions que cela implique. Les applications console ne synchronisent pas l'exécution des appels <xref:System.ComponentModel.AsyncOperation.Post%2A>. Cela peut entraîner le déclenchement d'événements `ProgressChanged` dans le désordre. Si vous souhaitez que l'exécution des appels <xref:System.ComponentModel.AsyncOperation.Post%2A> soit sérialisée, implémentez et installez une classe <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType>.  
  
 Pour plus d’informations sur l’utilisation de <xref:System.ComponentModel.AsyncOperation> et <xref:System.ComponentModel.AsyncOperationManager> pour activer vos opérations asynchrones, consultez [procédure pas à pas : implémentation d’un composant qui prend en charge le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="guidelines"></a>Recommandations  
  
-   Dans l'idéal, chaque appel de méthode doit être indépendant des autres appels. Vous devez éviter d'associer des appels qui partagent des ressources. Si des ressources doivent être partagées par des appels, vous devez prévoir un mécanisme de synchronisation approprié dans votre implémentation.  
  
-   Les conceptions qui obligent le client à implémenter une synchronisation sont déconseillées. Par exemple, dans le cas d'une méthode asynchrone qui reçoit un objet statique global comme paramètre, plusieurs appels simultanés de ce type de méthode peuvent entraîner une altération des données ou des interblocages.  
  
-   Si vous implémentez une méthode avec la surcharge de plusieurs appels (`userState` dans la signature), votre classe doit gérer une collection d'états utilisateur, ou d'ID de tâche, ainsi que leurs opérations en attente correspondantes. Cette collection doit être protégée avec des régions `lock`, car les différents appels ajoutent et suppriment des objets `userState` dans la collection.  
  
-   Pensez à réutiliser les classes `CompletedEventArgs` si cela est possible et approprié. Dans ce cas, l'affectation des noms n'est pas cohérente avec le nom de la méthode, car un délégué et un type <xref:System.EventArgs> donnés ne sont pas liés à une même méthode. Toutefois, évitez absolument que les développeurs soit obligés d'effectuer un transtypage de la valeur récupérée d'une propriété sur la classe <xref:System.EventArgs>.  
  
-   Si vous créez une classe qui dérive de <xref:System.ComponentModel.Component>, n'implémentez pas et n'installez pas votre propre classe <xref:System.Threading.SynchronizationContext>. Ce sont les modèles d'application, pas les composants, qui contrôlent la classe <xref:System.Threading.SynchronizationContext> utilisée.  
  
-   Quand vous utilisez un type quelconque de multithreading, vous vous exposez potentiellement à des bogues sérieux et complexes. Consultez les [Meilleures pratiques pour le threading managé](../../../docs/standard/threading/managed-threading-best-practices.md) avant d'implémenter une solution qui utilise le multithreading.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Implémentation du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Programmation multithread avec le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Choix du moment auquel implémenter le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Guide pratique : utiliser des composants qui prennent en charge le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Procédure pas à pas : implémenter un composant qui prend en charge le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
