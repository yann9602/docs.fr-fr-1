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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 82e314dacc9fb2657a3a7088a928b59d00282a5d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="296ab-102">Gestion et levée d’exceptions dans .NET</span><span class="sxs-lookup"><span data-stu-id="296ab-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="296ab-103">Les applications doivent pouvoir gérer de manière cohérente les erreurs qui se produisent au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="296ab-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="296ab-104">.NET fournit un modèle pour avertir les applications de façon uniforme de la présence d’erreurs : les opérations .NET indiquent un échec en levant des exceptions.</span><span class="sxs-lookup"><span data-stu-id="296ab-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="296ab-105">Exceptions</span><span class="sxs-lookup"><span data-stu-id="296ab-105">Exceptions</span></span>

<span data-ttu-id="296ab-106">Une exception est une condition d'erreur ou un comportement inattendu rencontré par un programme en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="296ab-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="296ab-107">Les exceptions peuvent être levées à cause d’une erreur dans votre code ou dans le code que vous appelez (une bibliothèque partagée, par exemple), de ressources de système d’exploitation non disponibles, de conditions inattendues rencontrées par le runtime (du code qui ne peut pas être vérifié, par exemple), etc.</span><span class="sxs-lookup"><span data-stu-id="296ab-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that cannot be verified), and so on.</span></span> <span data-ttu-id="296ab-108">Votre application peut récupérer suite à certaines de ces conditions, mais pas toutes.</span><span class="sxs-lookup"><span data-stu-id="296ab-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="296ab-109">Bien que vous puissiez récupérer suite à la plupart des exceptions d'application, vous ne pouvez pas récupérer suite à la plupart des exceptions runtime.</span><span class="sxs-lookup"><span data-stu-id="296ab-109">Although you can recover from most application exceptions, you cannot recover from most runtime exceptions.</span></span>

<span data-ttu-id="296ab-110">Dans .NET, une exception est un objet qui hérite de la classe <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="296ab-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="296ab-111">Une exception est levée à partir d'une partie du code où un problème s'est produit.</span><span class="sxs-lookup"><span data-stu-id="296ab-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="296ab-112">L'exception remonte la pile jusqu'à sa prise en charge par l'application ou l'arrêt du programme.</span><span class="sxs-lookup"><span data-stu-id="296ab-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="296ab-113">Exceptions et méthodes traditionnelles de gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="296ab-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="296ab-114">Traditionnellement, le modèle de gestion des erreurs d'un langage reposait soit sur le mode unique utilisé par le langage en question pour détecter des erreurs et leur trouver des gestionnaires appropriés, soit sur le mécanisme de gestion des erreurs fourni par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="296ab-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="296ab-115">La façon dont .NET implémente la gestion des exceptions offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="296ab-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="296ab-116">La gestion et la levée des exceptions fonctionne de la même façon pour les langages de programmation .NET.</span><span class="sxs-lookup"><span data-stu-id="296ab-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="296ab-117">Ne requiert aucune syntaxe particulière pour la gestion des exceptions, mais laisse chaque langage définir sa propre syntaxe.</span><span class="sxs-lookup"><span data-stu-id="296ab-117">Does not require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="296ab-118">Les exceptions peuvent être levées au-delà des limites des processus et même des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="296ab-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="296ab-119">Un code de gestion des exceptions peut être ajouté à une application pour augmenter la fiabilité du programme.</span><span class="sxs-lookup"><span data-stu-id="296ab-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="296ab-120">Les exceptions offrent des avantages par rapport à d’autres méthodes de notification des erreurs, comme les codes de retour.</span><span class="sxs-lookup"><span data-stu-id="296ab-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="296ab-121">Les erreurs ne passent pas inaperçues, car si une exception est levée et que vous ne la gérez pas, le runtime arrête votre application.</span><span class="sxs-lookup"><span data-stu-id="296ab-121">Failures do not go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="296ab-122">Les valeurs non valides ne continuent pas à se propager dans le système parce que du code n’a pas pu vérifier un code de retour d’échec.</span><span class="sxs-lookup"><span data-stu-id="296ab-122">Invalid values do not continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span> 

## <a name="common-exceptions"></a><span data-ttu-id="296ab-123">Exceptions courantes</span><span class="sxs-lookup"><span data-stu-id="296ab-123">Common Exceptions</span></span>

<span data-ttu-id="296ab-124">Le tableau suivant répertorie certaines exceptions courantes avec des exemples de cause possible.</span><span class="sxs-lookup"><span data-stu-id="296ab-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="296ab-125">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="296ab-125">Exception type</span></span> | <span data-ttu-id="296ab-126">Type de base</span><span class="sxs-lookup"><span data-stu-id="296ab-126">Base type</span></span> | <span data-ttu-id="296ab-127">Description</span><span class="sxs-lookup"><span data-stu-id="296ab-127">Description</span></span> | <span data-ttu-id="296ab-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="296ab-128">Example</span></span> |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | <span data-ttu-id="296ab-129">Classe de base pour toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="296ab-129">Base class for all exceptions.</span></span> | <span data-ttu-id="296ab-130">Aucun (utilisez une classe dérivée de cette exception).</span><span class="sxs-lookup"><span data-stu-id="296ab-130">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="296ab-131">Levée par le runtime uniquement en cas d’indexation incorrecte du tableau.</span><span class="sxs-lookup"><span data-stu-id="296ab-131">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="296ab-132">Indexation d’un tableau en dehors de sa plage valide : `arr[arr.Length+1]`</span><span class="sxs-lookup"><span data-stu-id="296ab-132">Indexing an array outside its valid range: `arr[arr.Length+1]`</span></span> |
| <xref:System.NullReferenceException> | <xref:System.Exception> | <span data-ttu-id="296ab-133">Levée par le runtime uniquement si un objet Null est référencé.</span><span class="sxs-lookup"><span data-stu-id="296ab-133">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | <span data-ttu-id="296ab-134">Levée par les méthodes en cas d’état non valide.</span><span class="sxs-lookup"><span data-stu-id="296ab-134">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="296ab-135">Appel de `Enumerator.GetNext()` après la suppression d’un élément de la collection sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="296ab-135">Calling `Enumerator.GetNext()` after removing an Item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <xref:System.Exception> | <span data-ttu-id="296ab-136">Classe de base pour toutes les exceptions d’argument.</span><span class="sxs-lookup"><span data-stu-id="296ab-136">Base class for all argument exceptions.</span></span> | <span data-ttu-id="296ab-137">Aucun (utilisez une classe dérivée de cette exception).</span><span class="sxs-lookup"><span data-stu-id="296ab-137">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | <span data-ttu-id="296ab-138">Levée par les méthodes qui n’acceptent pas la valeur Null pour un argument.</span><span class="sxs-lookup"><span data-stu-id="296ab-138">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="296ab-139">Levée par les méthodes qui vérifient que les arguments sont inclus dans une plage donnée.</span><span class="sxs-lookup"><span data-stu-id="296ab-139">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="296ab-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="296ab-140">See Also</span></span>

* [<span data-ttu-id="296ab-141">Classe et propriétés d’exception</span><span class="sxs-lookup"><span data-stu-id="296ab-141">Exception Class and Properties</span></span>](exception-class-and-properties.md)
* [<span data-ttu-id="296ab-142">Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions</span><span class="sxs-lookup"><span data-stu-id="296ab-142">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [<span data-ttu-id="296ab-143">Guide pratique : utiliser des exceptions spécifiques dans un bloc Catch</span><span class="sxs-lookup"><span data-stu-id="296ab-143">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
* [<span data-ttu-id="296ab-144">Guide pratique pour lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="296ab-144">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
* [<span data-ttu-id="296ab-145">Guide pratique : créer des exceptions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="296ab-145">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
* [<span data-ttu-id="296ab-146">Utilisation de gestionnaires filtrés par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="296ab-146">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
* [<span data-ttu-id="296ab-147">Guide pratique pour utiliser des blocs Finally</span><span class="sxs-lookup"><span data-stu-id="296ab-147">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
* [<span data-ttu-id="296ab-148">Gestion des exceptions COM Interop</span><span class="sxs-lookup"><span data-stu-id="296ab-148">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
* [<span data-ttu-id="296ab-149">Meilleures pratiques pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="296ab-149">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)

<span data-ttu-id="296ab-150">Pour en savoir plus sur le fonctionnement des exceptions dans .NET, consultez [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md) (Tout ce que doit savoir un développeur sur les exceptions dans le runtime).</span><span class="sxs-lookup"><span data-stu-id="296ab-150">To learn more about how exceptions work in .NET, see [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
