---
title: "Quelles sont les nouveautés en c# 6 - Guide c#"
description: "Découvrez les nouvelles fonctionnalités de C# version 6"
keywords: .NET, .NET Core
author: BillWagner
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f3e7a515b1dde52461ab6abf8a9adbe84d27b7c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="ecc2b-104">Nouveautés de C# 6</span><span class="sxs-lookup"><span data-stu-id="ecc2b-104">What's New in C# 6</span></span>

<span data-ttu-id="ecc2b-105">La version Release 6.0 de C# comprenait de nombreuses fonctionnalités qui améliorent la productivité des développeurs.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-105">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="ecc2b-106">Cette version inclut les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-106">Features in this release include:</span></span>

* <span data-ttu-id="ecc2b-107">[Auto-properties en lecture seule](#read-only-auto-properties) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-107">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="ecc2b-108">Vous pouvez créer des auto-properties en lecture seule qui ne peuvent être définies que dans des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-108">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="ecc2b-109">[Initialiseurs d’auto-properties](#auto-property-initializers) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-109">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="ecc2b-110">Vous pouvez écrire des expressions d’initialisation pour définir la valeur initiale d’une auto-property.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-110">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="ecc2b-111">[Membres de fonction expression-bodied](#expression-bodied-function-members) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-111">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="ecc2b-112">Vous pouvez créer des méthodes d’une ligne à l’aide d’expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-112">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="ecc2b-113">[using static](#using-static) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-113">[using static](#using-static):</span></span>
    - <span data-ttu-id="ecc2b-114">Vous pouvez importer toutes les méthodes d’une classe unique dans l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-114">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="ecc2b-115">[Null - Opérateurs conditionnels](#null-conditional-operators) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-115">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="ecc2b-116">Vous pouvez accéder avec concision et en toute sécurité aux membres d’un objet tout en recherchant les valeurs null avec l’opérateur conditionnel null.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-116">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="ecc2b-117">[Interpolation de chaîne](#string-interpolation) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-117">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="ecc2b-118">Vous pouvez écrire des expressions de mise en forme de chaînes à l’aide d’expressions inline plutôt que d’arguments de position.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-118">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="ecc2b-119">[Filtres d’exception](#exception-filters) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-119">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="ecc2b-120">Vous pouvez intercepter des expressions en fonction de propriétés de l’exception ou de l’état d’un autre programme.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-120">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="ecc2b-121">[Expressions nameof](#nameof-expressions) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-121">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="ecc2b-122">Vous pouvez laisser le compilateur générer des représentations de symboles sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-122">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="ecc2b-123">[await dans des blocs catch et finally](#await-in-catch-and-finally-blocks) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-123">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="ecc2b-124">Vous pouvez utiliser des expressions `await` dans des emplacements qui ne les autorisaient pas auparavant.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-124">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="ecc2b-125">[Initialiseurs d’index](#index-initializers) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-125">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="ecc2b-126">Vous pouvez créer des expressions d’initialisation pour les conteneurs associatifs, ainsi que des conteneurs de séquence.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-126">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="ecc2b-127">[Méthodes d’extension pour les initialiseurs de collections](#extension-add-methods-in-collection-initializers) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-127">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="ecc2b-128">Les initialiseurs de collections peuvent s’appuyer sur des méthodes d’extension accessibles, en plus des méthodes membres.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-128">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="ecc2b-129">[Résolution de surcharge améliorée](#improved-overload-resolution) :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-129">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="ecc2b-130">Certaines constructions qui généraient auparavant des appels de méthode ambigus sont désormais résolues correctement.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-130">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="ecc2b-131">Globalement, ces fonctionnalités vous permettent d’écrire du code plus concis et également plus lisible.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-131">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="ecc2b-132">La syntaxe est moins formelle concernant de nombreuses pratiques courantes.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-132">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="ecc2b-133">Moins de formalisme permet de voir plus facilement l’intention de conception.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-133">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="ecc2b-134">En maîtrisant ces fonctionnalités, vous serez plus productif, vous écrirez du code plus lisible et vous vous concentrerez davantage sur vos fonctionnalités principales que sur les constructions du langage.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-134">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="ecc2b-135">Le reste de cette rubrique fournit des détails sur chacune de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-135">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="ecc2b-136">Améliorations des auto-properties</span><span class="sxs-lookup"><span data-stu-id="ecc2b-136">Auto-Property enhancements</span></span> 

<span data-ttu-id="ecc2b-137">La syntaxe des propriétés implémentées automatiquement (généralement appelées "auto-properties") permettait de créer très facilement des propriétés qui avaient des accesseurs get et set simples :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-137">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="ecc2b-138">Toutefois, cette syntaxe simple limitait les types de conceptions que vous pouviez prendre en charge à l’aide d’auto-properties.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-138">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="ecc2b-139">C# 6 améliore les fonctionnalités des auto-properties afin de vous permettre de les exécuter dans un plus grand nombre de scénarios.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-139">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="ecc2b-140">Vous n’aurez pas besoin de fréquemment revenir manuellement sur la syntaxe plus détaillée de la déclaration et de la manipulation du champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-140">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="ecc2b-141">La nouvelle syntaxe répond à des scénarios pour les propriétés en lecture seule et pour l’initialisation de la variable stockage derrière une propriété automatique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-141">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="ecc2b-142">Auto-properties en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ecc2b-142">Read-only auto-properties</span></span>

<span data-ttu-id="ecc2b-143">Les *auto-properties en lecture seule* offrent une syntaxe plus concise pour créer des types immuables.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-143">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="ecc2b-144">Dans les versions antérieures de C#, déclarer les méthodes Set privées permettait de vous rapprocher le plus de types immuables :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-144">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="ecc2b-145">En utilisant cette syntaxe, le compilateur ne garantit pas que le type soit vraiment immuable.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-145">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="ecc2b-146">Il garantit seulement que les propriétés `FirstName` et `LastName` ne sont pas modifiées à partir de code en dehors de la classe.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-146">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="ecc2b-147">Les auto-properties en lecture seule permettent un véritable comportement en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-147">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="ecc2b-148">Vous déclarez l’auto-property avec uniquement un accesseur get :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-148">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="ecc2b-149">Les propriétés `FirstName` et `LastName` peuvent être définies uniquement dans le corps d’un constructeur :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-149">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="ecc2b-150">Tenter de définir `LastName` dans une autre méthode génère une erreur de compilation `CS0200` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-150">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="ecc2b-151">Cette fonctionnalité permet une véritable prise en charge du langage pour la création de types immuables et l’utilisation de la syntaxe d’auto-property plus concise et plus pratique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-151">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="ecc2b-152">Initialiseurs d’auto-properties</span><span class="sxs-lookup"><span data-stu-id="ecc2b-152">Auto-Property Initializers</span></span>

<span data-ttu-id="ecc2b-153">Les *initialiseurs d’auto-properties* vous permettent de déclarer la valeur initiale d’une auto-property dans le cadre de la déclaration de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-153">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="ecc2b-154">Dans les versions antérieures, ces propriétés devaient avoir des méthodes setter que vous deviez utiliser pour initialiser le stockage de données utilisé par le champ de stockage.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-154">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="ecc2b-155">Étudions la classe suivante pour un étudiant. Elle contient le nom et la liste des diplômes de ce dernier :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-155">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="ecc2b-156">À mesure que cette classe augmente, vous pouvez inclure d’autres constructeurs.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-156">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="ecc2b-157">Chaque constructeur doit initialiser ce champ, sans quoi vous introduirez des erreurs.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-157">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="ecc2b-158">C# 6 vous permet d’assigner une valeur initiale pour le stockage utilisé par une auto-property dans la déclaration de l’auto-property :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-158">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="ecc2b-159">Le membre `Grades` est initialisé à l’emplacement où il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-159">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="ecc2b-160">Il est ainsi plus facile d’effectuer l’initialisation une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-160">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="ecc2b-161">L’initialisation fait partie de la déclaration de propriété, facilitant ainsi la mise en correspondance de l’allocation de stockage et de l’interface publique pour les objets `Student`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-161">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="ecc2b-162">Initialiseurs de propriété peuvent être utilisés avec les propriétés en lecture/écriture, ainsi que les propriétés en lecture seule, comme indiqué ici.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-162">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="ecc2b-163">Membres de fonction expression-bodied</span><span class="sxs-lookup"><span data-stu-id="ecc2b-163">Expression-bodied function members</span></span>

<span data-ttu-id="ecc2b-164">Le corps de beaucoup de membres que nous écrivons se compose d’une seule instruction qui peut être représentée sous la forme d’une expression.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-164">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="ecc2b-165">Vous pouvez réduire cette syntaxe en écrivant un membre expression-bodied à la place.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-165">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="ecc2b-166">Il fonctionne pour les méthodes et propriétés en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-166">It works for methods and read-only properties.</span></span> <span data-ttu-id="ecc2b-167">Par exemple, une substitution de `ToString()` est souvent un excellent candidat :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-167">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="ecc2b-168">Vous pouvez également utiliser des membres de l’expression-pulvérisés dans les propriétés en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-168">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="ecc2b-169">using static</span><span class="sxs-lookup"><span data-stu-id="ecc2b-169">using static</span></span>

<span data-ttu-id="ecc2b-170">L’amélioration de *using static* vous permet d’importer les méthodes statiques d’une classe unique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-170">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="ecc2b-171">Auparavant, l’instruction `using` importait tous les types d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-171">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="ecc2b-172">Souvent, nous utilisons les méthodes statiques d’une classe dans notre code.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-172">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="ecc2b-173">Saisir de manière répétée le nom de classe peut nuire à la visibilité de la signification de votre code.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-173">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="ecc2b-174">C’est souvent le cas quand vous écrivez des classes qui effectuent de nombreux calculs numériques.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-174">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="ecc2b-175">Votre code sera encombré de <xref:System.Math.Sin%2A>, de <xref:System.Math.Sqrt%2A> et d’autres appels à différentes méthodes de la classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-175">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="ecc2b-176">La nouvelle syntaxe `using static` clarifie considérablement la lecture de ces classes.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-176">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="ecc2b-177">Vous spécifiez la classe que vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-177">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="ecc2b-178">Vous pouvez maintenant utiliser n’importe quelle méthode statique de la classe <xref:System.Math> sans qualifier la classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-178">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="ecc2b-179">La classe <xref:System.Math> est un excellent cas d’usage de cette fonctionnalité, car elle ne contient aucune méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-179">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="ecc2b-180">Vous pouvez également utiliser `using static` pour importer les méthodes statiques d’une classe pour une classe qui comprend à la fois des méthodes statiques et des méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-180">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="ecc2b-181">Un des exemples plus utiles est <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="ecc2b-181">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="ecc2b-182">Vous devez utiliser le nom de classe complet, `System.String`, dans une instruction static using.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-182">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="ecc2b-183">Vous ne pouvez pas utiliser le mot clé `string` à la place.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-183">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="ecc2b-184">Vous pouvez maintenant appeler des méthodes statiques définies dans la classe <xref:System.String> sans qualifier ces méthodes comme membres de cette classe :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-184">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="ecc2b-185">La fonctionnalité `static using` et les méthodes d’extension interagissent de façons intéressantes, et la conception du langage comprenait des règles qui traitent spécifiquement ces interactions.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-185">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="ecc2b-186">L’objectif est de réduire les risques de changements importants dans des codes base existants, dont les vôtres.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-186">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="ecc2b-187">Les méthodes d’extension sont dans la portée uniquement quand elles sont appelées à l’aide de la syntaxe d’invocation de méthode d’extension, et pas quand elles sont appelées en tant que méthode statique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-187">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="ecc2b-188">Ce sera souvent le cas dans les requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-188">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="ecc2b-189">Vous pouvez importer le modèle LINQ en important <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-189">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="ecc2b-190">Cette opération importe toutes les méthodes de la classe <xref:System.Linq.Enumerable>.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-190">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="ecc2b-191">Toutefois, les méthodes d’extension sont dans la portée uniquement quand elles sont appelées en tant que méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-191">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="ecc2b-192">Elles ne sont pas dans la portée si elles sont appelées à l’aide de la syntaxe de méthode statique :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-192">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="ecc2b-193">Cette décision est justifiée par le fait que les méthodes d’extension sont généralement appelées à l’aide d’expressions d’invocation de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-193">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="ecc2b-194">Il existe de rares cas où elles sont appelées à l’aide de la syntaxe d’appel de méthode statique, dans le but de résoudre une ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-194">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="ecc2b-195">Il semble judicieux d’exiger le nom de la classe dans le cadre de l’invocation.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-195">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="ecc2b-196">`static using` comprend une dernière fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-196">There's one last feature of `static using`.</span></span> <span data-ttu-id="ecc2b-197">La directive `static using` importe également n’importe quel type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-197">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="ecc2b-198">Cela vous permet de référencer tout type imbriqué sans qualification.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-198">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="ecc2b-199">Null - Opérateurs conditionnel</span><span class="sxs-lookup"><span data-stu-id="ecc2b-199">Null-conditional operators</span></span>

<span data-ttu-id="ecc2b-200">Les valeurs null compliquent le code.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-200">Null values complicate code.</span></span> <span data-ttu-id="ecc2b-201">Vous devez vérifier chaque accès de variables afin de garantir que vous ne déréférencez pas `null`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-201">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="ecc2b-202">L’*opérateur conditionnel null* rend ces contrôles beaucoup plus faciles et plus fluides.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-202">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="ecc2b-203">Remplacez simplement l’accès aux membres `.` par `?.` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-203">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="ecc2b-204">Dans l’exemple précédent, la valeur `null` est assignée à la variable `first` si l’objet person a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-204">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="ecc2b-205">Sinon, la valeur de la propriété `FirstName` lui est assignée.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-205">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="ecc2b-206">Plus important encore, le `?.` signifie que cette ligne de code ne génère pas de `NullReferenceException` quand la variable `person` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-206">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="ecc2b-207">Au lieu de cela, elle court-circuite et produit `null`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-207">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="ecc2b-208">Notez également que cette expression retourne un `string`, quelle que soit la valeur de `person`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-208">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="ecc2b-209">Dans le cas d’un court-circuit, la valeur `null` retournée est typée pour correspondre à l’expression complète.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-209">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="ecc2b-210">Vous pouvez souvent utiliser cette construction avec l’opérateur de *fusion null*  pour assigner des valeurs par défaut quand l’une des propriétés a la valeur `null` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-210">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="ecc2b-211">L’opérande de droite de l’opérateur `?.` n’est pas limité aux propriétés ou aux champs.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-211">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="ecc2b-212">Vous pouvez également l’utiliser pour appeler des méthodes de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-212">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="ecc2b-213">L’utilisation la plus courante de fonctions membres avec l’opérateur conditionnel null consiste à appeler en toute sécurité des délégués (ou des gestionnaires d’événements) qui peuvent avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-213">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="ecc2b-214">Pour ce faire, appelez la méthode `Invoke` du délégué à l’aide de l’opérateur `?.` pour accéder au membre.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-214">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="ecc2b-215">Vous trouverez un exemple dans la rubrique relative aux</span><span class="sxs-lookup"><span data-stu-id="ecc2b-215">You can see an example in the</span></span>  
<span data-ttu-id="ecc2b-216">[modèles de délégués](../delegates-patterns.md#handling-null-delegates).</span><span class="sxs-lookup"><span data-stu-id="ecc2b-216">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="ecc2b-217">Les règles de l’opérateur `?.` garantissent que la partie gauche de l’opérateur n’est évalué qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-217">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="ecc2b-218">Cela est important et permet de nombreux idiomes, notamment l’exemple utilisant des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-218">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="ecc2b-219">Commençons par l’utilisation de gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-219">Let's start with the event handler usage.</span></span> <span data-ttu-id="ecc2b-220">Dans les précédentes versions de C#, vous étiez encouragé à écrire du code semblable à ceci :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-220">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="ecc2b-221">Cela était préférable à une syntaxe plus simple :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-221">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="ecc2b-222">L’exemple précédent introduit une concurrence critique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-222">The preceding example introduces a race condition.</span></span> <span data-ttu-id="ecc2b-223">L’événement `SomethingHappened` peut avoir des abonnés au moment où il est vérifié pour voir s’il a la valeur `null`, et ces abonnés peuvent avoir été supprimés avant le déclenchement de l’événement.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-223">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="ecc2b-224">Cela entraînerait la levée d’un <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-224">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="ecc2b-225">Dans cette deuxième version, le gestionnaire d’événements `SomethingHappened` peut être non null au moment du test, mais si un autre code supprime un gestionnaire, il peut être encore null quand le gestionnaire d’événements a été appelé.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-225">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="ecc2b-226">Le compilateur génère du code pour l’opérateur `?.` qui garantit que la partie gauche (`this.SomethingHappened`) de l’expression `?.` n’est évaluée qu’une seule fois, et le résultat est mis en cache :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-226">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="ecc2b-227">Le fait de garantir que la partie gauche n’est évaluée qu’une seule fois vous permet également d’utiliser n’importe quelle expression, notamment des appels de méthode, dans la partie gauche de l’expression `?.`. Même si ces expressions ont des effets secondaires, elles ne sont évaluées qu’une seule fois ; les effets secondaires ne se produisent donc qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-227">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="ecc2b-228">Vous trouverez un exemple dans notre contenu relatif aux [événements](../events-overview.md#language-support-for-events).</span><span class="sxs-lookup"><span data-stu-id="ecc2b-228">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="ecc2b-229">Interpolation de chaîne</span><span class="sxs-lookup"><span data-stu-id="ecc2b-229">String Interpolation</span></span>

<span data-ttu-id="ecc2b-230">C# 6 contient une nouvelle syntaxe pour la composition de chaînes à partir d’une chaîne de format et des expressions qui peuvent être évaluées pour produire d’autres valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-230">C# 6 contains new syntax for composing strings from a format string and expressions that can be evaluated to produce other string values.</span></span>

<span data-ttu-id="ecc2b-231">Habituellement, vous deviez utiliser des paramètres de position dans une méthode telle que `string.Format` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-231">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="ecc2b-232">Avec C# 6, la nouvelle fonctionnalité d’interpolation de chaîne vous permet d’incorporer des expressions dans la chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-232">With C# 6, the new string interpolation feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="ecc2b-233">Faites simplement précéder la chaîne de `$` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-233">Simple preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="ecc2b-234">Cet exemple initial utilisait des expressions variables pour les expressions substituées.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-234">This initial example used variable expressions for the substituted expressions.</span></span> <span data-ttu-id="ecc2b-235">Vous pouvez étendre cette syntaxe pour utiliser n’importe quelle expression.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-235">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="ecc2b-236">Par exemple, vous pourrez calculer la moyenne pondérée cumulative d’un étudiant dans le cadre de l’interpolation :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-236">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="ecc2b-237">En exécutant l’exemple précédent, vous pouvez voir que la sortie de `Grades.Average()` peut avoir plus de décimales que vous ne le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-237">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="ecc2b-238">La syntaxe d’interpolation de chaîne prend en charge toutes les chaînes de format disponibles en utilisant des méthodes de mise en forme précédentes.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-238">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="ecc2b-239">Vous ajoutez les chaînes de format entre les accolades.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-239">You add the format strings inside the braces.</span></span> <span data-ttu-id="ecc2b-240">Ajoutez un `:` après l’expression à mettre en forme :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-240">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="ecc2b-241">La ligne de code précédente mettra en forme la valeur de `Grades.Average()` sous la forme d’un nombre à virgule flottante à deux décimales.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-241">The preceding line of code will format the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="ecc2b-242">Le `:` est toujours interprété comme le séparateur entre l’expression mise en forme et la chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-242">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="ecc2b-243">Cela peut entraîner des problèmes quand votre expression utilise un `:` d’une autre manière, par exemple comme opérateur conditionnel :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-243">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="ecc2b-244">Dans l’exemple précédent, le `:` est analysé comme début de la chaîne de format, et non comme partie de l’opérateur conditionnel.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-244">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="ecc2b-245">Dans tous les cas où cela se produit, vous pouvez mettre l’expression entre parenthèses pour forcer le compilateur à interpréter l’expression comme vous le souhaitez :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-245">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="ecc2b-246">Aucune limite ne s’applique aux expressions que vous pouvez placer entre accolades.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-246">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="ecc2b-247">Vous pouvez exécuter une requête LINQ complexe à l’intérieur d’une chaîne interpolée pour effectuer des calculs et afficher le résultat :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-247">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="ecc2b-248">Dans cet exemple, vous pouvez voir qu’il est même possible d’imbriquer une expression d’interpolation de chaîne à l’intérieur d’une autre expression d’interpolation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-248">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="ecc2b-249">Cet exemple est très probablement plus complexe que vous ne le souhaiteriez dans le code de production.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-249">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="ecc2b-250">En fait, il illustre l’étendue de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-250">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="ecc2b-251">Toute expression C# peut être placée entre les accolades d’une chaîne interpolée.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-251">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="ecc2b-252">Interpolation de chaîne et cultures spécifiques</span><span class="sxs-lookup"><span data-stu-id="ecc2b-252">String interpolation and specific cultures</span></span>

<span data-ttu-id="ecc2b-253">Tous les exemples présentés dans la section précédente mettront en forme les chaînes à l’aide de la culture et de la langue actuelles sur l’ordinateur sur lequel le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-253">All the examples shown in the preceding section will format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="ecc2b-254">Souvent, vous devrez mettre en forme la chaîne produite à l’aide d’une culture spécifique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-254">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="ecc2b-255">L’objet créé à partir d’une interpolation de chaîne est un type qui a une conversion implicite en <xref:System.String> ou en <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-255">The object produced from a string interpolation is a type that has an implicit conversion to either <xref:System.String> or <xref:System.FormattableString>.</span></span>

<span data-ttu-id="ecc2b-256">Le type <xref:System.FormattableString> contient la chaîne de format et les résultats de l’évaluation des arguments avant leur conversion en chaînes.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-256">The <xref:System.FormattableString> type contains the format string, and the results of evaluating the arguments before converting them to strings.</span></span> <span data-ttu-id="ecc2b-257">Vous pouvez utiliser des méthodes publiques de <xref:System.FormattableString> pour spécifier la culture lors de la mise en forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-257">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="ecc2b-258">Par exemple, le code suivant produira une chaîne utilisant l’allemand comme langue et culture.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-258">For example, the following will produce a string using German as the language and culture.</span></span> <span data-ttu-id="ecc2b-259">(Il utilisera le caractère ',' comme séparateur décimal et le caractère '.' comme séparateur des milliers.)</span><span class="sxs-lookup"><span data-stu-id="ecc2b-259">(It will use the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = string.Format(null, 
    System.Globalization.CultureInfo.CreateSpecificCulture("de-de"),
    str.GetFormat(), str.GetArguments());
```

> [!NOTE]
> <span data-ttu-id="ecc2b-260">L’exemple précédent n’est pas pris en charge dans .NET Core version 1.0.1.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-260">The preceding example is not supported in .NET Core version 1.0.1.</span></span> <span data-ttu-id="ecc2b-261">Il est pris en charge uniquement dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-261">It is only supported in the .NET Framework.</span></span>

<span data-ttu-id="ecc2b-262">En général, les expressions d’interpolation de chaîne produisent des chaînes comme sortie.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-262">In general, string interpolation expressions produce strings as their output.</span></span> <span data-ttu-id="ecc2b-263">Toutefois, si vous souhaitez mieux contrôler la culture utilisée pour mettre en forme la chaîne, vous pouvez spécifier une sortie spécifique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-263">However, when you want greater control over the culture used to format the string, you can specify a specific output.</span></span>  <span data-ttu-id="ecc2b-264">S’il s’agit d’une fonctionnalité dont vous avez souvent besoin, vous pouvez créer des méthodes pratiques, comme des méthodes d’extension, pour faciliter la mise en forme simple avec des cultures spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-264">If this is a capability you often need, you can create convenience methods, as extension methods, to enable easy formatting with specific cultures.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="ecc2b-265">Filtres d’exception</span><span class="sxs-lookup"><span data-stu-id="ecc2b-265">Exception Filters</span></span>

<span data-ttu-id="ecc2b-266">Les *filtres d’exception* constituent une autre nouvelle fonctionnalité en C# 6.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-266">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="ecc2b-267">Les filtres d’exception sont des clauses qui déterminent quand une clause catch donnée doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-267">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="ecc2b-268">Si l’expression utilisée pour un filtre d’exception prend la valeur `true`, la clause catch effectue son traitement normal sur une exception.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-268">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="ecc2b-269">Si l’expression prend la valeur `false`, la clause `catch` est ignorée.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-269">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="ecc2b-270">Une de leurs utilisations consiste à examiner les informations concernant une exception pour déterminer si une clause `catch` peut la traiter :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-270">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="ecc2b-271">Le code généré par les filtres d’exception fournit de meilleures informations concernant une exception qui est levée et non traitée.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-271">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="ecc2b-272">Avant que des filtres d’exception soient ajoutés au langage, vous deviez créer du code semblable au code suivant :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-272">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="ecc2b-273">Le point où l’exception est levée change entre ces deux exemples.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-273">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="ecc2b-274">Dans le code précédent, où une clause `throw` est utilisée, toute analyse de trace de pile ou tout examen de vidages sur incident montrera que l’exception a été levée à partir de l’instruction `throw` dans votre clause catch.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-274">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="ecc2b-275">L’objet exception réel contiendra la pile des appels d’origine, mais toutes les autres informations relatives aux variables de la pile des appels entre ce point de levée et l’emplacement du point de levée d’origine ont été perdues.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-275">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="ecc2b-276">Comparez cela à la façon dont le code qui utilise un filtre d’exception est traité : l’expression de filtre d’exception prend la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-276">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="ecc2b-277">Par conséquent, l’exécution n’entre jamais dans la clause `catch`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-277">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="ecc2b-278">Étant donné que la clause `catch` ne s’exécute pas, aucun déroulement de pile n’a lieu.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-278">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="ecc2b-279">Cela signifie que l’emplacement de levée d’origine est conservé pour toutes les activités de débogage qui se produiront ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-279">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="ecc2b-280">Chaque fois que vous avez besoin d’évaluer des champs ou des propriétés d’une exception, au lieu de vous appuyer uniquement sur le type d’exception, utilisez un filtre d’exception pour conserver davantage d’informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-280">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="ecc2b-281">Une autre pratique recommandée avec des filtres d’exception consiste à les utiliser pour les routines de journalisation.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-281">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="ecc2b-282">Cette utilisation profite également de la manière dont le point de levée de l’exception est conservé quand un filtre d’exception prend la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-282">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="ecc2b-283">Une méthode de journalisation est une méthode dont l’argument est l’exception qui retourne `false` sans condition :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-283">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="ecc2b-284">Chaque fois que vous voulez journaliser une exception, vous pouvez ajouter une clause catch et utiliser cette méthode comme filtre d’exception :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-284">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="ecc2b-285">Les exceptions ne sont jamais interceptées, car la méthode `LogException` retourne toujours `false`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-285">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="ecc2b-286">Ce filtre d’exception qui a toujours la valeur false signifie que vous pouvez placer ce gestionnaire de journalisation avant tous les autres gestionnaires d’exceptions :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-286">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="ecc2b-287">L’exemple précédent met en évidence une facette très importante des filtres d’exception.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-287">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="ecc2b-288">Ces derniers autorisent les scénarios où une clause catch d’exception plus générale peut apparaître avant une clause plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-288">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="ecc2b-289">Il est également possible que le même type d’exception apparaisse dans plusieurs clauses catch :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-289">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="ecc2b-290">Une autre pratique recommandée empêche que les clauses catch traitent les exceptions quand un débogueur est attaché.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-290">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="ecc2b-291">Cette technique vous permet d’exécuter une application avec le débogueur, et d’arrêter son exécution quand une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-291">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="ecc2b-292">Dans votre code, ajoutez un filtre d’exception afin que tout code de récupération s’exécute uniquement quand un débogueur n’est pas attaché :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-292">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="ecc2b-293">Après avoir ajouté cela au code, vous configurez votre débogueur pour qu’il s’arrête sur toutes les exceptions non prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-293">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="ecc2b-294">Exécutez le programme sous le débogueur. Ce dernier s’arrête chaque fois que `PerformFailingOperation()` lève un `RecoverableException`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-294">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="ecc2b-295">Le débogueur arrête votre programme, car la clause catch ne sera pas exécutée en raison du filtre d’exception qui retourne false.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-295">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="ecc2b-296">Expressions `nameof`</span><span class="sxs-lookup"><span data-stu-id="ecc2b-296">`nameof` Expressions</span></span>

<span data-ttu-id="ecc2b-297">L’expression `nameof` prend comme valeur le nom d’un symbole.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-297">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="ecc2b-298">C’est un très bon moyen d’obtenir les outils fonctionnant chaque fois que vous avez besoin du nom d’une variable, d’une propriété ou d’un champ de membre.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-298">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="ecc2b-299">L’une des utilisations les plus courantes de `nameof` est la fourniture du nom d’un symbole qui a provoqué une exception :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-299">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="ecc2b-300">Une autre utilisation concerne les applications XAML qui implémentent l’interface `INotifyPropertyChanged` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-300">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="ecc2b-301">L’avantage d’utiliser l’opérateur `nameof` sur une chaîne constante est que les outils peuvent comprendre le symbole.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-301">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="ecc2b-302">Si vous utilisez des outils de refactorisation pour renommer le symbole, il sera renommé dans l’expression `nameof`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-302">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="ecc2b-303">Les chaînes constantes ne présentent pas cet avantage.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-303">Constant strings don't have that advantage.</span></span> <span data-ttu-id="ecc2b-304">Faites vous-même l’essai dans votre éditeur préféré : renommez une variable ; toutes les expressions `nameof` se mettront également à jour.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-304">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="ecc2b-305">L’expression `nameof` produit le nom non qualifié de son argument (`LastName` dans les exemples précédents), même si vous utilisez le nom complet de l’argument :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-305">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="ecc2b-306">Cette expression `nameof` produit `FirstName`, et non pas `UXComponents.ViewModel.FirstName`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-306">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="ecc2b-307">await dans des blocs catch et finally</span><span class="sxs-lookup"><span data-stu-id="ecc2b-307">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="ecc2b-308">C# 5 présentait plusieurs restrictions concernant les emplacements où vous pouviez placer des expressions `await`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-308">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="ecc2b-309">L’une de ces restrictions a été supprimée dans C# 6.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-309">One of those has been removed in C# 6.</span></span> <span data-ttu-id="ecc2b-310">Vous pouvez maintenant utiliser `await` dans des expressions `catch` ou `finally`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-310">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="ecc2b-311">L’ajout d’expressions await dans des blocs catch et finally peut sembler compliquer la façon dont elles sont traitées.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-311">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="ecc2b-312">Ajoutons un exemple pour étudier comment cela se présente.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-312">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="ecc2b-313">Dans n’importe quelle méthode asynchrone, vous pouvez utiliser une expression await dans une clause finally.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-313">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="ecc2b-314">Avec C# 6, vous pouvez également utiliser await dans des expressions catch.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-314">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="ecc2b-315">C’est le plus souvent le cas avec les scénarios de journalisation :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-315">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="ecc2b-316">Les informations d’implémentation détaillées de l’ajout de la prise en charge d’`await` dans des clauses `catch` et `finally` garantissent que le comportement est cohérent avec le comportement du code synchrone.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-316">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="ecc2b-317">Quand le code exécuté dans une clause `catch` ou `finally` est déclenché, l’exécution recherche une clause `catch` appropriée dans le bloc voisin suivant.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-317">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="ecc2b-318">S’il existait une exception actuelle, elle est perdue.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-318">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="ecc2b-319">Il en va de même pour les expressions await dans les clauses `catch` et `finally` : une clause `catch` appropriée est recherchée, et l’exception actuelle, le cas échéant, est perdue.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-319">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="ecc2b-320">De ce fait, il est recommandé d’écrire les clauses `catch` et `finally` avec précaution, afin d’éviter d’introduire de nouvelles exceptions.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-320">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="ecc2b-321">Initialiseurs d’index.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-321">Index Initializers</span></span>

<span data-ttu-id="ecc2b-322">Les *initialiseurs d’index* constituent l’une des deux fonctionnalités qui améliorent la cohérence des initialiseurs.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-322">*Index Initializers* is one of two features that make collection initializers more consistent.</span></span> <span data-ttu-id="ecc2b-323">Dans les versions Release précédentes de C#, vous ne pouviez utiliser des *initialiseurs de collection* qu’avec des collections de styles de séquence :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-323">In earlier releases of C#, you could use *collection initializers* only with sequence style collections:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="ecc2b-324">À présent, vous pouvez également les utiliser avec des collections <xref:System.Collections.Generic.Dictionary%602> et des types similaires :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-324">Now, you can also use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="ecc2b-325">Cette fonctionnalité signifie que les conteneurs associatifs peuvent être initialisés à l’aide d’une syntaxe similaire à ce qui a été mis en place pour les conteneurs de séquence depuis plusieurs versions.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-325">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

### <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="ecc2b-326">Méthodes `Add` d’extension dans des initialiseurs de collections</span><span class="sxs-lookup"><span data-stu-id="ecc2b-326">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="ecc2b-327">La possibilité d’utiliser une *méthode d’extension* pour la méthode `Add` constitue une autre fonctionnalité qui simplifie l’initialisation des collections.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-327">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="ecc2b-328">Elle a été ajoutée à des fins de parité avec Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-328">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="ecc2b-329">Cette fonctionnalité est particulièrement utile pour ajouter sémantiquement de nouveaux éléments quand vous avez une classe de collection personnalisée dont une méthode porte un nom différent.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-329">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="ecc2b-330">Prenons, par exemple, une collection d’étudiants telle que la suivante :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-330">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="ecc2b-331">La méthode `Enroll` ajoute un étudiant.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-331">The `Enroll` method adds a student.</span></span> <span data-ttu-id="ecc2b-332">Mais elle ne suit pas le modèle `Add`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-332">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="ecc2b-333">Dans les versions antérieures de C#, vous ne pouviez pas utiliser d’initialiseurs de collections avec un objet `Enrollment` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-333">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="ecc2b-334">C’est maintenant possible, mais uniquement si vous créez une méthode d’extension qui mappe `Add` à `Enroll` :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-334">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="ecc2b-335">En utilisant cette fonctionnalité, vous mappez toute méthode ajoutant des éléments à une collection à une méthode nommée `Add` en créant une méthode d’extension :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-335">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method:</span></span> 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a><span data-ttu-id="ecc2b-336">Résolution de surcharge améliorée</span><span class="sxs-lookup"><span data-stu-id="ecc2b-336">Improved overload resolution</span></span>

<span data-ttu-id="ecc2b-337">Il est probable que vous ne remarquerez pas cette dernière fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-337">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="ecc2b-338">La précédente version du compilateur C# pouvait trouver, dans certaines constructions, des appels de méthode impliquant des expressions lambda ambigües.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-338">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="ecc2b-339">Prenons la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-339">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="ecc2b-340">Dans les versions antérieures de C#, l’appel de cette méthode à l’aide de la syntaxe de groupe de méthodes échouait :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-340">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="ecc2b-341">Le précédent compilateur ne pouvait pas faire correctement la distinction entre `Task.Run(Action)` et `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-341">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="ecc2b-342">Dans les versions précédentes, vous deviez utiliser une expression lambda comme argument :</span><span class="sxs-lookup"><span data-stu-id="ecc2b-342">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="ecc2b-343">Le compilateur C# 6 détermine correctement que `Task.Run(Func<Task>())` constitue un meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="ecc2b-343">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>
