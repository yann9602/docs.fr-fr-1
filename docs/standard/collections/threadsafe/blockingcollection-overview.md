---
title: Vue d&quot;ensemble de BlockingCollection
description: Vue d&quot;ensemble de BlockingCollection
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a1a867de-53c2-49ca-9a1a-e5770a942724
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 64a01b5e21e012dfaae07a02f5fb27932be9cf98

---

# <a name="blockingcollection-overview"></a>Vue d'ensemble de BlockingCollection

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) est une classe de collection thread-safe qui fournit les fonctionnalités suivantes :

*   Implémentation du modèle producteur-consommateur.

*   Ajout et suppression thread-safe d’éléments dans une collection.

*   Capacité maximale facultative.

*   Opérations d’insertion et de suppression qui se bloquent quand la collection est vide ou complète.

*   Opérations « d’essai » d’insertion et de suppression qui ne se bloquent pas ou qui se bloquent pendant une période spécifiée.

*   Encapsule tout type de collection qui implémente [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1).

*   Annulation avec jetons d’annulation.

*   Deux sortes d’énumérations avec `foreach` : 

    1. Énumération en lecture seule.
    
    2. Énumération qui supprime des éléments à mesure qu’ils sont énumérés.
    
## <a name="bounding-and-blocking-support"></a>Prise en charge de la délimitation et du blocage 

[BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) prend en charge la délimitation et le blocage. La délimitation signifie que vous pouvez définir la capacité maximale de la collection. La délimitation est importante dans certains scénarios, car elle vous permet de contrôler la taille maximale de la collection en mémoire, et elle empêche les threads producteur de se déplacer trop loin avant les threads consommateur.

Plusieurs threads ou tâches peuvent ajouter simultanément des éléments à la collection, et si la collection atteint sa capacité maximale spécifiée, les threads producteur se bloquent jusqu’à ce qu’un élément soit supprimé. Plusieurs consommateurs peuvent supprimer des éléments simultanément, et si la collection devient vide, les threads consommateur se bloquent jusqu’à ce qu’un producteur ajoute un élément. Un thread producteur peut appeler `CompleteAdding` pour indiquer qu’aucun élément supplémentaire ne sera ajouté. Les consommateurs surveillent la propriété `IsCompleted` pour savoir quand la collection est vide et quand aucun autre élément ne sera ajouté. L’exemple suivant montre un `BlockingCollection` simple avec une capacité limitée de 100. Une tâche de producteur ajoute des éléments à la collection tant qu’une certaine condition externe est remplie, puis appelle `CompleteAdding`. La tâche du consommateur prend des éléments jusqu’à ce que la propriété `IsCompleted` ait la valeur true.

```csharp
// A bounded collection. It can hold no more 
// than 100 items at once.
BlockingCollection<Data> dataItems = new BlockingCollection<Data>(100);


// A simple blocking consumer with no cancellation.
Task.Run(() => 
{
    while (!dataItems.IsCompleted)
    {

        Data data = null;
        // Blocks if number.Count == 0
        // IOE means that Take() was called on a completed collection.
        // Some other thread can call CompleteAdding after we pass the
        // IsCompleted check but before we call Take. 
        // In this example, we can simply catch the exception since the 
        // loop will break on the next iteration.
        try
        {
            data = dataItems.Take();
        }
        catch (InvalidOperationException) { }

        if (data != null)
        {
            Process(data);
        }
    }
    Console.WriteLine("\r\nNo more items to take.");
});

// A simple blocking producer with no cancellation.
Task.Run(() =>
{
    while (moreItemsToAdd)
    {
        Data data = GetData();
        // Blocks if numbers.Count == dataItems.BoundedCapacity
        dataItems.Add(data);
    }
    // Let consumer know we are done.
    dataItems.CompleteAdding();
});
```

Pour obtenir un exemple complet, consultez [Guide pratique : ajouter et prendre des éléments individuellement dans un BlockingCollection](how-to-add-and-take-items.md).

## <a name="timed-blocking-operations"></a>Opérations de blocage temporisé

Dans les opérations `TryAdd` et `TryTake` de blocage temporisé sur les collections limitées, la méthode tente d’ajouter ou de prendre un élément. Si un élément est disponible, il est placé dans la variable qui a été passée par référence, et la méthode retourne la valeur `true`. Si aucun élément n’est récupéré après un délai d’attente spécifié, la méthode retourne la valeur `false`. Le thread est ensuite libre d’effectuer un autre travail utile avant de réessayer d’accéder à la collection. Pour obtenir un exemple d’accès à blocage temporisé, consultez le deuxième exemple de la rubrique [Guide pratique : ajouter et prendre des éléments individuellement dans un BlockingCollection](how-to-add-and-take-items.md).

## <a name="cancelling-add-and-take-operations"></a>Annulation d’opérations Add et Take

Les opérations Add et Take sont généralement effectuées dans une boucle. Vous pouvez annuler une boucle en passant un `CancellationToken` à la méthode `TryAdd` ou `TryTake`, puis en vérifiant la valeur de la propriété `IsCancellationRequested` du jeton à chaque itération. Si la valeur est `true`, vous pouvez, si vous le souhaitez, répondre à la demande d’annulation en nettoyant toutes les ressources et en quittant la boucle. L’exemple suivant montre une surcharge de `TryAdd` qui prend un jeton d’annulation, ainsi que le code qui l’utilise :

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="specifying-the-collection-type"></a>Spécification du type de collection

Quand vous créez un `BlockingCollection<T>;`, vous pouvez spécifier non seulement la capacité limitée, mais aussi le type de collection à utiliser. Par exemple, vous pouvez spécifier un [ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) pour un comportement premier entré, premier sorti (FIFO, First In-First Out), ou un [ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) pour un comportement dernier entré, premier sorti (LIFO, Last In-First Out). Vous pouvez utiliser n’importe quelle classe de collection qui implémente l’interface [IProducerConsumerCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.IProducerConsumerCollection-1). Le type de collection par défaut pour `BlockingCollection<T>` est `ConcurrentQueue<T>`. L’exemple de code suivant montre comment créer un `BlockingCollection<T>` de chaînes qui possède une capacité de 1 000 et qui utilise un [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) :

```csharp
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );
```

## <a name="ienumerable-support"></a>Prise en charge d’IEnumerable

`BlockingCollection<T>` fournit une méthode `GetConsumingEnumerable` qui permet aux consommateurs d’utiliser une instruction `foreach` pour supprimer des éléments jusqu’à ce que la collection soit terminée, ce qui signifie qu’elle est vide et qu’aucun autre élément ne sera plus ajouté. Pour plus d’informations, consultez [Guide pratique : utiliser la boucle ForEach pour supprimer les éléments d’un BlockingCollection](how-to-use-foreach-to-remove.md).

## <a name="using-many-blockingcollections-as-one"></a>Utilisation de nombreux BlockingCollections comme un seul

Pour les scénarios dans lesquels un consommateur doit prendre simultanément des éléments à partir de plusieurs collections, vous pouvez créer des tableaux de `BlockingCollection<T>` et utiliser les méthodes statiques telles que `TakeFromAny` et `AddToAny` qui effectuent un ajout ou une prise dans n’importe laquelle des collections du tableau. Si une collection bloque, la méthode en essaie immédiatement une autre jusqu’à ce qu’elle en trouve une qui peut effectuer l’opération. Pour plus d’informations, consultez [Guide pratique : utiliser des tableaux de collections de blocage dans un pipeline](how-to-use-arrays-of-blockingcollections.md).

## <a name="see-also"></a>Voir aussi

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[Collections et structures de données](../index.md)

[Collections thread-safe](index.md)




<!--HONumber=Nov16_HO3-->


