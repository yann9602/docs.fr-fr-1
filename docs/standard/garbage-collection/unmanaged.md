---
title: "Cleaning Up Unmanaged Resources | Microsoft Docs"
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
  - "Close method"
  - "Dispose method"
  - "garbage collector"
  - "garbage collection, unmanaged resources"
  - "cleanup operations"
  - "explicit cleanups"
  - "unmanaged resource cleanup"
  - "Finalize method"
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Cleaning Up Unmanaged Resources
Pour la majorité des objets créés par votre application, vous pouvez laisser au récupérateur de mémoire du .NET Framework le soin de gérer les tâches de gestion de mémoire.  Lorsque vous créez des objets qui incluent des ressources non managées, vous devez libérer explicitement ces ressources lorsque vous avez fini de les utiliser dans votre application.  Les types les plus courants de ressources non managées sont des objets qui encapsulent les ressources du système d'exploitation, telles que les fichiers, les fenêtres, les connexions réseau ou les connexions de bases de données.  Bien que le récupérateur de mémoire puisse assurer le suivi de la durée de vie d'un objet qui encapsule une ressource non managée, il ne sait pas comment libérer et nettoyer la ressource non managée.  
  
 Si vos types utilisent les ressources non managées, procédez comme suit :  
  
-   Implémentez le [modèle de suppression](../../../docs/standard/design-guidelines/dispose-pattern.md).  Pour ce faire, vous devez fournir une implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> pour activer la version déterministe des ressources non managées.  Un consommateur de votre type appelle la méthode <xref:System.IDisposable.Dispose%2A> lorsque l'objet \(et les ressources qu'il utilise\) n'est plus nécessaire.  La méthode <xref:System.IDisposable.Dispose%2A> libère immédiatement les ressources non managées.  
  
-   Prévoyez que vos ressources non managées soient libérées si un consommateur de votre type oublie d'appeler la méthode <xref:System.IDisposable.Dispose%2A>.  Il existe deux façons d'effectuer cette opération :  
  
    -   Utilisez un handle sécurisé pour encapsuler votre ressource non managée.  Il s'agit de la technique recommandée.  Les handles sécurisés sont dérivés de la classe <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> et incluent une méthode <xref:System.Object.Finalize%2A> fiable.  Lorsque vous utilisez un handle sécurisé, implémentez simplement l'interface <xref:System.IDisposable> et appelez la méthode <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> de votre handle sécurisé dans l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>.  Le finaliseur du handle sécurisé est appelé automatiquement par le récupérateur de mémoire si sa méthode <xref:System.IDisposable.Dispose%2A> n'est pas appelé.  
  
         — ou —  
  
    -   Remplacez la méthode <xref:System.Object.Finalize%2A?displayProperty=fullName>.  La finalisation active la version non déterministe des ressources non managées lorsque le consommateur d'un type n'appelle pas la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> pour les supprimer de manière déterministe.  Toutefois, comme la finalisation de l'objet peut s'avérer être une opération complexe et susceptible d'engendrer des erreurs, nous vous recommandons d'utiliser un handle sécurisé au lieu de fournir votre propre finaliseur.  
  
 Les consommateurs de votre type peuvent ensuite appeler directement votre implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> pour libérer la mémoire utilisée par les ressources non managées.  Lorsque vous implémentez correctement une méthode <xref:System.IDisposable.Dispose%2A>, la méthode <xref:System.Object.Finalize%2A> de votre handle sécurisé ou votre propre substitution de la méthode <xref:System.Object.Finalize%2A?displayProperty=fullName> devient un dispositif de protection pour nettoyer les ressources si la méthode <xref:System.IDisposable.Dispose%2A> n'est pas appelée.  
  
## Dans cette section  
 [Implementing a Dispose Method](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 Explique comment implémenter le [modèle de suppression](../../../docs/standard/design-guidelines/dispose-pattern.md) pour libérer les ressources non managées.  
  
 [Using Objects That Implement IDisposable](../../../docs/standard/garbage-collection/using-objects.md)  
 Décrit comment les consommateurs d'un type vérifient que son implémentation de <xref:System.IDisposable.Dispose%2A> est appelée.  Pour ce faire, nous vous recommandons d'utiliser l'instruction `using` en C\# ou l'instruction `Using` en Visual Basic.  
  
## Référence  
 <xref:System.IDisposable?displayProperty=fullName>  
 Définit la méthode <xref:System.IDisposable.Dispose%2A> pour libérer des ressources non managées.  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName>  
 Prévoit la finalisation de l'objet si les ressources non managées ne sont pas libérées par la méthode <xref:System.IDisposable.Dispose%2A>.  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>  
 Supprime la finalisation.  Cette méthode est généralement appelée à partir d'une méthode `Dispose` pour empêcher un finaliseur de s'exécuter.