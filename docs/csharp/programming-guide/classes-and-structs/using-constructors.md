---
title: Utilisation de constructeurs (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
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
ms.openlocfilehash: 75b55fde2fbd1697aed7eb0665a571c63b9b0b42
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="7014f-102">Utilisation de constructeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7014f-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="7014f-103">Quand une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) est créé, son constructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="7014f-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="7014f-104">Les constructeurs portent le même nom que la classe ou le struct, et ils initialisent généralement les membres de données du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="7014f-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="7014f-105">Dans l’exemple suivant, une classe nommée `Taxi` est définie en utilisant un constructeur simple.</span><span class="sxs-lookup"><span data-stu-id="7014f-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="7014f-106">Cette classe est ensuite instanciée à l’aide de l’opérateur [new](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="7014f-107">Le constructeur `Taxi` est appelé par l’opérateur `new` immédiatement après l’allocation de la mémoire pour le nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="7014f-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 <span data-ttu-id="7014f-108">[!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-108">[!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="7014f-109">Un constructeur qui ne prend pas de paramètres est appelé *constructeur par défaut*.</span><span class="sxs-lookup"><span data-stu-id="7014f-109">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="7014f-110">Les constructeurs par défaut sont appelés chaque fois qu’un objet est instancié à l’aide de l’opérateur `new` et qu’aucun argument n’est fourni à `new`.</span><span class="sxs-lookup"><span data-stu-id="7014f-110">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="7014f-111">Pour plus d’informations, consultez [Constructeurs d’instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-111">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="7014f-112">À moins que la classe soit [statique](../../../csharp/language-reference/keywords/static.md), les classes sans constructeurs se voient attribuer un constructeur public par défaut par le compilateur C# pour activer l’instanciation de classe.</span><span class="sxs-lookup"><span data-stu-id="7014f-112">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="7014f-113">Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-113">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="7014f-114">Vous pouvez empêcher qu’une classe soit instanciée en rendant le constructeur privé, comme suit :</span><span class="sxs-lookup"><span data-stu-id="7014f-114">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 <span data-ttu-id="7014f-115">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-115">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="7014f-116">Pour plus d’informations, consultez [Constructeurs privés](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-116">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="7014f-117">Les constructeurs pour les types [struct](../../../csharp/language-reference/keywords/struct.md) ressemblent aux constructeurs de classe, mais les `structs` ne peuvent pas contenir de constructeur par défaut explicite, car le compilateur en fournit automatiquement un.</span><span class="sxs-lookup"><span data-stu-id="7014f-117">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="7014f-118">Ce constructeur initialise chaque champ du `struct` aux valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="7014f-118">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="7014f-119">Pour plus d’informations, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-119">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="7014f-120">Toutefois, ce constructeur par défaut est appelé uniquement si le `struct` est instancié avec `new`.</span><span class="sxs-lookup"><span data-stu-id="7014f-120">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="7014f-121">Par exemple, ce code utilise le constructeur par défaut pour <xref:System.Int32>. Vous êtes par conséquent assuré que l’entier est initialisé :</span><span class="sxs-lookup"><span data-stu-id="7014f-121">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="7014f-122">Toutefois, le code suivant provoque une erreur de compilateur, car il n’utilise pas `new` et il essaie d’utiliser un objet qui n’a pas été initialisé :</span><span class="sxs-lookup"><span data-stu-id="7014f-122">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="7014f-123">Les objets basés sur des `structs` (notamment tous les types numériques intégrés) peuvent également être initialisés ou assignés, puis utilisés, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7014f-123">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="7014f-124">Ainsi, l’appel du constructeur par défaut pour un type valeur n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7014f-124">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="7014f-125">Les classes et les `structs` peuvent tous les deux définir des constructeurs qui prennent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="7014f-125">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="7014f-126">Les constructeurs qui prennent des paramètres doivent être appelés à l’aide d’une instruction `new` ou d’une instruction [base](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-126">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="7014f-127">Les classes et les `structs` peuvent également définir plusieurs constructeurs, et ni l’un ni l’autre n’est nécessaire pour définir un constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7014f-127">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="7014f-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7014f-128">For example:</span></span>  
  
 <span data-ttu-id="7014f-129">[!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-129">[!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]</span></span>  
  
 <span data-ttu-id="7014f-130">Cette classe peut être créée à l’aide de l’une ou l’autre des instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="7014f-130">This class can be created by using either of the following statements:</span></span>  
  
 <span data-ttu-id="7014f-131">[!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-131">[!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]</span></span>  
  
 <span data-ttu-id="7014f-132">Un constructeur peut utiliser le mot clé `base` pour appeler le constructeur d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="7014f-132">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="7014f-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7014f-133">For example:</span></span>  
  
 <span data-ttu-id="7014f-134">[!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-134">[!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]</span></span>  
  
 <span data-ttu-id="7014f-135">Dans cet exemple, le constructeur de la classe de base est appelé avant que le bloc du constructeur ne soit exécuté.</span><span class="sxs-lookup"><span data-stu-id="7014f-135">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="7014f-136">Le mot clé `base` peut être utilisé avec ou sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="7014f-136">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="7014f-137">Tous les paramètres du constructeur peuvent être utilisés comme paramètres pour `base` ou comme partie d’une expression.</span><span class="sxs-lookup"><span data-stu-id="7014f-137">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="7014f-138">Pour plus d’informations, consultez [base](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-138">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="7014f-139">Dans une classe dérivée, si un constructeur de classe de base n’est pas appelé explicitement à l’aide du mot clé `base`, le constructeur par défaut, s’il existe, est appelé implicitement.</span><span class="sxs-lookup"><span data-stu-id="7014f-139">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="7014f-140">Cela signifie que les déclarations de constructeur suivantes sont en fait les mêmes :</span><span class="sxs-lookup"><span data-stu-id="7014f-140">This means that the following constructor declarations are effectively the same:</span></span>  
  
 <span data-ttu-id="7014f-141">[!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-141">[!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]</span></span>  
  
 <span data-ttu-id="7014f-142">[!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-142">[!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]</span></span>  
  
 <span data-ttu-id="7014f-143">Si une classe de base n’offre pas de constructeur par défaut, la classe dérivée doit faire un appel explicite à un constructeur de base à l’aide du mot clé `base`.</span><span class="sxs-lookup"><span data-stu-id="7014f-143">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="7014f-144">Un constructeur peut appeler un autre constructeur dans le même objet à l’aide du mot clé [this](../../../csharp/language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-144">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="7014f-145">Comme `base`, `this` peut être utilisé avec ou sans paramètres, et tous les paramètres dans le constructeur sont disponibles comme paramètres pour `this` ou comme partie d’une expression.</span><span class="sxs-lookup"><span data-stu-id="7014f-145">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="7014f-146">Par exemple, le deuxième constructeur de l’exemple précédent peut être récrit à l’aide de `this` :</span><span class="sxs-lookup"><span data-stu-id="7014f-146">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 <span data-ttu-id="7014f-147">[!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-147">[!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]</span></span>  
  
 <span data-ttu-id="7014f-148">L’utilisation du mot clé `this` dans l’exemple précédent provoque l’appel de ce constructeur :</span><span class="sxs-lookup"><span data-stu-id="7014f-148">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 <span data-ttu-id="7014f-149">[!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="7014f-149">[!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]</span></span>  
  
 <span data-ttu-id="7014f-150">Les constructeurs peuvent être marqués comme [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="7014f-150">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="7014f-151">Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent construire la classe.</span><span class="sxs-lookup"><span data-stu-id="7014f-151">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="7014f-152">Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-152">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="7014f-153">Un constructeur peut être déclaré statique à l’aide du mot clé [static](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-153">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="7014f-154">Les constructeurs statiques sont appelés automatiquement, juste avant que des champs statiques soient accessibles, et ils sont généralement utilisés pour initialiser des membres de classe statique.</span><span class="sxs-lookup"><span data-stu-id="7014f-154">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="7014f-155">Pour plus d’informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="7014f-155">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7014f-156">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="7014f-156">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7014f-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7014f-157">See Also</span></span>  
 <span data-ttu-id="7014f-158">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7014f-158">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7014f-159">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="7014f-159">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="7014f-160">[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="7014f-160">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 [<span data-ttu-id="7014f-161">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="7014f-161">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

