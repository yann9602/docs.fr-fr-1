---
title: Constructeurs d'instances (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
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
ms.openlocfilehash: f93f622d5bf99ab7e8b1d8338192ff58472813dd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="a5b69-102">Constructeurs d'instances (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a5b69-102">Instance Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="a5b69-103">Les constructeurs d’instances sont utilisés pour créer et initialiser toutes les variables membres d’instance quand vous utilisez l’expression [new](../../../csharp/language-reference/keywords/new.md) pour créer un objet d’une [classe](../../../csharp/language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="a5b69-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../../csharp/language-reference/keywords/new.md) expression to create an object of a [class](../../../csharp/language-reference/keywords/class.md).</span></span> <span data-ttu-id="a5b69-104">Pour initialiser une classe [statique](../../../csharp/language-reference/keywords/static.md) ou des variables statiques dans une classe non statique, vous devez définir un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="a5b69-104">To initialize a [static](../../../csharp/language-reference/keywords/static.md) class, or static variables in a non-static class, you must define a static constructor.</span></span> <span data-ttu-id="a5b69-105">Pour plus d’informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="a5b69-105">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
 <span data-ttu-id="a5b69-106">L’exemple suivant présente un constructeur d’instance :</span><span class="sxs-lookup"><span data-stu-id="a5b69-106">The following example shows an instance constructor:</span></span>  
  
 <span data-ttu-id="a5b69-107">[!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-107">[!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5b69-108">Pour plus de clarté, cette classe contient des champs publics.</span><span class="sxs-lookup"><span data-stu-id="a5b69-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="a5b69-109">L’utilisation de champs publics n’est pas une pratique de programmation recommandée, car elle octroie à n’importe quelle méthode n’importe où dans un programme un accès sans restriction ni vérification aux mécanismes internes d’un objet.</span><span class="sxs-lookup"><span data-stu-id="a5b69-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="a5b69-110">Les données membres doivent généralement être privées et doivent être accessibles uniquement via les propriétés et les méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="a5b69-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="a5b69-111">Ce constructeur d’instance est appelé chaque fois qu’un objet basé sur la classe `CoOrds` est créé.</span><span class="sxs-lookup"><span data-stu-id="a5b69-111">This instance constructor is called whenever an object based on the `CoOrds` class is created.</span></span> <span data-ttu-id="a5b69-112">Un constructeur comme celui-ci, qui n’accepte aucun argument, est un *constructeur par défaut*.</span><span class="sxs-lookup"><span data-stu-id="a5b69-112">A constructor like this one, which takes no arguments, is called a *default constructor*.</span></span> <span data-ttu-id="a5b69-113">Toutefois, il est souvent utile de fournir des constructeurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="a5b69-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="a5b69-114">Par exemple, nous pouvons ajouter un constructeur à la classe `CoOrds` qui nous permet de spécifier les valeurs initiales pour les données membres :</span><span class="sxs-lookup"><span data-stu-id="a5b69-114">For example, we can add a constructor to the `CoOrds` class that allows us to specify the initial values for the data members:</span></span>  
  
 <span data-ttu-id="a5b69-115">[!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-115">[!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="a5b69-116">Cela permet de créer des objets `CoOrd` avec des valeurs par défaut ou initiales spécifiques, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5b69-116">This allows `CoOrd` objects to be created with default or specific initial values, like this:</span></span>  
  
 <span data-ttu-id="a5b69-117">[!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-117">[!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]</span></span>  
  
 <span data-ttu-id="a5b69-118">Si une classe n’a pas de constructeur, un constructeur par défaut est généré automatiquement et les valeurs par défaut sont utilisées pour initialiser les champs objet.</span><span class="sxs-lookup"><span data-stu-id="a5b69-118">If a class does not have a constructor, a default constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="a5b69-119">Par exemple, [int](../../../csharp/language-reference/keywords/int.md) est initialisé à 0.</span><span class="sxs-lookup"><span data-stu-id="a5b69-119">For example, an [int](../../../csharp/language-reference/keywords/int.md) is initialized to 0.</span></span> <span data-ttu-id="a5b69-120">Pour plus d’informations sur les valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="a5b69-120">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="a5b69-121">Par conséquent, comme le constructeur par défaut de la classe `CoOrds` initialise toutes les données membres à zéro, il peut être supprimé entièrement sans modification du fonctionnement de la classe.</span><span class="sxs-lookup"><span data-stu-id="a5b69-121">Therefore, because the `CoOrds` class default constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="a5b69-122">Un exemple complet d’utilisation de plusieurs constructeurs est fourni dans l’exemple 1, plus loin dans cette rubrique, et un exemple d’un constructeur généré automatiquement est fourni dans l’exemple 2.</span><span class="sxs-lookup"><span data-stu-id="a5b69-122">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="a5b69-123">Les constructeurs d’instances peuvent également servir à appeler les constructeurs d’instances des classes de base.</span><span class="sxs-lookup"><span data-stu-id="a5b69-123">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="a5b69-124">Le constructeur de classe peut appeler le constructeur de la classe de base via l’initialiseur, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5b69-124">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 <span data-ttu-id="a5b69-125">[!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-125">[!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]</span></span>  
  
 <span data-ttu-id="a5b69-126">Dans cet exemple, la classe `Circle` passe des valeurs représentant le rayon et la hauteur au constructeur fourni par `Shape` duquel `Circle` est dérivé.</span><span class="sxs-lookup"><span data-stu-id="a5b69-126">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="a5b69-127">Un exemple complet d’utilisation de `Shape` et `Circle` s’affiche dans cette rubrique en tant qu’exemple 3.</span><span class="sxs-lookup"><span data-stu-id="a5b69-127">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a5b69-128">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="a5b69-128">Example 1</span></span>  
 <span data-ttu-id="a5b69-129">L’exemple suivant illustre une classe avec deux constructeurs de classe, l’un sans argument et l’autre avec deux arguments.</span><span class="sxs-lookup"><span data-stu-id="a5b69-129">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 <span data-ttu-id="a5b69-130">[!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-130">[!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="a5b69-131">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="a5b69-131">Example 2</span></span>  
 <span data-ttu-id="a5b69-132">Dans cet exemple, la classe `Person` n’a aucun constructeur, auquel cas un constructeur par défaut est fourni automatiquement et les champs sont initialisés à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5b69-132">In this example, the class `Person` does not have any constructors, in which case, a default constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 <span data-ttu-id="a5b69-133">[!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-133">[!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]</span></span>  
  
 <span data-ttu-id="a5b69-134">Notez que la valeur par défaut d’`age` est `0` et que celle de `name` est `null`.</span><span class="sxs-lookup"><span data-stu-id="a5b69-134">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="a5b69-135">Pour plus d’informations sur les valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="a5b69-135">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="a5b69-136">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="a5b69-136">Example 3</span></span>  
 <span data-ttu-id="a5b69-137">L’exemple suivant illustre l’utilisation de l’initialiseur de classe de base.</span><span class="sxs-lookup"><span data-stu-id="a5b69-137">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="a5b69-138">La classe `Circle` est dérivée de la classe générale `Shape` et la classe `Cylinder` est dérivée de la classe `Circle`.</span><span class="sxs-lookup"><span data-stu-id="a5b69-138">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="a5b69-139">Le constructeur de chaque classe dérivée utilise son initialiseur de classe de base.</span><span class="sxs-lookup"><span data-stu-id="a5b69-139">The constructor on each derived class is using its base class initializer.</span></span>  
  
 <span data-ttu-id="a5b69-140">[!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="a5b69-140">[!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]</span></span>  
  
 <span data-ttu-id="a5b69-141">Pour obtenir d’autres exemples sur l’appel des constructeurs de classe de base, consultez [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md) et [base](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="a5b69-141">For more examples on invoking the base class constructors, see [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), and [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b69-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5b69-142">See Also</span></span>  
 <span data-ttu-id="a5b69-143">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5b69-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a5b69-144">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5b69-144">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="a5b69-145">[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="a5b69-145">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="a5b69-146">[Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="a5b69-146">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 [<span data-ttu-id="a5b69-147">static</span><span class="sxs-lookup"><span data-stu-id="a5b69-147">static</span></span>](../../../csharp/language-reference/keywords/static.md)

