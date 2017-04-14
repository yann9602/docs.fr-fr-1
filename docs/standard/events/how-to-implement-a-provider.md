---
title: "Comment&#160;: impl&#233;menter un fournisseur | Microsoft Docs"
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
  - "modèle de design observateur (.NET Framework), implémentation des fournisseurs"
  - "fournisseurs (.NET Framework), dans le modèle de design observateur"
  - "observables (.NET Framework), dans le modèle de design observateur"
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: impl&#233;menter un fournisseur
Le modèle de conception observateur requiert une division entre un fournisseur qui surveille les données et envoie des notifications, et un ou plusieurs observateurs, qui reçoivent les notifications \(rappels\) du fournisseur.  Cette rubrique explique comment créer un fournisseur.  Une rubrique connexe, [Comment : implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md), explique comment créer un observateur.  
  
### Pour créer un fournisseur  
  
1.  Définissez les données que le fournisseur est chargé d'envoyer aux observateurs.  Même si le fournisseur et les données qu'il envoie aux observateurs peuvent être un type unique, ils sont en général représentés par des types différents.  Par exemple, dans une application de surveillance de la température, la structure `Temperature` définit les données que le fournisseur \(représenté par la classe `TemperatureMonitor` définie à l'étape suivante\) surveille et auxquelles les observateurs s'abonnent.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  Définissez le fournisseur de données, qui est un type qui implémente l'interface <xref:System.IObservable%601?displayProperty=fullName>.  L'argument de type générique du fournisseur est le type que le fournisseur envoie aux observateurs.  L'exemple suivant définit une classe `TemperatureMonitor`, qui est une implémentation <xref:System.IObservable%601?displayProperty=fullName> construite avec un argument de type générique de `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  Déterminez comment le fournisseur stockera les références aux observateurs afin que chaque observateur puisse être averti, le cas échéant.  En règle générale, un objet de collection, tel qu'un objet <xref:System.Collections.Generic.List%601> générique est utilisé à cette fin.  L'exemple suivant définit un objet <xref:System.Collections.Generic.List%601> privé qui est instancié dans le constructeur de classe `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  Définissez une implémentation <xref:System.IDisposable> que le fournisseur peut retourner aux abonnés afin qu'ils puissent cesser de recevoir des notifications à tout moment.  L'exemple suivant définit une classe `Unsubscriber` imbriquée à laquelle est passée une référence à la collection d'abonnés et à l'abonné lorsque la classe est instanciée.  Ce code permet à l'abonné d'appeler l'implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> de l'objet pour se supprimer de la collection des abonnés.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  Implémentez la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName>.  Une référence à l'interface <xref:System.IObserver%601?displayProperty=fullName> est passée à la méthode et doit être stockée dans l'objet conçu dans ce but à l'étape 3.  La méthode doit ensuite retourner l'implémentation <xref:System.IDisposable> développée à l'étape 4.  L'exemple suivant illustre l'implémentation de la méthode <xref:System.IObservable%601.Subscribe%2A> dans la classe `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  Avertissez les observateurs si nécessaire en appelant leurs implémentations <xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>, <xref:System.IObserver%601.OnError%2A?displayProperty=fullName> et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>.  Dans certains cas, un fournisseur peut ne pas appeler la méthode <xref:System.IObserver%601.OnError%2A> lorsqu'une erreur se produit.  Par exemple, la méthode `GetTemperature` suivante simule un moniteur qui indique les données de température toutes les cinq secondes et notifie les observateurs si la température a changé d'au moins .1 degré depuis la lecture précédente.  Si le périphérique n'enregistre pas une température \(autrement dit, si sa valeur est null\), le fournisseur avertit les observateurs que la transmission est terminée.  Notez que, en plus d'appeler la méthode pour chaque méthode <xref:System.IObserver%601.OnCompleted%2A> de l'observateur, la méthode `GetTemperature` supprime la collection <xref:System.Collections.Generic.List%601>.  Dans ce cas, le fournisseur ne fait pas appel à la méthode <xref:System.IObserver%601.OnError%2A> de ses observateurs.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## Exemple  
 L'exemple suivant contient le code source complet pour définir une implémentation <xref:System.IObservable%601> pour une application de surveillance de la température.  Il inclut la structure `Temperature`, qui correspond aux données envoyées aux observateurs, et la classe `TemperatureMonitor`, qui est l'implémentation <xref:System.IObservable%601>.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## Voir aussi  
 <xref:System.IObservable%601>   
 [Modèle de design observateur](../../../docs/standard/events/observer-design-pattern.md)   
 [Comment : implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md)   
 [Meilleures pratiques du modèle de design observateur](../../../docs/standard/events/observer-design-pattern-best-practices.md)