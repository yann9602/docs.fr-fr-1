---
title: "Comment : implémenter un fournisseur"
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
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9d8f96de8cb3d13568e755f1d5e885e0474d891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-provider"></a>Comment : implémenter un fournisseur
Le modèle de conception observateur requiert une division entre un fournisseur qui surveille les données et envoie des notifications, et un ou plusieurs observateurs, qui reçoivent des notifications (rappels) à partir du fournisseur. Cette rubrique explique comment créer un fournisseur. Une rubrique connexe, [Comment : implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md), explique comment créer un observateur.  
  
### <a name="to-create-a-provider"></a>Pour créer un fournisseur  
  
1.  Définir les données que le fournisseur est chargé d’envoyer aux observateurs. Bien que le fournisseur et les données qu’il envoie aux observateurs peuvent être un type unique, ils sont généralement représentées par différents types. Par exemple, dans une application, de surveillance de la température le `Temperature` structure définit les données que le fournisseur (qui est représenté par le `TemperatureMonitor` classe définie dans l’étape suivante) surveille et auxquelles les observateurs s’abonner.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  Définir le fournisseur de données, qui est un type qui implémente le <xref:System.IObservable%601?displayProperty=nameWithType> interface. Argument de type générique du fournisseur est le type que le fournisseur envoie aux observateurs. L’exemple suivant définit un `TemperatureMonitor` (classe), qui est un élément construit <xref:System.IObservable%601?displayProperty=nameWithType> mise en œuvre avec un argument de type générique `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  Déterminez comment le fournisseur stockera les références aux observateurs afin que chaque observateur puisse être averti lorsque cela est approprié. En règle générale, un objet de collection comme un type générique <xref:System.Collections.Generic.List%601> objet est utilisé à cet effet. L’exemple suivant définit un privé <xref:System.Collections.Generic.List%601> objet instancié dans le `TemperatureMonitor` constructeur de classe.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  Définir un <xref:System.IDisposable> implémentation le fournisseur peut retourner aux abonnés afin qu’ils peuvent cesser de recevoir des notifications à tout moment. L’exemple suivant définit une liste imbriquée `Unsubscriber` classe passée une référence à la collection d’abonnés et à l’abonné lorsque la classe est instanciée. Ce code permet à l’abonné appeler l’objet <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implémentation à supprimer de la collection d’abonnés.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  Implémentez la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>. La méthode est passée à la <xref:System.IObserver%601?displayProperty=nameWithType> de l’interface et doivent être stockées dans l’objet conçu à cet effet à l’étape 3. La méthode doit ensuite retourner le <xref:System.IDisposable> implémentation développé à l’étape 4. L’exemple suivant illustre l’implémentation de la <xref:System.IObservable%601.Subscribe%2A> méthode dans la `TemperatureMonitor` classe.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  Informer les observateurs si nécessaire en appelant leurs <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implémentations. Dans certains cas, un fournisseur ne peut pas appeler le <xref:System.IObserver%601.OnError%2A> méthode lorsqu’une erreur se produit. Par exemple, les éléments suivants `GetTemperature` méthode simule un moniteur qui lit les données de température toutes les cinq secondes et notifie les observateurs si la température a changé par au moins.1 degré depuis la lecture précédente. Si l’appareil ne signale pas une température (autrement dit, si sa valeur est null), le fournisseur notifie les observateurs que la transmission est terminée. Notez que, en plus de l’appel de chaque observateur <xref:System.IObserver%601.OnCompleted%2A> (méthode), la `GetTemperature` méthode efface le <xref:System.Collections.Generic.List%601> collection. Dans ce cas, le fournisseur ne met à aucun appel à la <xref:System.IObserver%601.OnError%2A> méthode de ses observateurs.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient le code source complet permettant de définir un <xref:System.IObservable%601> implémentation pour une application de surveillance de la température. Il inclut le `Temperature` structure des données envoyées aux observateurs, et la `TemperatureMonitor` (classe), qui est le <xref:System.IObservable%601> implémentation.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IObservable%601>  
 [Modèle de conception Observateur](../../../docs/standard/events/observer-design-pattern.md)  
 [Guide pratique pour implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Meilleures pratiques du modèle de design observateur](../../../docs/standard/events/observer-design-pattern-best-practices.md)
