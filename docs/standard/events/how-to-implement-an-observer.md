---
title: "Comment&#160;: impl&#233;menter une m&#233;thode Observer | Microsoft Docs"
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
  - "observateurs (.NET Framework), modèle de design observateur"
  - "modèle de design observateur (.NET Framework), implémentation des observateurs"
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: impl&#233;menter une m&#233;thode Observer
Le modèle de conception observateur requiert une division entre un observateur qui s'abonne aux notifications et un fournisseur qui surveille les données et envoie des notifications à un ou plusieurs observateurs.  Cette rubrique explique comment créer un observateur.  Une rubrique connexe, [Comment : implémenter un fournisseur](../../../docs/standard/events/how-to-implement-a-provider.md), explique comment créer un fournisseur.  
  
### Pour créer un observateur  
  
1.  Définissez l'observateur, qui est un type qui implémente l'interface <xref:System.IObserver%601?displayProperty=fullName>.  Par exemple, le code suivant définit un type nommé `TemperatureReporter` qui est une implémentation <xref:System.IObserver%601?displayProperty=fullName> construite avec un argument de type générique de `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Si l'observateur peut cesser de recevoir des notifications avant que le fournisseur appelle son implémentation <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>, définissez une variable privée qui contiendra l'implémentation <xref:System.IDisposable> retournée par la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName> du fournisseur.  Vous devez également définir une méthode d'abonnement qui appelle la méthode du fournisseur <xref:System.IObservable%601.Subscribe%2A> et stocke l'objet <xref:System.IDisposable> retourné.  Par exemple, le code suivant définit une variable privée nommée `unsubscriber` et définit une méthode `Subscribe` qui appelle la méthode <xref:System.IObservable%601.Subscribe%2A> du fournisseur et assigne l'objet retourné à la variable `unsubscriber`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Définissez une méthode qui permet à l'observateur d'arrêter de recevoir des notifications avant que le fournisseur appelle son implémentation <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>, si cette fonctionnalité est requise.  L'exemple suivant définit une méthode `Unsubscribe`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Fournissez des implémentations des trois méthodes définies par l'interface <xref:System.IObserver%601> : <xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>, <xref:System.IObserver%601.OnError%2A?displayProperty=fullName> et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>.  Selon le fournisseur et les besoins de l'application, les méthodes <xref:System.IObserver%601.OnError%2A> et <xref:System.IObserver%601.OnCompleted%2A> peuvent être des implémentations de stub.  Notez que la méthode <xref:System.IObserver%601.OnError%2A> ne doit pas gérer l'objet <xref:System.Exception> passé comme une exception et la méthode <xref:System.IObserver%601.OnCompleted%2A> est libre d'appeler l'implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> du fournisseur.  L'exemple suivant illustre l'implémentation <xref:System.IObserver%601> de la classe `TemperatureReporter`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## Exemple  
 L'exemple suivant contient le code source complet pour la classe `TemperatureReporter`, qui fournit l'implémentation <xref:System.IObserver%601> pour une application de surveillance de la température.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## Voir aussi  
 <xref:System.IObserver%601>   
 [Modèle de design observateur](../../../docs/standard/events/observer-design-pattern.md)   
 [Comment : implémenter un fournisseur](../../../docs/standard/events/how-to-implement-a-provider.md)   
 [Meilleures pratiques du modèle de design observateur](../../../docs/standard/events/observer-design-pattern-best-practices.md)