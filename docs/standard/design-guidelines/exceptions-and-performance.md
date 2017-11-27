---
title: Exceptions et performances
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c2d7cfcb228c492d2adbe614d0ed88a3b02bb68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="e1c0f-102">Exceptions et performances</span><span class="sxs-lookup"><span data-stu-id="e1c0f-102">Exceptions and Performance</span></span>
<span data-ttu-id="e1c0f-103">Un problème courant lié aux exceptions est que si les exceptions sont utilisées pour le code qui échoue régulièrement, les performances de l’implémentation sera inacceptable.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="e1c0f-104">Il s’agit d’un problème valid.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-104">This is a valid concern.</span></span> <span data-ttu-id="e1c0f-105">Lorsqu’un membre lève une exception, ses performances peuvent être beaucoup plus lent.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="e1c0f-106">Toutefois, il est possible d’obtenir de bonnes performances tout en respectant strictement les instructions de l’exception interdire l’utilisation de codes d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="e1c0f-107">Deux modèles sont décrites dans cette section proposent des solutions pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="e1c0f-108">**X ne sont pas** utiliser des codes d’erreur en raison de problèmes qu’exceptions peuvent affecter négativement les performances.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="e1c0f-109">Pour améliorer les performances, il est possible d’utiliser le modèle utilisateur testeur ou le modèle d’analyse de Try, décrites dans les deux sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="e1c0f-110">Modèle de l’exécuteur de testeur</span><span class="sxs-lookup"><span data-stu-id="e1c0f-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="e1c0f-111">Parfois, les performances d’un membre de la levée d’exceptions peuvent être améliorées en divisant le membre en deux.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="e1c0f-112">Examinons le <xref:System.Collections.Generic.ICollection%601.Add%2A> méthode de la <xref:System.Collections.Generic.ICollection%601> interface.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="e1c0f-113">La méthode `Add` lève si la collection est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="e1c0f-114">Cela peut poser un problème de performances dans les scénarios où l’appel de méthode est censé échouent souvent.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="e1c0f-115">Un des moyens d’atténuer ce problème consiste à vérifier si la collection est accessible en écriture avant d’essayer d’ajouter une valeur.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="e1c0f-116">Le membre utilisé pour tester une condition qui, dans notre exemple, est la propriété `IsReadOnly`, est appelé par le testeur.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="e1c0f-117">Le membre utilisé pour effectuer une opération potentiellement levée d’exceptions, la `Add` méthode dans notre exemple, est appelé l’exécuteur.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="e1c0f-118">**✓ Envisagez** le modèle utilisateur testeur pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="e1c0f-119">Essayez de l’analyse de modèle</span><span class="sxs-lookup"><span data-stu-id="e1c0f-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="e1c0f-120">Pour les API de très sensibles aux performances, un modèle plus rapide que le modèle utilisateur testeur décrites dans la section précédente doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="e1c0f-121">Le modèle appelle pour ajuster le nom de membre pour effectuer un test bien défini de cas une partie de la sémantique de membre.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="e1c0f-122">Par exemple, <xref:System.DateTime> définit un <xref:System.DateTime.Parse%2A> méthode qui lève une exception en cas de l’analyse d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="e1c0f-123">Il définit également un correspondant <xref:System.DateTime.TryParse%2A> méthode qui tente d’analyser, mais retourne la valeur false si l’analyse échoue et retourne le résultat d’une analyse réussie à l’aide un `out` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="e1c0f-124">Lorsque vous utilisez ce modèle, il est important de définir la fonctionnalité de try en termes de stricts.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="e1c0f-125">Si le membre échoue pour une raison quelconque autre que le bloc try bien défini, le membre doit lève toujours une exception correspondante.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="e1c0f-126">**✓ Envisagez** le modèle d’analyse de Try pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="e1c0f-127">**✓ FAIRE** utilisent le préfixe « Try » et la valeur booléenne de type de retour pour les méthodes d’implémentation de ce schéma.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="e1c0f-128">**✓ FAIRE** fournissent un membre levant des exceptions pour chaque membre de l’utilisation du modèle d’analyse de Try.</span><span class="sxs-lookup"><span data-stu-id="e1c0f-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="e1c0f-129">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="e1c0f-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e1c0f-130">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e1c0f-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c0f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c0f-131">See Also</span></span>  
 [<span data-ttu-id="e1c0f-132">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e1c0f-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e1c0f-133">Règles de conception pour les Exceptions</span><span class="sxs-lookup"><span data-stu-id="e1c0f-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
