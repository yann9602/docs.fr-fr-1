---
title: "Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern | Microsoft Docs"
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
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern
Si vous écrivez une classe avec certaines opérations pouvant entraîner d'importants retards, prévoyez de lui affecter des fonctionnalités asynchrones en implémentant [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Cette procédure pas à pas illustre comment créer un composant qui implémente le modèle asynchrone basé sur des événements.  Il est implémenté à l'aide des classes d'assistance de l'espace de noms <xref:System.ComponentModel?displayProperty=fullName>, ce qui garantit que le composant fonctionne correctement sous tous les modèles d'application, notamment [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], les applications console et les applications Windows Forms.  Ce composant est également concevable avec un contrôle <xref:System.Windows.Forms.PropertyGrid> et vos propres concepteurs personnalisés.  
  
 Lorsque vous avez terminé, une application calcule des nombres premiers de manière asynchrone.  Votre application possède un thread d'interface utilisateur principal et un thread pour chaque calcul de nombre premier.  Bien que le fait de tester si un nombre élevé est un nombre premier puisse prendre beaucoup de temps, le thread d'interface utilisateur principal n'est pas interrompu par ce délai et le formulaire est réactif pendant les calculs.  Vous pouvez exécuter simultanément autant de calculs que vous le souhaitez et annuler des calculs en attente de manière sélective.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création du composant  
  
-   Définition des événements asynchrones et des délégués publics  
  
-   Définition des délégués privés  
  
-   Implémentation des événements publics  
  
-   Implémentation de la méthode d'achèvement  
  
-   Implémentation des méthodes de travail  
  
-   Implémentation des méthodes Start et Cancel  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## Création du composant  
 La première étape consiste à créer le composant qui implémentera le modèle asynchrone basé sur des événements.  
  
#### Pour créer le composant  
  
-   Créez une classe appelée `PrimeNumberCalculator` qui hérite de <xref:System.ComponentModel.Component>.  
  
## Définition des événements asynchrones et des délégués publics  
 Votre composant communique avec les clients à l'aide des événements.  L'événement *MethodName*`Completed` avertit les clients de l'achèvement d'une tâche asynchrone, et l'événement *MethodName*`ProgressChanged` informe les clients de la progression d'une tâche asynchrone.  
  
#### Pour définir des événements asynchrones pour les clients de votre composant :  
  
1.  Importez les espaces de noms <xref:System.Threading?displayProperty=fullName> et <xref:System.Collections.Specialized?displayProperty=fullName> au début de votre fichier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Avant la définition de la classe  `PrimeNumberCalculator` , déclarez des délégués pour les événements de progression et d'achèvement.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  Dans la définition de la classe  `PrimeNumberCalculator` , déclarez les événements destinés à signaler la progression et l'achèvement aux clients.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Après la définition de la classe  `PrimeNumberCalculator` , dérivez la classe  `CalculatePrimeCompletedEventArgs`  pour signaler le résultat de chaque calcul au gestionnaire d'événements du client pour l'événement `CalculatePrimeCompleted`.  En plus des propriétés `AsyncCompletedEventArgs`, cette classe permet au client de déterminer le nombre qui a été testé, s'il s'agit d'un nombre premier, et le premier diviseur s'il ne s'agit pas d'un nombre premier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## Point de contrôle  
 À présent, vous pouvez générer le composant.  
  
#### Pour tester votre composant :  
  
-   Compilez le composant.  
  
     Vous recevez deux avertissements du compilateur :  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Ces avertissements seront effacés dans la section suivante.  
  
## Définition des délégués privés  
 Les aspects asynchrones du composant  `PrimeNumberCalculator`  sont implémentés en interne avec un délégué spécial appelé <xref:System.Threading.SendOrPostCallback>.  <xref:System.Threading.SendOrPostCallback> représente une méthode de rappel qui s'exécute sur un thread <xref:System.Threading.ThreadPool>.  La méthode de rappel doit avoir une signature qui accepte un seul paramètre de type <xref:System.Object>, ce qui signifie que vous devrez passer l'état aux délégués dans une classe wrapper.  Pour plus d'informations, consultez <xref:System.Threading.SendOrPostCallback>.  
  
#### Pour implémenter le comportement asynchrone interne de votre composant :  
  
1.  Déclarez et créez les délégués <xref:System.Threading.SendOrPostCallback> dans la classe  `PrimeNumberCalculator` .  Créez les objets <xref:System.Threading.SendOrPostCallback> dans une méthode utilitaire appelée  `InitializeDelegates`.  
  
     Vous aurez besoin de deux délégués : un pour signaler la progression au client, et un pour signaler l'achèvement au client.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Appelez la méthode `InitializeDelegates` dans le constructeur de votre composant.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Déclarez un délégué dans la classe `PrimeNumberCalculator` qui gère de manière asynchrone le travail effectif à réaliser.  Ce délégué encapsule la méthode de travail qui teste si un nombre est un nombre premier.  Le délégué accepte un paramètre <xref:System.ComponentModel.AsyncOperation> qui sera utilisé pour assurer le suivi de la durée de vie de l'opération asynchrone.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Créez une collection pour gérer les durées de vie d'opérations asynchrones en attente.  Le client a besoin d'une méthode de suivi des opérations au fur et à mesure qu'elles sont exécutées et achevées, et ce suivi est effectué en demandant au client de passer un jeton unique, ou un ID de tâche, lorsqu'il fait appel à la méthode asynchrone.  Le composant `PrimeNumberCalculator` doit conserver une trace de chaque appel en associant l'ID de tâche à l'appel correspondant.  Si le client passe un ID de tâche qui n'est pas unique, le composant `PrimeNumberCalculator` doit lever une exception.  
  
     Le composant `PrimeNumberCalculator` conserve une trace de l'ID de tâche en utilisant une classe de collection spéciale appelée <xref:System.Collections.Specialized.HybridDictionary>.  Dans la définition de classe, créez un <xref:System.Collections.Specialized.HybridDictionary> appelé  `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## Implémentation des événements publics  
 Les composants qui implémentent le modèle asynchrone basé sur des événements communiquent avec les clients à l'aide d'événements.  Ces événements sont appelés sur le thread approprié à l'aide de la classe <xref:System.ComponentModel.AsyncOperation>.  
  
#### Pour déclencher des événements aux clients de votre composant :  
  
1.  Implémentez des événements publics pour le signalement aux clients.  Vous aurez besoin d'un événement pour signaler la progression et d'un autre pour signaler l'achèvement.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## Implémentation de la méthode d'achèvement  
 Le délégué d'achèvement est la méthode que le comportement asynchrone libre de threads sous\-jacent appelle lorsque l'opération asynchrone se termine par un achèvement correct, une erreur ou une annulation.  Cet appel a lieu sur un thread arbitraire.  
  
 Cette méthode correspond à la suppression de l'ID de tâche du client dans la collection interne de jetons de clients uniques.  Cette méthode met également fin à la durée de vie d'une opération asynchrone particulière en appelant la méthode <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> sur le <xref:System.ComponentModel.AsyncOperation> correspondant.  Cet appel déclenche l'événement d'achèvement sur le thread approprié au modèle d'application.  Une fois la méthode <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> appelée, cette instance de <xref:System.ComponentModel.AsyncOperation> ne peut plus être utilisée et toute tentative ultérieure visant à l'utiliser lèvera une exception.  
  
 La signature `CompletionMethod` doit contenir tout l'état nécessaire pour décrire le résultat de l'opération asynchrone.  Il contient l'état pour le nombre qui a été testé par cette opération asynchrone particulière, sait si le nombre est un nombre premier et contient la valeur de son premier diviseur s'il ne s'agit pas d'un nombre premier.  Elle contient également l'état décrivant toute exception levée et le <xref:System.ComponentModel.AsyncOperation> correspondant à cette tâche particulière.  
  
#### Pour terminer une opération asynchrone :  
  
-   Implémentez la méthode d'achèvement.  Elle accepte six paramètres qu'elle utilise pour remplir  `CalculatePrimeCompletedEventArgs` qui est retourné au client via le  `CalculatePrimeCompletedEventHandler` du client.  Elle supprime le jeton d'ID de tâche du client de la collection interne et met fin à la durée de vie de l'opération asynchrone en appelant <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>.  <xref:System.ComponentModel.AsyncOperation> marshale l'appel au thread ou au contexte approprié au modèle d'application.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## Point de contrôle  
 À présent, vous pouvez générer le composant.  
  
#### Pour tester votre composant :  
  
-   Compilez le composant.  
  
     Vous recevrez un avertissement du compilateur :  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Cet avertissement sera résolu dans la section suivante.  
  
## Implémentation des méthodes de travail  
 Jusqu'à présent, vous avez implémenté le code asynchrone de prise en charge pour le composant `PrimeNumberCalculator`.  Maintenant, vous pouvez implémenter le code qui procède au travail effectif.  Vous implémenterez trois méthodes : `CalculateWorker`,  `BuildPrimeNumberList` et `IsPrime`.  Ensemble, `BuildPrimeNumberList` et `IsPrime` composent un algorithme connu appelé crible d'Ératosthène qui détermine si un nombre est un nombre premier en recherchant tous les nombres premiers jusqu'à la racine carrée du nombre test.  Si aucun diviseur n'est trouvé à ce stade, le nombre test est un nombre premier.  
  
 Si ce composant était conçu pour une efficacité maximale, il rappellerait tous les nombres premiers découverts par divers appels pour différents nombres test.  Il rechercherait également des diviseurs simples tels 2, 3 et 5.  Cet exemple sert à montrer comment les opérations prenant du temps peuvent être exécutées de façon asynchrone, ces optimisations sont données à titre d'exercice.  
  
 La méthode `CalculateWorker` est encapsulée dans un délégué et est appelée de manière asynchrone avec un appel à `BeginInvoke`.  
  
> [!NOTE]
>  Le rapport de progression est implémenté dans la méthode `BuildPrimeNumberList`.  Sur les ordinateurs rapides, les événements `ProgressChanged` peuvent être déclenchés à intervalles courts.  Le thread client sur lequel ces événements sont déclenchés doit être capable de gérer cette situation.  Le code de l'interface utilisateur peut être submergé de messages et incapable d'y faire face, ce qui provoque un blocage.  Pour obtenir un exemple d'interface utilisateur gérant cette situation, consultez [How to: Implement a Client of the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### Pour exécuter le calcul de nombre premier de manière asynchrone :  
  
1.  Implémentez la méthode utilitaire `TaskCanceled`.  Elle vérifie la collection de durées de vie de la tâche pour l'ID de tâche donné et retourne la valeur `true` si l'ID de tâche est introuvable.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Implémentez la méthode `CalculateWorker`.  Elle accepte deux paramètres : un nombre à tester et une <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Implémentez `BuildPrimeNumberList`.  Elle accepte deux paramètres : le nombre à tester et une <xref:System.ComponentModel.AsyncOperation>.  Elle utilise <xref:System.ComponentModel.AsyncOperation> pour signaler la progression et les résultats incrémentiels.  Cela garantit que les gestionnaires d'événements du client sont appelés sur le thread ou le contexte approprié pour le modèle d'application.  Lorsque `BuildPrimeNumberList` trouve un nombre premier, celui\-ci est signalé comme un résultat incrémentiel au gestionnaire d'événements du client pour l'événement `ProgressChanged`.  Une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>, appelée `CalculatePrimeProgressChangedEventArgs`, à laquelle une propriété appelée `LatestPrimeNumber` est ajoutée, est nécessaire.  
  
     La méthode `BuildPrimeNumberList` appelle aussi périodiquement la méthode `TaskCanceled` et s'arrête si la méthode retourne la valeur `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Implémentez `IsPrime`.  Elle accepte trois paramètres : une liste de nombres premiers connus, le nombre à tester et un paramètre de sortie pour le premier diviseur trouvé.  Selon la liste de nombres premiers, elle détermine si le nombre test est un nombre premier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Dérivez `CalculatePrimeProgressChangedEventArgs` de <xref:System.ComponentModel.ProgressChangedEventArgs>.  Cette classe est nécessaire pour signaler des résultats incrémentiels au gestionnaire d'événements du client pour l'événement `ProgressChanged`.  Elle possède une propriété ajoutée appelée `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## Point de contrôle  
 À présent, vous pouvez générer le composant.  
  
#### Pour tester votre composant :  
  
-   Compilez le composant.  
  
     Il reste alors à écrire les méthodes permettant de démarrer et d'annuler des opérations asynchrones, à savoir `CalculatePrimeAsync` et `CancelAsync`.  
  
## Implémentation des méthodes Start et Cancel  
 Vous démarrez la méthode de travail sur son propre thread en appelant `BeginInvoke` sur le délégué qui l'encapsule.  Pour gérer la durée de vie d'une opération asynchrone particulière, vous appelez la méthode <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> sur la classe d'assistance <xref:System.ComponentModel.AsyncOperationManager>.  Elle retourne une <xref:System.ComponentModel.AsyncOperation> qui marshale les appels sur les gestionnaires d'événements du client au thread ou au contexte approprié.  
  
 Vous annulez une opération en attente particulière en appelant <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> sur son <xref:System.ComponentModel.AsyncOperation> correspondante.  Cela met fin à cette opération et tous les appels ultérieurs à son <xref:System.ComponentModel.AsyncOperation> lèveront une exception.  
  
#### Pour implémenter les fonctionnalités Start et Cancel :  
  
1.  Implémentez la méthode `CalculatePrimeAsync`.  Assurez\-vous que le jeton \(ID de tâche\) fourni par le client est unique parmi tous les jetons représentant les tâches en attente.  Si le client passe un jeton qui n'est pas unique, `CalculatePrimeAsync` lève une exception.  Sinon, le jeton est ajouté à la collection d'ID de tâche.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Implémentez la méthode `CancelAsync`.  Si le paramètre `taskId` existe dans la collection de jetons, il est supprimé.  Cela empêche l'exécution des tâches annulées qui n'ont pas démarré.  Si la tâche est en cours d'exécution, la méthode `BuildPrimeNumberList` s'arrête lorsqu'elle détecte que l'ID de tâche a été supprimé de la collection de durées de vie.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## Point de contrôle  
 À présent, vous pouvez générer le composant.  
  
#### Pour tester votre composant :  
  
-   Compilez le composant.  
  
 Le composant  `PrimeNumberCalculator`  est maintenant terminé et prêt à être utilisé.  
  
 Pour obtenir un exemple de client qui utilise le composant `PrimeNumberCalculator`, consultez [How to: Implement a Client of the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## Étapes suivantes  
 Vous pouvez remplir cet exemple en écrivant `CalculatePrime`, l'équivalent synchrone de la méthode `CalculatePrimeAsync`.  Le composant `PrimeNumberCalculator` devient alors totalement conforme au modèle asynchrone basé sur des événements.  
  
 Vous pouvez améliorer cet exemple en conservant la liste de tous les nombres premiers découverts par divers appels pour différents nombres test.  En utilisant cette approche, chaque tâche bénéficiera du travail effectué par les tâches précédentes.  Veillez à protéger cette liste par des zones `lock` afin que l'accès à la liste par différents threads soit sérialisé.  
  
 Vous pouvez également améliorer cet exemple en testant les diviseurs triviaux tels que 2, 3 et 5.  
  
## Voir aussi  
 [Comment : exécuter une opération en arrière\-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)   
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/fr-fr/c731a50c-09c1-4468-9646-54c86b75d269)   
 [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)