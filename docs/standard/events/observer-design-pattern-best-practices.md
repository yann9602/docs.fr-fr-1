---
title: "Meilleures pratiques du mod&#232;le de design observateur | Microsoft Docs"
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
  - "meilleures pratiques (.NET Framework), modèle de design observateur"
  - "modèle de design observateur (.NET Framework), meilleures pratiques"
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Meilleures pratiques du mod&#232;le de design observateur
Dans le .NET Framework, le modèle de conception observateur est implémenté comme un ensemble d'interfaces.  L'interface <xref:System.IObservable%601?displayProperty=fullName> représente le fournisseur de données, qui est également chargé de fournir une implémentation <xref:System.IDisposable> permettant aux observateurs d'annuler leur abonnement aux notifications.  L'interface <xref:System.IObserver%601?displayProperty=fullName> représente l'observateur.  Cette rubrique décrit les meilleures pratiques que les développeurs doivent suivre quand ils implémentent le modèle de conception observateur à l'aide de ces interfaces.  
  
## Threads  
 En général, un fournisseur implémente la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName> en ajoutant un observateur à une liste d'abonnés représentée par un objet de collection, puis il implémente la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> en supprimant un observateur de la liste des abonnés.  Un observateur peut appeler ces méthodes à tout moment.  De plus, étant donné que le contrat fournisseur\/observateur ne spécifie pas qui est responsable de l'annulation d'abonnement après la méthode de rappel <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>, il est possible que le fournisseur et l'observateur tentent de supprimer le même membre de la liste.  En raison de cette éventualité, les méthodes <xref:System.IObservable%601.Subscribe%2A> et <xref:System.IDisposable.Dispose%2A> doivent être thread\-safe.  En général, cela implique l'utilisation d'une [collection simultanée](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) ou d'un verrou.  Les implémentations qui ne sont pas thread\-safe doivent indiquer explicitement qu'elles ne le sont pas.  
  
 Les garanties supplémentaires doivent être spécifiées dans une couche supérieure au contrat fournisseur\/observateur.  Les implémenteurs doivent indiquer clairement lorsqu'ils imposent des conditions supplémentaires afin d'éviter la confusion des utilisateurs concernant le contrat observateur.  
  
## Gestion des exceptions  
 En raison du couplage faible entre un fournisseur de données et un observateur, les exceptions du modèle de conception observateur ont un but informatif.  Cela affecte la façon dont les observateurs et les fournisseurs gèrent les exceptions dans le modèle de conception observateur.  
  
### Le fournisseur – Appel de la méthode OnError  
 La méthode <xref:System.IObserver%601.OnError%2A> a pour but d'informer les observateurs, tout comme la méthode <xref:System.IObserver%601.OnNext%2A?displayProperty=fullName>.  Toutefois, la méthode <xref:System.IObserver%601.OnNext%2A> sert à fournir aux observateurs des données actuelles ou mises à jour, alors que la méthode <xref:System.IObserver%601.OnError%2A> sert à indiquer que le fournisseur ne peut pas fournir de données valides.  
  
 Le fournisseur doit suivre ces meilleures pratiques lors de la gestion des exceptions et de l'appel de la méthode <xref:System.IObserver%601.OnError%2A> :  
  
-   Le fournisseur doit gérer ses propres exceptions s'il a des exigences spécifiques.  
  
-   Le fournisseur ne doit pas exiger ni s'attendre à ce que les observateurs gèrent les exceptions.  
  
-   Le fournisseur doit appeler la méthode <xref:System.IObserver%601.OnError%2A> quand il gère une exception qui compromet sa capacité à fournir des mises à jour.  Les informations sur ces exceptions peuvent être passées à l'observateur.  Dans les autres cas, il est inutile d'informer les observateurs des exceptions.  
  
 Une fois que le fournisseur a appelé la méthode <xref:System.IObserver%601.OnError%2A> ou <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>, il ne doit y avoir aucune autre notification et le fournisseur peut annuler l'abonnement de ses observateurs.  Toutefois, les observateurs peuvent également annuler leur abonnement à tout moment, y compris avant et après la réception d'une notification <xref:System.IObserver%601.OnError%2A> ou <xref:System.IObserver%601.OnCompleted%2A?displayProperty=fullName>.  Le modèle de conception observateur ne détermine pas qui du fournisseur ou de l'observateur est responsable de l'annulation d'abonnement. Par conséquent, il est possible que les deux tentent de se désabonner.  En règle générale, quand les observateurs annulent un abonnement, ils sont supprimés de la collection d'abonnés.  Dans une application à thread unique, l'implémentation <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> doit s'assurer qu'une référence d'objet est valide et que l'objet est membre de la collection d'abonnés avant d'essayer de le supprimer.  Dans une application multithread, un objet de collection thread\-safe, tel qu'un objet <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>, doit être utilisé.  
  
### L'observateur – Implémentation de la méthode OnError  
 Quand un observateur reçoit une notification d'erreur provenant du fournisseur, celle\-ci lui est fournie à titre indicatif et ne l'oblige pas à effectuer d'action particulière.  
  
 L'observateur doit utiliser ces meilleures pratiques quand il répond à un appel de méthode <xref:System.IObserver%601.OnError%2A> provenant du fournisseur :  
  
-   L'observateur ne doit pas lever d'exceptions depuis ses implémentations d'interface, telles que <xref:System.IObserver%601.OnNext%2A> ou <xref:System.IObserver%601.OnError%2A>.  Si l'observateur lève des exceptions, il doit s'attendre à ce qu'elles ne soient pas gérées.  
  
-   Pour conserver la pile des appels, un observateur qui souhaite lever un objet <xref:System.Exception> passé à sa méthode <xref:System.IObserver%601.OnError%2A> doit encapsuler l'exception avant de la lever.  Un objet d'exception standard doit être utilisé à cet effet.  
  
## Autres meilleures pratiques  
 Dans la méthode <xref:System.IObservable%601.Subscribe%2A?displayProperty=fullName>, une tentative d'annulation d'abonnement peut entraîner une référence null.  Par conséquent, nous vous recommandons d'éviter cette pratique.  
  
 Même s'il est possible d'attacher un observateur à plusieurs fournisseurs, le modèle recommandé consiste à attacher une instance <xref:System.IObserver%601> à une seule et même instance <xref:System.IObservable%601>.  
  
## Voir aussi  
 [Modèle de design observateur](../../../docs/standard/events/observer-design-pattern.md)   
 [Comment : implémenter une méthode Observer](../../../docs/standard/events/how-to-implement-an-observer.md)   
 [Comment : implémenter un fournisseur](../../../docs/standard/events/how-to-implement-a-provider.md)