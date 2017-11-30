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
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="959ed-102">Comment : implémenter une méthode Observer</span><span class="sxs-lookup"><span data-stu-id="959ed-102">How to: Implement an Observer</span></span>
<span data-ttu-id="959ed-103">Le modèle de conception observateur requiert une division entre un observateur, qui s’inscrit pour les notifications, et un fournisseur qui surveille les données et envoie des notifications à un ou plusieurs observateurs.</span><span class="sxs-lookup"><span data-stu-id="959ed-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="959ed-104">Cette rubrique explique comment créer un observateur.</span><span class="sxs-lookup"><span data-stu-id="959ed-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="959ed-105">Une rubrique connexe, [Comment : implémenter un fournisseur](../../../docs/standard/events/how-to-implement-a-provider.md), explique comment créer un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="959ed-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="959ed-106">Pour créer un observateur</span><span class="sxs-lookup"><span data-stu-id="959ed-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="959ed-107">Définissez l’Observateur, qui est un type qui implémente le <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="959ed-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="959ed-108">Par exemple, le code suivant définit un type nommé `TemperatureReporter` qui est construit <xref:System.IObserver%601?displayProperty=nameWithType> mise en œuvre avec un argument de type générique `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="959ed-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="959ed-109">Si l’observateur peut cesser de recevoir des notifications avant que le fournisseur appelle son <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implémentation, définissez une variable privée qui contiendra le <xref:System.IDisposable> implémentation retournée par le fournisseur <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="959ed-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="959ed-110">Vous devez également définir une méthode d’abonnement qui appelle le fournisseur <xref:System.IObservable%601.Subscribe%2A> (méthode) et les magasins retournés <xref:System.IDisposable> objet.</span><span class="sxs-lookup"><span data-stu-id="959ed-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="959ed-111">Par exemple, le code suivant définit une variable privée nommée `unsubscriber` et définit un `Subscribe` méthode qui appelle le fournisseur <xref:System.IObservable%601.Subscribe%2A> (méthode) et affecte l’objet retourné à la `unsubscriber` variable.</span><span class="sxs-lookup"><span data-stu-id="959ed-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="959ed-112">Définir une méthode qui permet à l’Observateur d’arrêter de recevoir des notifications avant que le fournisseur appelle son <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implémentation, si cette fonctionnalité est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="959ed-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="959ed-113">L’exemple suivant définit un `Unsubscribe` (méthode).</span><span class="sxs-lookup"><span data-stu-id="959ed-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="959ed-114">Fournir des implémentations des trois méthodes définies par le <xref:System.IObserver%601> interface : <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, et <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="959ed-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="959ed-115">Selon le fournisseur et les besoins de l’application, le <xref:System.IObserver%601.OnError%2A> et <xref:System.IObserver%601.OnCompleted%2A> méthodes peuvent être des implémentations de stub.</span><span class="sxs-lookup"><span data-stu-id="959ed-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="959ed-116">Notez que la <xref:System.IObserver%601.OnError%2A> méthode ne doit pas gérer passé <xref:System.Exception> objet en tant qu’exception et le <xref:System.IObserver%601.OnCompleted%2A> méthode est libre d’appel du fournisseur <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implémentation.</span><span class="sxs-lookup"><span data-stu-id="959ed-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="959ed-117">L’exemple suivant illustre la <xref:System.IObserver%601> mise en oeuvre de la `TemperatureReporter` classe.</span><span class="sxs-lookup"><span data-stu-id="959ed-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="959ed-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="959ed-118">Example</span></span>  
 <span data-ttu-id="959ed-119">L’exemple suivant contient le code source complet pour le `TemperatureReporter` (classe), qui fournit le <xref:System.IObserver%601> implémentation pour une application de surveillance de la température.</span><span class="sxs-lookup"><span data-stu-id="959ed-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="959ed-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="959ed-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="959ed-121">Modèle de conception Observateur</span><span class="sxs-lookup"><span data-stu-id="959ed-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="959ed-122">Guide pratique pour implémenter un fournisseur</span><span class="sxs-lookup"><span data-stu-id="959ed-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="959ed-123">Meilleures pratiques du modèle de design observateur</span><span class="sxs-lookup"><span data-stu-id="959ed-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
