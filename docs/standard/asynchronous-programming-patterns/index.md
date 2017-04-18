---
title: "Modèles de programmation asynchrone | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 26d5c4da21671c0f4ce37bf08c28ae82213f4374
ms.lasthandoff: 04/08/2017

---
# <a name="asynchronous-programming-patterns"></a>Modèles de programmation asynchrone
Le .NET Framework propose trois modèles d’exécution d’opérations asynchrones :  
  
-   Le modèle de programmation asynchrone (APM) (également appelé modèle <xref:System.IAsyncResult>), dans lequel les opérations asynchrones nécessitent les méthodes `Begin` et `End` (par exemple, `BeginWrite` et `EndWrite` pour les opérations d’écriture asynchrones). Ce modèle n’est plus recommandé pour un futur développement. Pour plus d’informations sur la programmation asynchrone, consultez [Modèle de programmation asynchrone (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
-   Le modèle asynchrone basé sur les événements (EAP), qui nécessite une méthode avec le suffixe `Async`, ainsi qu'un ou plusieurs événements, des types de délégués de gestionnaire d'événements et des types dérivés de `EventArg`. Ce modèle a été introduit avec le .NET Framework 2.0. Il n'est plus recommandé pour un futur développement. Pour plus d'informations, consultez [Modèle asynchrone basé sur des événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
-   Le modèle asynchrone basé sur les tâches (TAP), qui utilise une méthode unique pour représenter le lancement et l’achèvement d’une opération asynchrone. Ce modèle a été introduit avec le .NET Framework 4. Il s'agit de la méthode recommandée pour la programmation asynchrone dans le .NET Framework. Les mots clés [async](~/docs/csharp/language-reference/keywords/async.md) et [await](~/docs/csharp/language-reference/keywords/await.md) en C#, ainsi que les opérateurs [Async](~/docs/visual-basic/language-reference/modifiers/async.md) et [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) en Visual Basic ajoutent au modèle TAP la prise en charge des langages. Pour plus d’informations, consultez [Modèle asynchrone basé sur des tâches (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Comparaison des modèles  
 Pour comprendre rapidement la façon dont chacun des trois modèles modélise les opérations asynchrones, prenons une méthode `Read` qui lit une quantité de données spécifiée dans une mémoire tampon fournie, en commençant à l'offset spécifié :  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
 Le modèle APM de cette méthode exposerait les méthodes `BeginRead` et `EndRead` :  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
 Le modèle EAP exposerait l'ensemble de types et de membres suivant :  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
 Le modèle TAP exposerait l'unique méthode `ReadAsync` suivante :  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
 Pour plus d'informations sur les modèles TAP, APM et EAP, consultez les liens fournis dans la section suivante.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Modèle de programmation asynchrone](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)|Décrit le modèle hérité qui utilise l'interface <xref:System.IAsyncResult> pour fournir un comportement asynchrone. Ce modèle n'est plus recommandé pour un futur développement.|  
|[Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)|Décrit le modèle hérité basé sur les événements qui fournit un comportement asynchrone. Ce modèle n'est plus recommandé pour un futur développement.|  
|[Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Décrit le nouveau modèle asynchrone basé sur l’espace de noms <xref:System.Threading.Tasks>. Ce modèle est recommandé pour la programmation asynchrone dans le .NET Framework 4 et versions ultérieures.|
