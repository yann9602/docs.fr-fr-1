---
title: "Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7cc2563f193fba9f9e30fcdfd5ea2766be16ba63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="ccbfa-102">Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccbfa-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="ccbfa-103">Vous pouvez définir une classe à partir de laquelle vous créez des objets qui fournissent les mêmes fonctions pour des types de données différents.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="ccbfa-104">Pour cela, vous spécifiez un ou plusieurs *paramètres de type* dans la définition.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="ccbfa-105">La classe peut ensuite servir de modèle pour les objets qui utilisent différents types de données.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="ccbfa-106">Une classe définie de cette façon est appelée *classe générique*.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="ccbfa-107">L’avantage de définir une classe générique est que vous la définissez une seule fois. Votre code peut ensuite l’utiliser pour créer divers objets qui utilisent différents types de données.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="ccbfa-108">Cette approche offre de meilleures performances que la définition d’une classe avec le type `Object` .</span><span class="sxs-lookup"><span data-stu-id="ccbfa-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="ccbfa-109">En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="ccbfa-110">Pour définir une classe avec un paramètre de type</span><span class="sxs-lookup"><span data-stu-id="ccbfa-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="ccbfa-111">Définissez la classe comme vous le faites habituellement.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="ccbfa-112">Ajoutez `(Of` *typeparameter*`)` juste après le nom de classe pour spécifier un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="ccbfa-113">Si vous utilisez plusieurs paramètres de type, spécifiez-les dans une liste séparée par des virgules et mise entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="ccbfa-114">Ne répétez pas le mot clé `Of` .</span><span class="sxs-lookup"><span data-stu-id="ccbfa-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="ccbfa-115">Si votre code effectue des opérations sur un paramètre de type autre qu’une simple assignation, faites suivre ce paramètre de type d’une clause `As` pour ajouter une ou plusieurs *contraintes*.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="ccbfa-116">Une contrainte garantit que le type fourni pour ce paramètre de type remplit une exigence similaire aux exigences suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccbfa-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="ccbfa-117">Prend en charge une opération, par exemple `>`, que votre code exécute.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="ccbfa-118">Prend en charge un membre, tel qu’une méthode, auquel votre code accède.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="ccbfa-119">Expose un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="ccbfa-120">Si vous ne spécifiez pas de contraintes, votre code peut utiliser uniquement les opérations et membres qui sont pris en charge par [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="ccbfa-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="ccbfa-121">Pour plus d'informations, consultez [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="ccbfa-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="ccbfa-122">Identifiez chaque membre de classe qui doit être déclaré avec un type fourni et déclarez-le dans `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="ccbfa-123">Cela s’applique au stockage interne, aux paramètres de procédure et aux valeurs renvoyées.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="ccbfa-124">Vérifiez que votre code utilise uniquement des opérations et des méthodes qui sont prises en charge par tous les types de données qu’il peut fournir à `itemType`.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="ccbfa-125">L’exemple suivant définit une classe qui gère une liste très simple.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="ccbfa-126">Cette liste est contenue dans le tableau interne `items`. Le code utilisé peut déclarer le type de données des éléments de la liste.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="ccbfa-127">Un constructeur paramétrable permet au code utilisé de définir la limite supérieure de `items`, et le constructeur par défaut définit cette limite à 9 (sur un total de 10 éléments).</span><span class="sxs-lookup"><span data-stu-id="ccbfa-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     <span data-ttu-id="ccbfa-128">Vous pouvez déclarer une classe à partir de `simpleList` pour contenir une liste de valeurs `Integer` , une deuxième classe pour contenir une liste de valeurs `String` et une troisième classe pour contenir des valeurs `Date` .</span><span class="sxs-lookup"><span data-stu-id="ccbfa-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="ccbfa-129">À l’exception du type de données des membres de la liste, les objets créés à partir de toutes ces classes ont un comportement identique.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="ccbfa-130">L’argument de type que le code utilisé fournit à `itemType` peut être un type intrinsèque tel que `Boolean` ou `Double`, une structure, une énumération ou un type de classe, y compris l’un des types de classe définis par votre application.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="ccbfa-131">Vous pouvez tester la classe `simpleList` à l’aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="ccbfa-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ccbfa-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccbfa-132">See Also</span></span>  
 [<span data-ttu-id="ccbfa-133">Types de données</span><span class="sxs-lookup"><span data-stu-id="ccbfa-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ccbfa-134">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ccbfa-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="ccbfa-135">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="ccbfa-135">Language Independence and Language-Independent Components</span></span>](https://msdn.microsoft.com/library/12a7a7h3)  
 [<span data-ttu-id="ccbfa-136">Of</span><span class="sxs-lookup"><span data-stu-id="ccbfa-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="ccbfa-137">Liste de types</span><span class="sxs-lookup"><span data-stu-id="ccbfa-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="ccbfa-138">Guide pratique : utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="ccbfa-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="ccbfa-139">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="ccbfa-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
