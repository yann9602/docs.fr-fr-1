---
title: Constructeurs (guide de programmation C#)
ms.date: 2017-05-05
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 400afcda2fe30bf0e3621ee4c4247486e01d3ee4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="60289-102">Constructeurs (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="60289-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="60289-103">Chaque fois qu’une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) est créé, son constructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="60289-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="60289-104">Une classe ou un struct peut avoir plusieurs constructeurs qui prennent des arguments différents.</span><span class="sxs-lookup"><span data-stu-id="60289-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="60289-105">Les constructeurs permettent au programmeur de définir des valeurs par défaut, de limiter l’instanciation et d’écrire un code flexible et facile à lire.</span><span class="sxs-lookup"><span data-stu-id="60289-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="60289-106">Pour obtenir plus d’informations et d’exemples, consultez [Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) et [Constructeurs d’instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="60289-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="60289-107">Constructeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="60289-107">Default constructors</span></span>
  
<span data-ttu-id="60289-108">Si vous ne fournissez pas de constructeur pour votre classe, C# en crée un par défaut qui instancie l’objet et affecte aux variables membres les valeurs par défaut listées dans le [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="60289-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="60289-109">Si vous ne fournissez pas de constructeur pour votre struct, C# s’appuie sur un *constructeur par défaut implicite* pour initialiser automatiquement chaque champ d’un type valeur à sa valeur par défaut listée dans le [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="60289-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="60289-110">Pour obtenir plus d’informations et d’exemples, consultez [Constructeurs d’instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="60289-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="60289-111">Syntaxe du constructeur</span><span class="sxs-lookup"><span data-stu-id="60289-111">Constructor syntax</span></span>

<span data-ttu-id="60289-112">Un constructeur est une méthode dont le nom est le même que celui de son type.</span><span class="sxs-lookup"><span data-stu-id="60289-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="60289-113">Sa signature de méthode inclut uniquement le nom de la méthode et sa liste de paramètres ; elle n’inclut pas de type de retour.</span><span class="sxs-lookup"><span data-stu-id="60289-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="60289-114">L’exemple suivant affiche le constructeur d’une classe nommée `Person`.</span><span class="sxs-lookup"><span data-stu-id="60289-114">The following example shows the constructor for a class named `Person`.</span></span>

<span data-ttu-id="60289-115">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="60289-115">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]</span></span>  

<span data-ttu-id="60289-116">Si un constructeur peut être implémenté comme une seule instruction, vous pouvez utiliser une [définition de corps d’expression](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="60289-116">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="60289-117">L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*.</span><span class="sxs-lookup"><span data-stu-id="60289-117">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="60289-118">La définition de corps d’expression assigne l’argument au champ `locationName`.</span><span class="sxs-lookup"><span data-stu-id="60289-118">The expression body definition assigns the argument to the `locationName` field.</span></span>

<span data-ttu-id="60289-119">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="60289-119">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

## <a name="static-constructors"></a><span data-ttu-id="60289-120">Constructeurs statiques</span><span class="sxs-lookup"><span data-stu-id="60289-120">Static constructors</span></span>

<span data-ttu-id="60289-121">Les exemples précédents ont tous montré des constructeurs d’instances qui permettent de créer un objet.</span><span class="sxs-lookup"><span data-stu-id="60289-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="60289-122">Une classe ou un struct peut également avoir un constructeur statique qui initialise les membres statiques du type.</span><span class="sxs-lookup"><span data-stu-id="60289-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="60289-123">Les constructeurs statiques sont sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="60289-123">Static constructors are parameterless.</span></span> <span data-ttu-id="60289-124">Si vous ne fournissez pas de constructeur statique pour initialiser les champs statiques, le compilateur C# fournit un constructeur statique par défaut qui initialise les champs statiques à leur valeur par défaut listée dans le [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="60289-124">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="60289-125">L’exemple suivant utilise un constructeur statique pour initialiser un champ statique.</span><span class="sxs-lookup"><span data-stu-id="60289-125">The following example uses a static constructor to initialize a static field.</span></span>

<span data-ttu-id="60289-126">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="60289-126">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]</span></span>  

<span data-ttu-id="60289-127">Vous pouvez également définir un constructeur statique avec une définition de corps d’expression, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="60289-127">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

<span data-ttu-id="60289-128">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="60289-128">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]</span></span>  

<span data-ttu-id="60289-129">Pour obtenir plus d’informations et d’exemples, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="60289-129">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60289-130">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="60289-130">In This Section</span></span>  
 [<span data-ttu-id="60289-131">Utilisation de constructeurs</span><span class="sxs-lookup"><span data-stu-id="60289-131">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="60289-132">Constructeurs d’instances</span><span class="sxs-lookup"><span data-stu-id="60289-132">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="60289-133">Constructeurs privés</span><span class="sxs-lookup"><span data-stu-id="60289-133">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="60289-134">Constructeurs statiques</span><span class="sxs-lookup"><span data-stu-id="60289-134">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="60289-135">Guide pratique pour écrire un constructeur de copie</span><span class="sxs-lookup"><span data-stu-id="60289-135">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="60289-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60289-136">See Also</span></span>  
 <span data-ttu-id="60289-137">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="60289-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="60289-138">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="60289-138">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="60289-139">[Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="60289-139">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 <span data-ttu-id="60289-140">[static](../../../csharp/language-reference/keywords/static.md) </span><span class="sxs-lookup"><span data-stu-id="60289-140">[static](../../../csharp/language-reference/keywords/static.md) </span></span>  
 [<span data-ttu-id="60289-141">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span><span class="sxs-lookup"><span data-stu-id="60289-141">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112374)

