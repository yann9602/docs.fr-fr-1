---
title: "Propriétés (Guide de programmation C#)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.properties
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 127299a617cacee15f87964a12bb3877a2586204
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="properties-c-programming-guide"></a><span data-ttu-id="8570a-102">Propriétés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8570a-102">Properties (C# Programming Guide)</span></span>

<span data-ttu-id="8570a-103">Une propriété est un membre qui fournit un mécanisme flexible pour la lecture, l'écriture ou le calcul de la valeur d'un champ privé.</span><span class="sxs-lookup"><span data-stu-id="8570a-103">A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.</span></span> <span data-ttu-id="8570a-104">Les propriétés peuvent être utilisées comme s’il s’agissait de membres de données publics, mais ce sont en fait des méthodes spéciales appelées *accesseurs*.</span><span class="sxs-lookup"><span data-stu-id="8570a-104">Properties can be used as if they are public data members, but they are actually special methods called *accessors*.</span></span> <span data-ttu-id="8570a-105">Elles permettent aux données d'être facilement accessibles tout en soutenant quand même la sécurité et la flexibilité des méthodes.</span><span class="sxs-lookup"><span data-stu-id="8570a-105">This enables data to be accessed easily and still helps promote the safety and flexibility of methods.</span></span>  

## <a name="properties-overview"></a><span data-ttu-id="8570a-106">Vue d’ensemble des propriétés</span><span class="sxs-lookup"><span data-stu-id="8570a-106">Properties overview</span></span>  
  
- <span data-ttu-id="8570a-107">Les propriétés permettent à une classe d'exposer un moyen public d'obtenir et de définir des valeurs, tout en masquant le code d'implémentation ou de vérification.</span><span class="sxs-lookup"><span data-stu-id="8570a-107">Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.</span></span>  
  
- <span data-ttu-id="8570a-108">Un accesseur de propriété [get](../../../csharp/language-reference/keywords/get.md) est utilisé pour retourner la valeur de la propriété et un accesseur de propriété [set](../../../csharp/language-reference/keywords/set.md) est utilisé pour affecter une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="8570a-108">A [get](../../../csharp/language-reference/keywords/get.md) property accessor is used to return the property value, and a [set](../../../csharp/language-reference/keywords/set.md) property accessor is used to assign a new value.</span></span> <span data-ttu-id="8570a-109">Ces accesseurs peuvent avoir différents niveaux d’accès.</span><span class="sxs-lookup"><span data-stu-id="8570a-109">These accessors can have different access levels.</span></span> <span data-ttu-id="8570a-110">Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="8570a-110">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
- <span data-ttu-id="8570a-111">Le mot clé [value](../../../csharp/language-reference/keywords/value.md) est utilisé pour définir la valeur assignée par l’accesseur `set`.</span><span class="sxs-lookup"><span data-stu-id="8570a-111">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
- <span data-ttu-id="8570a-112">Les propriétés peuvent être *en lecture-écriture* (elles ont un accesseur `get` et un accesseur `set`), *en lecture seule* (elles ont un accesseur `get`, mais pas d’accesseur `set`) ou *en écriture seule* (elles ont un accesseur `set`, mais pas d’accesseur `get`).</span><span class="sxs-lookup"><span data-stu-id="8570a-112">Properties can be *read-write* (they have both a `get` and a `set` accessor), *read-only* (they have a `get` accessor but no `set` accessor), or *write-only* (they have a `set` accessor, but no `get` accessor).</span></span> <span data-ttu-id="8570a-113">Les propriétés en écriture seule sont rares et sont généralement utilisées pour restreindre l’accès aux données sensibles.</span><span class="sxs-lookup"><span data-stu-id="8570a-113">Write-only properties are rare and are most commonly used to restrict access to sensitive data.</span></span>

- <span data-ttu-id="8570a-114">Les propriétés simples qui ne nécessitent pas de code d’accesseur personnalisé peuvent être implémentées en tant que définitions de corps d’expression ou en tant que [propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8570a-114">Simple properties that require no custom accessor code can be implemented either as expression body definitions or as [auto-implemented properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>
 
## <a name="properties-with-backing-fields"></a><span data-ttu-id="8570a-115">Propriétés avec des champs de stockage</span><span class="sxs-lookup"><span data-stu-id="8570a-115">Properties with backing fields</span></span>

<span data-ttu-id="8570a-116">Un modèle de base pour l’implémentation d’une propriété consiste à utiliser un champ de stockage privé pour définir et extraire la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="8570a-116">One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value.</span></span> <span data-ttu-id="8570a-117">L’accesseur `get` retourne la valeur du champ privé et l’accesseur `set` peut effectuer une validation des données avant d’assigner une valeur au champ privé.</span><span class="sxs-lookup"><span data-stu-id="8570a-117">The `get` accessor returns the value of the private field, and the `set` accessor may perform some data validation before assigning a value to the private field.</span></span> <span data-ttu-id="8570a-118">Les deux accesseurs peuvent également effectuer des opérations de conversion ou de calcul sur les données avant de stocker ou retourner les données.</span><span class="sxs-lookup"><span data-stu-id="8570a-118">Both accessors may also perform some conversion or computation on the data before it is stored or returned.</span></span>

<span data-ttu-id="8570a-119">L’exemple suivant illustre ce modèle.</span><span class="sxs-lookup"><span data-stu-id="8570a-119">The following example illustrates this pattern.</span></span> <span data-ttu-id="8570a-120">Dans cet exemple, la classe `TimePeriod` représente un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="8570a-120">In this example, the `TimePeriod` class represents an interval of time.</span></span> <span data-ttu-id="8570a-121">La classe stocke l’intervalle de temps en secondes, en interne, dans un champ privé nommé `seconds`.</span><span class="sxs-lookup"><span data-stu-id="8570a-121">Internally, the class stores the time interval in seconds in a private field named `seconds`.</span></span> <span data-ttu-id="8570a-122">L’utilisateur peut éventuellement spécifier l’intervalle de temps en heures à l’aide de la propriété en lecture-écriture `Hours`.</span><span class="sxs-lookup"><span data-stu-id="8570a-122">A read-write property named `Hours` allows the customer to specify the time interval in hours.</span></span> <span data-ttu-id="8570a-123">Les deux accesseurs de propriété `get` et `set` effectuent ensuite la conversion nécessaire des heures en secondes.</span><span class="sxs-lookup"><span data-stu-id="8570a-123">Both the `get` and the `set` accessors perform the necessary conversion between hours and seconds.</span></span> <span data-ttu-id="8570a-124">De plus, l’accesseur `set` valide les données et lève une exception @System.ArgumentOutOfRangeException si le nombre d’heures n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="8570a-124">In addition, the `set` accessor validates the data and throws an @System.ArgumentOutOfRangeException if the number of hours is invalid.</span></span> 
   
 <span data-ttu-id="8570a-125">[!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8570a-125">[!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="8570a-126">Définitions de corps d’expression</span><span class="sxs-lookup"><span data-stu-id="8570a-126">Expression body definitions</span></span>  

 <span data-ttu-id="8570a-127">Les accesseurs de propriété sont souvent des instructions sur une ligne qui ne font qu’assigner ou retourner le résultat d’une expression.</span><span class="sxs-lookup"><span data-stu-id="8570a-127">Property accessors often consist of single-line statements that just assign or return the result of an expression.</span></span> <span data-ttu-id="8570a-128">Vous pouvez implémenter ces propriétés en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="8570a-128">You can implement these properties as expression-bodied members.</span></span> <span data-ttu-id="8570a-129">Les définitions de corps d’expression se composent du symbole `=>` suivi de l’expression à assigner à la propriété ou à récupérer de la propriété.</span><span class="sxs-lookup"><span data-stu-id="8570a-129">Expression body definitions consist of the `=>` symbol followed by the expression to assign to or retrieve from the property.</span></span>

 <span data-ttu-id="8570a-130">À partir de C# 6, les propriétés en lecture seule peuvent implémenter l’accesseur `get` en tant que membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="8570a-130">Starting with C# 6, read-only properties can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="8570a-131">Dans ce cas, le mot clé d’accesseur `get` et le mot clé `return` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="8570a-131">In this case, neither the `get` accessor keyword nor the `return` keyword is used.</span></span> <span data-ttu-id="8570a-132">L’exemple suivant implémente la propriété en lecture seule `Name` en tant que membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="8570a-132">The following example implements the read-only `Name` property as an expression-bodied member.</span></span>

 <span data-ttu-id="8570a-133">[!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8570a-133">[!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]</span></span>  

 <span data-ttu-id="8570a-134">À partir de C# 7, l’accesseur `get` et l’accesseur `set` peuvent être implémentés en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="8570a-134">Starting with C# 7, both the `get` and the `set` accessor can be implemented as expression-bodied members.</span></span> <span data-ttu-id="8570a-135">Dans ce cas, les mots clés `get` et `set` doivent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8570a-135">In this case, the `get` and `set` keywords must be present.</span></span> <span data-ttu-id="8570a-136">L’exemple suivant illustre l’utilisation de définitions de corps d’expression pour les deux accesseurs.</span><span class="sxs-lookup"><span data-stu-id="8570a-136">The following example illustrates the use of expression body definitions for both accessors.</span></span> <span data-ttu-id="8570a-137">Notez que le mot clé `return` n’est pas utilisé avec l’accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="8570a-137">Note that the `return` keyword is not used with the `get` accessor.</span></span>
 
  <span data-ttu-id="8570a-138">[!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8570a-138">[!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]</span></span>  

## <a name="auto-implemented-properties"></a><span data-ttu-id="8570a-139">Propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="8570a-139">Auto-implemented properties</span></span>

<span data-ttu-id="8570a-140">Dans certains cas, les accesseurs de propriété `get` et `set` ne font qu’assigner une valeur à un champ de stockage, ou récupérer une valeur d’un champ de stockage, sans inclure de logique supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="8570a-140">In some cases, property `get` and `set` accessors just assign a value to or retrieve a value from a backing field without including any additional logic.</span></span> <span data-ttu-id="8570a-141">En utilisant des propriétés implémentées automatiquement, vous simplifiez votre code, tout en laissant le compilateur C# fournir le champ de stockage de manière transparente.</span><span class="sxs-lookup"><span data-stu-id="8570a-141">By using auto-implemented properties, you can simplify your code while having the C# compiler transparently provide the backing field for you.</span></span> 

<span data-ttu-id="8570a-142">Si une propriété a les accesseurs `get` et `set`, tous deux doivent être implémentés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="8570a-142">If a property has both a `get` and a `set` accessor, both must be auto-implemented.</span></span> <span data-ttu-id="8570a-143">Vous définissez une propriété implémentée automatiquement à l’aide des mots clés `get` et `set` sans fournir d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="8570a-143">You define an auto-implemented property by using the `get` and `set` keywords without providing any implementation.</span></span> <span data-ttu-id="8570a-144">L’exemple suivant est identique à l’exemple précédent, sauf qu’il utilise les propriétés implémentées automatiquement `Name` et `Price`.</span><span class="sxs-lookup"><span data-stu-id="8570a-144">The following example repeats the previous one, except that `Name` and `Price` are auto-implemented properties.</span></span> <span data-ttu-id="8570a-145">Notez que l’exemple supprime également le constructeur paramétrable pour que les objets `SaleItem` soient initialisés avec un appel au constructeur par défaut et un [initialiseur d’objet](object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="8570a-145">Note that the example also removes the parameterized constructor, so that `SaleItem` objects are now initialized with a call to the default constructor and an [object initializer](object-and-collection-initializers.md).</span></span>

  <span data-ttu-id="8570a-146">[!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="8570a-146">[!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]</span></span>  

## <a name="related-sections"></a><span data-ttu-id="8570a-147">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8570a-147">Related sections</span></span>  
  
-   [<span data-ttu-id="8570a-148">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="8570a-148">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="8570a-149">Propriétés de l’interface</span><span class="sxs-lookup"><span data-stu-id="8570a-149">Interface Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [<span data-ttu-id="8570a-150">Comparaison entre propriétés et indexeurs</span><span class="sxs-lookup"><span data-stu-id="8570a-150">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="8570a-151">Restriction d’accessibilité de l’accesseur</span><span class="sxs-lookup"><span data-stu-id="8570a-151">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [<span data-ttu-id="8570a-152">Propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="8570a-152">Auto-Implemented Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="8570a-153">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8570a-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8570a-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8570a-154">See also</span></span>
 <span data-ttu-id="8570a-155">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8570a-155">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8570a-156">[Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8570a-156">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="8570a-157">[Indexeurs](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="8570a-157">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="8570a-158">[get, mot clé](../../../csharp/language-reference/keywords/get.md)  </span><span class="sxs-lookup"><span data-stu-id="8570a-158">[get keyword](../../../csharp/language-reference/keywords/get.md)  </span></span>  
 [<span data-ttu-id="8570a-159">set, mot clé</span><span class="sxs-lookup"><span data-stu-id="8570a-159">set keyword</span></span>](../../../csharp/language-reference/keywords/set.md)    

