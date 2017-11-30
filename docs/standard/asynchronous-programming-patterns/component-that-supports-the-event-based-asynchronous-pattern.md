---
title: "Procédure pas à pas : implémentation d’un composant qui prend en charge le modèle asynchrone basé sur des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150e4b27cc149774895574ddd196de5f9bc2acd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Procédure pas à pas : implémentation d’un composant qui prend en charge le modèle asynchrone basé sur des événements
Si vous écrivez une classe avec certaines opérations pouvant entraîner d’importants retards, pensez à lui affecter des fonctionnalités asynchrones en implémentant la [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Cette procédure pas à pas montre comment créer un composant qui implémente le modèle asynchrone basé sur des événements. Il est implémenté à l’aide des classes d’assistance de la <xref:System.ComponentModel?displayProperty=nameWithType> espace de noms, ce qui garantit que le composant fonctionne correctement sous tout modèle d’application, y compris les [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], les applications Windows Forms et les applications de la Console. Ce composant est également possible avec un <xref:System.Windows.Forms.PropertyGrid> contrôle et vos propres concepteurs personnalisés.  
  
 Lorsque vous avez terminé, vous disposerez d’une application qui calcule les nombres premiers de manière asynchrone. Votre application aura un thread d’interface utilisateur principal d’utilisateur et un thread pour chaque calcul de nombres premiers. Bien que les tests si un grand nombre est prime peut prendre un certain temps, le thread d’interface utilisateur ne sera pas interrompue par ce délai et le formulaire est réactif pendant les calculs. Vous serez en mesure d’exécuter comme beaucoup de calculs que vous le souhaitez simultanément et de manière sélective annulation des calculs.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création du composant  
  
-   Définition des délégués et événements asynchrones publics  
  
-   Définition des délégués privés  
  
-   Implémentation des événements publics  
  
-   Implémentation de la méthode de saisie semi-automatique  
  
-   Implémentation des méthodes de travail  
  
-   Implémentation des méthodes Start et Cancel  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Création du composant  
 La première étape consiste à créer le composant qui implémente le modèle asynchrone basé sur des événements.  
  
#### <a name="to-create-the-component"></a>Pour créer le composant  
  
-   Créez une classe appelée `PrimeNumberCalculator` qui hérite de <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Définition des délégués et événements asynchrones publics  
 Votre composant communique avec les clients à l’aide d’événements. Le *MethodName* `Completed` événement avertit les clients de l’achèvement d’une tâche asynchrone et la *MethodName* `ProgressChanged` événements informant les clients de la progression d’une tâche asynchrone.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Pour définir des événements asynchrones pour les clients de votre composant :  
  
1.  Importer le <xref:System.Threading?displayProperty=nameWithType> et <xref:System.Collections.Specialized?displayProperty=nameWithType> espaces de noms en haut de votre fichier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Avant du `PrimeNumberCalculator` définition, de la classe déclarer des délégués pour les événements de progression et d’achèvement.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  Dans la `PrimeNumberCalculator` définition de classe, déclarez les événements pour signaler la progression et l’achèvement aux clients.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Après le `PrimeNumberCalculator` définition de classe, dérivez la `CalculatePrimeCompletedEventArgs` classe pour signaler le résultat de chaque calcul au gestionnaire d’événements du client pour le `CalculatePrimeCompleted`.event. Outre la `AsyncCompletedEventArgs` propriétés, cette classe permet au client déterminer le nombre qui a été testé, s’il est le premier et le premier diviseur Nouveautés si elle n’est pas principale.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade, vous pouvez générer le composant.  
  
#### <a name="to-test-your-component"></a>Pour tester votre composant  
  
-   Compilez le composant.  
  
     Vous recevez deux avertissements du compilateur :  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Ces avertissements seront effacés dans la section suivante.  
  
## <a name="defining-private-delegates"></a>Définition des délégués privés  
 Les aspects asynchrones de le `PrimeNumberCalculator` composant sont implémentés en interne avec un délégué spécial appelé un <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> représente une méthode de rappel qui s’exécute sur un <xref:System.Threading.ThreadPool> thread. La méthode de rappel doit avoir une signature qui accepte un seul paramètre de type <xref:System.Object>, ce qui signifie que vous devez passer l’état aux délégués dans une classe wrapper. Pour plus d'informations, consultez <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Pour implémenter le comportement d’asynchrone interne de votre composant :  
  
1.  Déclarez et créez le <xref:System.Threading.SendOrPostCallback> de délégués dans la `PrimeNumberCalculator` classe. Créer le <xref:System.Threading.SendOrPostCallback> objets dans une méthode utilitaire appellent `InitializeDelegates`.  
  
     Vous aurez besoin de deux délégués : un pour signaler la progression au client et un pour signaler l’achèvement au client.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Appelez le `InitializeDelegates` méthode dans le constructeur de votre composant.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Déclarez un délégué dans la `PrimeNumberCalculator` classe qui gère le travail à faire de façon asynchrone. Ce délégué encapsule la méthode de travail qui teste si un nombre est un nombre premier. Le délégué accepte un <xref:System.ComponentModel.AsyncOperation> paramètre, qui sera utilisé pour effectuer le suivi de la durée de vie de l’opération asynchrone.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Créer un regroupement pour la gestion des durées de vie des opérations asynchrones en attente. Le client a besoin d’un moyen pour effectuer le suivi des opérations comme elles sont exécutées et achevées, et ce suivi est effectué en demandant au client de passer un jeton unique, ou un ID de tâche, lorsque le client effectue l’appel à la méthode asynchrone. Le `PrimeNumberCalculator` composant doit effectuer le suivi de chaque appel en associant l’ID de tâche à l’appel correspondant. Si le client passe un ID de tâche qui n’est pas unique, le `PrimeNumberCalculator` composant doit lever une exception.  
  
     Le `PrimeNumberCalculator` composant effectue le suivi des ID de tâche à l’aide d’une classe de collection spéciale appelée un <xref:System.Collections.Specialized.HybridDictionary>. Dans la définition de classe, créez un <xref:System.Collections.Specialized.HybridDictionary> appelée `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implémentation des événements publics  
 Les composants qui implémentent le modèle asynchrone basé sur événement communiquent aux clients à l’aide d’événements. Ces événements sont appelés sur le thread approprié à l’aide de la <xref:System.ComponentModel.AsyncOperation> classe.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Pour déclencher des événements pour les clients de votre composant :  
  
1.  Implémenter des événements publics pour les clients de création de rapports. Vous devez un événement pour signaler la progression et l’autre pour signaler l’achèvement.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implémentation de la méthode de saisie semi-automatique  
 Le délégué d’achèvement est la méthode qui appelle le comportement asynchrone sous-jacente, libre de threads lorsque l’opération asynchrone se termine par la réussite, d’erreur ou d’annulation. Cet appel a lieu sur un thread arbitraire.  
  
 Cette méthode est où les ID de tâche du client est supprimé de la collection interne de jetons de clients uniques. Cette méthode termine également la durée de vie d’une opération asynchrone particulière en appelant le <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> méthode sur le correspondant <xref:System.ComponentModel.AsyncOperation>. Cet appel déclenche l’événement d’achèvement sur le thread qui est approprié pour le modèle d’application. Après le <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> méthode est appelée, cette instance de <xref:System.ComponentModel.AsyncOperation> ne peut plus être utilisé, et toute tentative ultérieure de l’utiliser lèvera une exception.  
  
 Le `CompletionMethod` signature doit contenir tout l’état nécessaire pour décrire le résultat de l’opération asynchrone. Il possède un état pour le nombre qui a été testé par cette opération asynchrone particulière, si le nombre est premier et la valeur de son premier diviseur si elle n’est pas un nombre premier. Il conserve également l’état décrivant toute exception qui s’est produite, et le <xref:System.ComponentModel.AsyncOperation> correspondant à cette tâche particulière.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>Pour effectuer une opération asynchrone :  
  
-   Implémentez la méthode d’exécution. Elle accepte six paramètres qu’elle utilise pour remplir un `CalculatePrimeCompletedEventArgs` qui est retournée au client par le biais du client `CalculatePrimeCompletedEventHandler`. Elle supprime le jeton d’ID tâche du client à partir de la collection interne et il met fin à la durée de vie de l’opération asynchrone avec un appel à <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. Le <xref:System.ComponentModel.AsyncOperation> marshale l’appel au thread ou contexte approprié pour le modèle d’application.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade, vous pouvez générer le composant.  
  
#### <a name="to-test-your-component"></a>Pour tester votre composant  
  
-   Compilez le composant.  
  
     Vous recevrez un avertissement du compilateur :  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Cet avertissement sera résolu dans la section suivante.  
  
## <a name="implementing-the-worker-methods"></a>Implémentation des méthodes de travail  
 Jusqu'à présent, vous avez implémenté le code asynchrone de prise en charge pour le `PrimeNumberCalculator` composant. Maintenant, vous pouvez implémenter le code qui effectue le travail. Vous allez implémenter trois méthodes : `CalculateWorker`, `BuildPrimeNumberList`, et `IsPrime`. Ensemble, `BuildPrimeNumberList` et `IsPrime` composent un algorithme connu appelé crible d’Ératosthène qui détermine si un nombre est un nombre premier en recherchant tous les nombres premiers jusqu'à la racine carrée du nombre test. Si aucun diviseur n’est trouvées à ce stade, le numéro de test est un nombre premier.  
  
 Si ce composant a été écrit pour une efficacité maximale, il serait n’oubliez pas de tous les nombres premiers découverts par divers appels pour différents nombres test. Il serait également vérifier diviseurs triviaux tels que 2, 3 et 5. L’objectif de cet exemple est d’illustrer les opérations longues comment peut être exécutée de façon asynchrone, toutefois, donc ces optimisations comme un exercice pour vous.  
  
 Le `CalculateWorker` méthode est encapsulée dans un délégué et est appelée de façon asynchrone avec un appel à `BeginInvoke`.  
  
> [!NOTE]
>  Rapport de progression est implémenté dans le `BuildPrimeNumberList` (méthode). Sur les ordinateurs rapides, `ProgressChanged` événements peuvent être déclenchés de suite. Le thread client sur lequel ces événements sont déclenchés, doit être en mesure de gérer cette situation. Code de l’interface utilisateur peut être submergé de messages et incapable de suivre, aboutissant à un blocage. Pour un exemple d’interface utilisateur qui gère cette situation, consultez [Comment : implémenter un Client du modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Pour exécuter de façon asynchrone le calcul de nombres premiers :  
  
1.  Implémentez la `TaskCanceled` méthode utilitaire. Elle vérifie la collection de durée de vie de tâche pour l’ID de tâche donné et retourne `true` si l’ID de tâche est introuvable.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Implémentez la méthode `CalculateWorker`. Elle accepte deux paramètres : un nombre à tester et qu’un <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Implémentez `BuildPrimeNumberList`. Elle accepte deux paramètres : le nombre à tester et un <xref:System.ComponentModel.AsyncOperation>. Elle utilise le <xref:System.ComponentModel.AsyncOperation> pour signaler la progression et des résultats incrémentiels. Cela garantit que les gestionnaires d’événements du client sont appelés sur le thread ou contexte approprié pour le modèle d’application. Lorsque `BuildPrimeNumberList` trouve un nombre premier, il est signalé comme un résultat incrémentiel au gestionnaire d’événements du client pour le `ProgressChanged` événement. Cela requiert une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>, appelé `CalculatePrimeProgressChangedEventArgs`, qui a une propriété appelée ajoutée `LatestPrimeNumber`.  
  
     Le `BuildPrimeNumberList` méthode appelle périodiquement la `TaskCanceled` (méthode) et s’arrête si la méthode retourne `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Implémentez `IsPrime`. Elle accepte trois paramètres : une liste de nombres premiers connus, le nombre à tester et un paramètre de sortie pour le premier diviseur trouvé. Étant donné la liste de nombres premiers, elle détermine si le nombre de tests est le premier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Dériver `CalculatePrimeProgressChangedEventArgs` de <xref:System.ComponentModel.ProgressChangedEventArgs>. Cette classe est nécessaire pour signaler des résultats incrémentiels au gestionnaire d’événements du client pour le `ProgressChanged` événement. Il possède une propriété ajoutée appelée `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade, vous pouvez générer le composant.  
  
#### <a name="to-test-your-component"></a>Pour tester votre composant  
  
-   Compilez le composant.  
  
     Il reste à écrire est les méthodes pour démarrer et d’annuler des opérations asynchrones, `CalculatePrimeAsync` et `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implémenter les méthodes Start et Cancel  
 Démarrage de la méthode de travail sur son propre thread en appelant `BeginInvoke` sur le délégué qui l’encapsule. Pour gérer la durée de vie d’une opération asynchrone particulière, vous appelez le <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> méthode sur la <xref:System.ComponentModel.AsyncOperationManager> classe d’assistance. Cette opération retourne un <xref:System.ComponentModel.AsyncOperation>, qui marshale les appels sur les gestionnaires d’événements du client pour le thread ou contexte adéquat.  
  
 Vous annulez une opération en attente de particulière en appelant <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> sur son <xref:System.ComponentModel.AsyncOperation>. Cela met fin à cette opération et tous les appels suivants à son <xref:System.ComponentModel.AsyncOperation> lève une exception.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>Pour implémenter le début et annuler des fonctionnalités :  
  
1.  Implémentez la méthode `CalculatePrimeAsync`. Assurez-vous que le jeton fourni par le client (ID de tâche) est unique parmi tous les jetons représentant actuellement en attente de tâches. Si le client passe un jeton non uniques, `CalculatePrimeAsync` lève une exception. Sinon, le jeton est ajouté à la collection d’ID de tâche.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Implémentez la méthode `CancelAsync`. Si le `taskId` paramètre existe dans la collection de jetons, il est supprimé. Cela empêche les tâches annulées qui n’ont pas démarré à partir de l’exécution. Si la tâche est en cours d’exécution, le `BuildPrimeNumberList` méthode se termine lorsqu’il détecte que l’ID de tâche a été supprimé de la collection de la durée de vie.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade, vous pouvez générer le composant.  
  
#### <a name="to-test-your-component"></a>Pour tester votre composant  
  
-   Compilez le composant.  
  
 Le `PrimeNumberCalculator` composant est maintenant terminé et prêt à être utilisé.  
  
 Pour un exemple de client qui utilise le `PrimeNumberCalculator` composant, consultez [Comment : implémenter un Client du modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous pouvez remplir cet exemple en écrivant `CalculatePrime`, l’équivalent synchrone de `CalculatePrimeAsync` (méthode). Cela facilitera la `PrimeNumberCalculator` entièrement compatible avec le modèle asynchrone basé sur des événements de composant.  
  
 Vous pouvez améliorer cet exemple en conservant la liste de tous les nombres premiers découverts par divers appels pour différents nombres test. À l’aide de cette approche, chaque tâche bénéficiera du travail effectué par les tâches précédentes. Veillez à protéger cette liste par `lock` régions, afin que l’accès à la liste par différents threads soit sérialisé.  
  
 Vous pouvez également améliorer cet exemple en testant les diviseurs triviaux tels que 2, 3 et 5.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Vue d’ensemble du modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NOT IN BUILD : Multithreading en Visual Basic](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Guide pratique pour implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Programmation multithread avec le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
