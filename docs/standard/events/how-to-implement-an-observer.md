---
title: "Comment : implémenter une méthode Observer"
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a>Comment : implémenter une méthode Observer
Le modèle de conception observateur requiert une division entre un observateur, qui s’inscrit pour les notifications, et un fournisseur qui surveille les données et envoie des notifications à un ou plusieurs observateurs. Cette rubrique explique comment créer un observateur. Une rubrique connexe, [Comment : implémenter un fournisseur](../../../docs/standard/events/how-to-implement-a-provider.md), explique comment créer un fournisseur.  
  
### <a name="to-create-an-observer"></a>Pour créer un observateur  
  
1.  Définissez l’Observateur, qui est un type qui implémente le <xref:System.IObserver%601?displayProperty=nameWithType> interface. Par exemple, le code suivant définit un type nommé `TemperatureReporter` qui est construit <xref:System.IObserver%601?displayProperty=nameWithType> mise en œuvre avec un argument de type générique `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Si l’observateur peut cesser de recevoir des notifications avant que le fournisseur appelle son <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implémentation, définissez une variable privée qui contiendra le <xref:System.IDisposable> implémentation retournée par le fournisseur <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> (méthode). Vous devez également définir une méthode d’abonnement qui appelle le fournisseur <xref:System.IObservable%601.Subscribe%2A> (méthode) et les magasins retournés <xref:System.IDisposable> objet. Par exemple, le code suivant définit une variable privée nommée `unsubscriber` et définit un `Subscribe` méthode qui appelle le fournisseur <xref:System.IObservable%601.Subscribe%2A> (méthode) et affecte l’objet retourné à la `unsubscriber` variable.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Définir une méthode qui permet à l’Observateur d’arrêter de recevoir des notifications avant que le fournisseur appelle son <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implémentation, si cette fonctionnalité est nécessaire. L’exemple suivant définit un `Unsubscribe` (méthode).  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Fournir des implémentations des trois méthodes définies par le <xref:System.IObserver%601> interface : <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Selon le fournisseur et les besoins de l’application, le <xref:System.IObserver%601.OnError%2A> et <xref:System.IObserver%601.OnCompleted%2A> méthodes peuvent être des implémentations de stub. Notez que la <xref:System.IObserver%601.OnError%2A> méthode ne doit pas gérer passé <xref:System.Exception> objet en tant qu’exception et le <xref:System.IObserver%601.OnCompleted%2A> méthode est libre d’appel du fournisseur <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implémentation. L’exemple suivant illustre la <xref:System.IObserver%601> mise en oeuvre de la `TemperatureReporter` classe.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient le code source complet pour le `TemperatureReporter` (classe), qui fournit le <xref:System.IObserver%601> implémentation pour une application de surveillance de la température.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IObserver%601>  
 [Modèle de conception Observateur](../../../docs/standard/events/observer-design-pattern.md)  
 [Guide pratique pour implémenter un fournisseur](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [Meilleures pratiques du modèle de design observateur](../../../docs/standard/events/observer-design-pattern-best-practices.md)
