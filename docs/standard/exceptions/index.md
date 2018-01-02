---
title: "Gestion et levée des exceptions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b064dc39f5807b154a1529eebe17493ae84981cf
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Gestion et levée d’exceptions dans .NET

Les applications doivent pouvoir gérer de manière cohérente les erreurs qui se produisent au moment de l'exécution. .NET fournit un modèle pour avertir les applications de façon uniforme de la présence d’erreurs : les opérations .NET indiquent un échec en levant des exceptions.

## <a name="exceptions"></a>Exceptions

Une exception est une condition d'erreur ou un comportement inattendu rencontré par un programme en cours d'exécution. Les exceptions peuvent être levées à cause d’une erreur dans votre code ou dans le code que vous appelez (une bibliothèque partagée, par exemple), de ressources de système d’exploitation non disponibles, de conditions inattendues rencontrées par le runtime (du code qui ne peut pas être vérifié, par exemple), etc. Votre application peut récupérer suite à certaines de ces conditions, mais pas toutes. Bien que vous puissiez récupérer suite à la plupart des exceptions d'application, vous ne pouvez pas récupérer suite à la plupart des exceptions runtime.

Dans .NET, une exception est un objet qui hérite de la classe <xref:System.Exception?displayProperty=nameWithType>. Une exception est levée à partir d'une partie du code où un problème s'est produit. L'exception remonte la pile jusqu'à sa prise en charge par l'application ou l'arrêt du programme.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Exceptions et méthodes traditionnelles de gestion des erreurs

Traditionnellement, le modèle de gestion des erreurs d'un langage reposait soit sur le mode unique utilisé par le langage en question pour détecter des erreurs et leur trouver des gestionnaires appropriés, soit sur le mécanisme de gestion des erreurs fourni par le système d'exploitation. La façon dont .NET implémente la gestion des exceptions offre les avantages suivants :

- La gestion et la levée des exceptions fonctionne de la même façon pour les langages de programmation .NET.

- Ne requiert aucune syntaxe particulière pour la gestion des exceptions, mais laisse chaque langage définir sa propre syntaxe.

- Les exceptions peuvent être levées au-delà des limites des processus et même des ordinateurs.

- Un code de gestion des exceptions peut être ajouté à une application pour augmenter la fiabilité du programme.

Les exceptions offrent des avantages par rapport à d’autres méthodes de notification des erreurs, comme les codes de retour. Les erreurs ne passent pas inaperçues, car si une exception est levée et que vous ne la gérez pas, le runtime arrête votre application. Les valeurs non valides ne continuent pas à se propager dans le système parce que du code n’a pas pu vérifier un code de retour d’échec. 

## <a name="common-exceptions"></a>Exceptions courantes

Le tableau suivant répertorie certaines exceptions courantes avec des exemples de cause possible.

| Type d'exception | Type de base | Description | Exemple |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | Classe de base pour toutes les exceptions. | Aucun (utilisez une classe dérivée de cette exception). |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | Levée par le runtime uniquement en cas d’indexation incorrecte du tableau. | Indexation d’un tableau en dehors de sa plage valide : `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <xref:System.Exception> | Levée par le runtime uniquement si un objet Null est référencé. | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | Levée par les méthodes en cas d’état non valide. | Appel de `Enumerator.GetNext()` après la suppression d’un élément de la collection sous-jacente. |
| <xref:System.ArgumentException> | <xref:System.Exception> | Classe de base pour toutes les exceptions d’argument. | Aucun (utilisez une classe dérivée de cette exception). |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | Levée par les méthodes qui n’acceptent pas la valeur Null pour un argument. | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | Levée par les méthodes qui vérifient que les arguments sont inclus dans une plage donnée. | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a>Voir aussi

* [Classe et propriétés d’exception](exception-class-and-properties.md)
* [Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [Guide pratique : utiliser des exceptions spécifiques dans un bloc Catch](how-to-use-specific-exceptions-in-a-catch-block.md)
* [Guide pratique pour lever explicitement des exceptions](how-to-explicitly-throw-exceptions.md)
* [Guide pratique : créer des exceptions définies par l’utilisateur](how-to-create-user-defined-exceptions.md)
* [Utilisation de gestionnaires filtrés par l'utilisateur](using-user-filtered-exception-handlers.md)
* [Guide pratique pour utiliser des blocs Finally](how-to-use-finally-blocks.md)
* [Gestion des exceptions COM Interop](handling-com-interop-exceptions.md)
* [Meilleures pratiques pour les exceptions](best-practices-for-exceptions.md)

Pour en savoir plus sur le fonctionnement des exceptions dans .NET, consultez [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md) (Tout ce que doit savoir un développeur sur les exceptions dans le runtime).
