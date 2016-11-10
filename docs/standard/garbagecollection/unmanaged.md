---
title: "Nettoyage de ressources non managées"
description: "Nettoyage de ressources non managées"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8c97c3e2-8619-47ce-ae29-d6a3140bfa83
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 692916bc5a9afd55dc4e3d0249386d2e3750895f

---

# <a name="cleaning-up-unmanaged-resources"></a>Nettoyage de ressources non managées

Pour la majorité des objets créés par votre application, vous pouvez laisser au Garbage collector .NET le soin de gérer les tâches de gestion de mémoire. Lorsque vous créez des objets qui incluent des ressources non managées, vous devez libérer explicitement ces ressources lorsque vous avez fini de les utiliser dans votre application. Les types les plus courants de ressources non managées sont des objets qui encapsulent les ressources du système d'exploitation, telles que les fichiers, les fenêtres, les connexions réseau ou les connexions de bases de données. Bien que le récupérateur de mémoire puisse assurer le suivi de la durée de vie d'un objet qui encapsule une ressource non managée, il ne sait pas comment libérer et nettoyer la ressource non managée. 

Si vos types utilisent les ressources non managées, procédez comme suit : 

* Implémentez le modèle de suppression. Pour ce faire, vous devez fournir une implémentation de [IDisposable.Dispose](xref:System.IDisposable.Dispose) pour activer la mise en production déterministe des ressources non managées. Un consommateur de votre type appelle la méthode [Dispose](xref:System.IDisposable.Dispose) quand l’objet (et les ressources qu’il utilise) ne sont plus nécessaires. La méthode [Dispose](xref:System.IDisposable.Dispose) libère immédiatement les ressources non managées. 

* Prévoyez que vos ressources non managées soient libérées si un consommateur de votre type oublie d’appeler la méthode [Dispose](xref:System.IDisposable.Dispose). Il existe deux façons d'effectuer cette opération : 

    * Utilisez un handle sécurisé pour encapsuler votre ressource non managée. Il s'agit de la technique recommandée. Les handles sécurisés sont dérivés de la classe [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) et incluent une méthode [Finalize](xref:System.Object.Finalize) fiable. Lorsque vous utilisez un handle sécurisé, implémentez simplement l’interface [IDisposable](xref:System.IDisposable) et appelez la méthode [Dispose](xref:System.IDisposable.Dispose) de votre handle sécurisé dans votre implémentation de [IDisposable.Dispose](xref:System.IDisposable.Dispose). Le finaliseur du handle sécurisé est appelé automatiquement par le Garbage collector si sa méthode [Dispose](xref:System.IDisposable.Dispose) n’est pas appelée. 

      - ou -

    * Remplacez la méthode [Object.Finalize](xref:System.Object.Finalize). La finalisation active la mise en production non déterministe des ressources non managées quand le consommateur d’un type n’appelle pas la méthode [IDisposable.Dispose](xref:System.IDisposable.Dispose) pour les supprimer de manière déterministe. Toutefois, comme la finalisation de l'objet peut s'avérer être une opération complexe et susceptible d'engendrer des erreurs, nous vous recommandons d'utiliser un handle sécurisé au lieu de fournir votre propre finaliseur. 

Les consommateurs de votre type peuvent ensuite appeler directement votre implémentation de [IDisposable.Dispose](xref:System.IDisposable.Dispose)pour libérer la mémoire utilisée par les ressources non managées. Lorsque vous implémentez correctement une méthode [Dispose](xref:System.IDisposable.Dispose), la méthode [Finalize](xref:System.Object.Finalize) de votre handle sécurisé ou votre propre substitution de la méthode [Object.Finalize](xref:System.Object.Finalize)devient un dispositif de protection pour nettoyer les ressources si la méthode [Dispose](xref:System.IDisposable.Dispose) n’est pas appelée. 

## <a name="in-this-section"></a>Dans cette section

[Implémentation d’une méthode Dispose](implementing-dispose.md) : explique comment implémenter le modèle de suppression pour libérer les ressources non managées.

[Utilisation d’objets implémentant IDisposable](using-objects.md) : décrit comment les consommateurs d’un type vérifient que son implémentation de la méthode Dispose est appelée. Pour ce faire, nous vous recommandons d’utiliser l’instruction using en C# ou l’instruction Using en Visual Basic.

## <a name="reference"></a>Référence

[System.IDisposable](xref:System.IDisposable) définit la méthode `Dispose` pour libérer des ressources non managées.

[Object.Finalize](xref:System.Object.Finalize) prévoit la finalisation de l’objet si les ressources non managées ne sont pas libérées par la méthode `Dispose`. 

[GC.SuppressFinalize](xref:System.GC#System_GC_SuppressFinalize_System_Object_) : supprime la finalisation. Cette méthode est généralement appelée à partir d'une méthode `Dispose` pour empêcher un finaliseur de s'exécuter. 



<!--HONumber=Nov16_HO1-->


