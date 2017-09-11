---
title: "Propriétés"
description: "En savoir plus sur les propriétés C#, notamment les fonctionnalités liées à la validation, les valeurs calculées, l’évaluation différée et les notifications de modification de propriété."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e5d2d5d7074678383243e687d4b469606007e585
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="properties"></a><span data-ttu-id="8a62c-104">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8a62c-104">Properties</span></span>

<span data-ttu-id="8a62c-105">Les propriétés sont des éléments de première classe dans C#.</span><span class="sxs-lookup"><span data-stu-id="8a62c-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="8a62c-106">Le langage définit la syntaxe que les développeurs utilisent pour écrire du code qui exprime leur intention de conception avec précision.</span><span class="sxs-lookup"><span data-stu-id="8a62c-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="8a62c-107">Les propriétés auxquelles le code accède se comportent comme des champs.</span><span class="sxs-lookup"><span data-stu-id="8a62c-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="8a62c-108">Toutefois, contrairement aux champs, les propriétés sont implémentées avec des accesseurs qui définissent quelles instructions sont exécutées au moment de l’accès à une propriété ou de son assignation.</span><span class="sxs-lookup"><span data-stu-id="8a62c-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="8a62c-109">Syntaxe des propriétés</span><span class="sxs-lookup"><span data-stu-id="8a62c-109">Property Syntax</span></span>

<span data-ttu-id="8a62c-110">La syntaxe des propriétés est une extension naturelle des champs.</span><span class="sxs-lookup"><span data-stu-id="8a62c-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="8a62c-111">Un champ définit un emplacement de stockage :</span><span class="sxs-lookup"><span data-stu-id="8a62c-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-112">Une définition de propriété contient les déclarations de l’accesseur `get`, qui récupère la valeur de cette propriété, et de l’accesseur `set`, qui assigne cette valeur :</span><span class="sxs-lookup"><span data-stu-id="8a62c-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-113">La syntaxe illustrée ci-dessus est la syntaxe *auto property*.</span><span class="sxs-lookup"><span data-stu-id="8a62c-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="8a62c-114">Le compilateur génère l’emplacement de stockage pour le champ qui enregistre la propriété.</span><span class="sxs-lookup"><span data-stu-id="8a62c-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="8a62c-115">Le compilateur implémente également le corps des accesseurs `get` et `set`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="8a62c-116">Parfois, vous devez initialiser une propriété sur une valeur autre que la valeur par défaut pour son type.</span><span class="sxs-lookup"><span data-stu-id="8a62c-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="8a62c-117">C# permet cette opération en définissant une valeur après l’accolade fermante de la propriété.</span><span class="sxs-lookup"><span data-stu-id="8a62c-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="8a62c-118">Vous pouvez choisir comme valeur initiale pour la propriété `FirstName` une chaîne vide au lieu de `null`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="8a62c-119">Vous pouvez le spécifier comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="8a62c-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-120">Cela est très utile pour les propriétés en lecture seule, comme vous le verrez plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8a62c-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="8a62c-121">Vous pouvez aussi définir le stockage vous-même, de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="8a62c-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-122">Quand une implémentation de propriété est une expression unique, vous pouvez utiliser des *membres expression-bodied* pour l’accesseur Get ou Set :</span><span class="sxs-lookup"><span data-stu-id="8a62c-122">When a property implementation is a single expression, you can use *expression bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-123">Cette syntaxe simplifiée est utilisée partout où elle est applicable dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8a62c-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="8a62c-124">La définition de propriété présentée ci-dessus est une propriété en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="8a62c-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="8a62c-125">Notez la présence du mot clé `value` dans l’accesseur set.</span><span class="sxs-lookup"><span data-stu-id="8a62c-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="8a62c-126">L’accesseur `set` a toujours un seul paramètre nommé `value`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="8a62c-127">L’accesseur `get` doit retourner une valeur convertible dans le type de la propriété (`string`, dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="8a62c-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="8a62c-128">Nous venons de voir les éléments de base de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8a62c-128">That's the basics of the syntax.</span></span> <span data-ttu-id="8a62c-129">Il existe beaucoup de variantes de cette syntaxe, qui sont adaptées aux différents idiomes de conception.</span><span class="sxs-lookup"><span data-stu-id="8a62c-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="8a62c-130">Nous allons explorer ces variantes et découvrir les options syntaxiques de chacune.</span><span class="sxs-lookup"><span data-stu-id="8a62c-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="8a62c-131">Scénarios</span><span class="sxs-lookup"><span data-stu-id="8a62c-131">Scenarios</span></span>

<span data-ttu-id="8a62c-132">Les exemples ci-dessus ont montré un des cas les plus simples de définition de propriété, à savoir une propriété en lecture-écriture sans validation.</span><span class="sxs-lookup"><span data-stu-id="8a62c-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="8a62c-133">En écrivant le code souhaité dans les accesseurs `get` et `set`, vous pouvez créer de nombreux scénarios différents.</span><span class="sxs-lookup"><span data-stu-id="8a62c-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="8a62c-134">Validation</span><span class="sxs-lookup"><span data-stu-id="8a62c-134">Validation</span></span>

<span data-ttu-id="8a62c-135">Vous pouvez écrire du code dans l’accesseur `set` pour garantir que les valeurs représentées par une propriété sont toujours valides.</span><span class="sxs-lookup"><span data-stu-id="8a62c-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="8a62c-136">Par exemple, définissez une règle pour la classe `Person` qui spécifie que le nom ne peut pas être vide, ni contenir d’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="8a62c-136">For example, suppose one rule for the `Person` class is that the name cannot be blank, or whitespace.</span></span> <span data-ttu-id="8a62c-137">Le code à écrire est le suivant :</span><span class="sxs-lookup"><span data-stu-id="8a62c-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-138">L’exemple ci-dessus applique la règle selon laquelle le nom ne doit pas être vide, ni contenir d’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="8a62c-138">The example above enforces the rule that the first name must not be blank, or whitespace.</span></span> <span data-ttu-id="8a62c-139">Supposons qu’un développeur écrive cette ligne de code :</span><span class="sxs-lookup"><span data-stu-id="8a62c-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="8a62c-140">Cette assignation lève une exception `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="8a62c-141">Étant donné qu’un accesseur set de propriété doit avoir un type de retour void, vous signalez les erreurs dans l’accesseur set en levant une exception.</span><span class="sxs-lookup"><span data-stu-id="8a62c-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="8a62c-142">Ceci est un cas simple de validation.</span><span class="sxs-lookup"><span data-stu-id="8a62c-142">That is a simple case of validation.</span></span> <span data-ttu-id="8a62c-143">Vous pouvez employer cette même syntaxe pour valider d’autres éléments dans votre scénario.</span><span class="sxs-lookup"><span data-stu-id="8a62c-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="8a62c-144">Vous pouvez notamment vérifier les relations entre plusieurs propriétés ou effectuer une validation par rapport à des conditions externes.</span><span class="sxs-lookup"><span data-stu-id="8a62c-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="8a62c-145">Toute instruction C# valide peut être utilisée dans un accesseur de propriété.</span><span class="sxs-lookup"><span data-stu-id="8a62c-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="8a62c-146">Propriétés en lecture seule</span><span class="sxs-lookup"><span data-stu-id="8a62c-146">Read-only</span></span>

<span data-ttu-id="8a62c-147">Jusqu’ici, nous avons vu uniquement des définitions de propriétés qui sont en lecture-écriture dans des accesseurs publics.</span><span class="sxs-lookup"><span data-stu-id="8a62c-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="8a62c-148">Ce n’est pas la seule accessibilité valide pour les propriétés.</span><span class="sxs-lookup"><span data-stu-id="8a62c-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="8a62c-149">Vous pouvez créer des propriétés en lecture seule, ou assigner une accessibilité différente aux accesseurs set et get.</span><span class="sxs-lookup"><span data-stu-id="8a62c-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="8a62c-150">Supposons que votre classe `Person` doit uniquement autoriser la modification de la valeur de la propriété `FirstName` à partir des autres méthodes de cette classe.</span><span class="sxs-lookup"><span data-stu-id="8a62c-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="8a62c-151">Vous pouvez alors assigner l’accessibilité `private` au lieu de `public` à l’accesseur set :</span><span class="sxs-lookup"><span data-stu-id="8a62c-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-152">À présent, la propriété `FirstName` est accessible à partir de n’importe quel code, mais elle peut uniquement être assignée à partir de code dans la classe `Person`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="8a62c-153">Vous pouvez ajouter n’importe quel modificateur d’accès restrictif à l’accesseur set ou get.</span><span class="sxs-lookup"><span data-stu-id="8a62c-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="8a62c-154">Le modificateur d’accès que vous ajoutez à un accesseur doit être plus restrictif que le modificateur d’accès spécifié dans la définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="8a62c-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="8a62c-155">Le code ci-dessus est autorisé, car la propriété `FirstName` est `public`, mais l’accesseur set est `private`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="8a62c-156">En revanche, vous ne pouvez pas déclarer une propriété `private` avec un accesseur `public`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="8a62c-157">Les propriétés peuvent également être déclarées comme `protected`, `internal`, `protected internal` ou même `private`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-157">Property declarations can also be declared `protected`, `internal`, `protected internal` or even `private`.</span></span>   

<span data-ttu-id="8a62c-158">Placer le modificateur le plus restrictif sur l’accesseur `get` est également autorisé.</span><span class="sxs-lookup"><span data-stu-id="8a62c-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="8a62c-159">Par exemple, vous pouvez avoir une propriété `public`, mais restreindre l’accesseur `get` à `private`.</span><span class="sxs-lookup"><span data-stu-id="8a62c-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="8a62c-160">Ce scénario s’observe rarement dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="8a62c-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="8a62c-161">Vous pouvez également limiter les modifications apportées à une propriété pour qu’elle puisse uniquement être définie dans un constructeur ou un initialiseur de propriété.</span><span class="sxs-lookup"><span data-stu-id="8a62c-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="8a62c-162">Vous pouvez modifier la classe `Person`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="8a62c-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-163">Cette fonctionnalité est généralement utilisée pour initialiser des collections qui sont exposées sous forme de propriétés en lecture seule :</span><span class="sxs-lookup"><span data-stu-id="8a62c-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="8a62c-164">Propriétés calculées</span><span class="sxs-lookup"><span data-stu-id="8a62c-164">Computed Properties</span></span>

<span data-ttu-id="8a62c-165">Une propriété peut faire plus que simplement retourner la valeur d’un champ de membre.</span><span class="sxs-lookup"><span data-stu-id="8a62c-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="8a62c-166">Vous pouvez créer des propriétés qui retournent une valeur calculée.</span><span class="sxs-lookup"><span data-stu-id="8a62c-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="8a62c-167">L’objet `Person` est étendu pour retourner le nom complet, calculé en concaténant le nom et le prénom :</span><span class="sxs-lookup"><span data-stu-id="8a62c-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="8a62c-168">L’exemple ci-dessus utilise la syntaxe d’*interpolation de chaîne* pour créer la chaîne mise en forme du nom complet.</span><span class="sxs-lookup"><span data-stu-id="8a62c-168">The example above uses the *String Interpolation* syntax to create the formatted string for the full name.</span></span>

<span data-ttu-id="8a62c-169">Vous pouvez également utiliser des *membres expression-bodied*, qui constituent un moyen plus succinct de créer la propriété `FullName` calculée :</span><span class="sxs-lookup"><span data-stu-id="8a62c-169">You can also use *Expression-bodied Members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="8a62c-170">Les *membres expression-bodied* utilisent la syntaxe des *expressions lambda* pour définir une méthode qui contient une expression unique.</span><span class="sxs-lookup"><span data-stu-id="8a62c-170">*Expression-bodied Members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="8a62c-171">Ici, cette expression retourne le nom complet de l’objet person.</span><span class="sxs-lookup"><span data-stu-id="8a62c-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="8a62c-172">Propriétés à évaluation différée</span><span class="sxs-lookup"><span data-stu-id="8a62c-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="8a62c-173">Vous pouvez combiner le concept d’une propriété calculée avec le stockage pour créer une *propriété à évaluation différée*.</span><span class="sxs-lookup"><span data-stu-id="8a62c-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="8a62c-174">Par exemple, vous pouvez mettre à jour la propriété `FullName` pour que la chaîne soit mise en forme uniquement lors du premier accès à cette propriété :</span><span class="sxs-lookup"><span data-stu-id="8a62c-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="8a62c-175">Le code ci-dessus contient toutefois un bogue.</span><span class="sxs-lookup"><span data-stu-id="8a62c-175">The above code contains a bug though.</span></span> <span data-ttu-id="8a62c-176">Si le code met à jour la valeur de la propriété `FirstName` ou `LastName`, le champ `fullName` qui a été précédemment évalué n’est plus valide.</span><span class="sxs-lookup"><span data-stu-id="8a62c-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="8a62c-177">Vous devez donc mettre à jour les accesseurs `set` des propriétés `FirstName` et `LastName` pour que le champ `fullName` soit recalculé :</span><span class="sxs-lookup"><span data-stu-id="8a62c-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="8a62c-178">Dans cette version finale du code, la propriété `FullName` est évaluée uniquement si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8a62c-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="8a62c-179">Si la version précédemment calculée est valide, elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8a62c-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="8a62c-180">Si elle n’est plus valide en raison d’un changement d’état, la version est recalculée.</span><span class="sxs-lookup"><span data-stu-id="8a62c-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="8a62c-181">Les développeurs peuvent utiliser cette classe sans connaître les détails de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="8a62c-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="8a62c-182">Ces modifications internes n’ont pas d’impact sur l’utilisation de l’objet Person.</span><span class="sxs-lookup"><span data-stu-id="8a62c-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="8a62c-183">C’est l’un des principaux avantages d’utiliser des propriétés pour exposer les membres de données d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8a62c-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="8a62c-184">Interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="8a62c-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="8a62c-185">Il existe un dernier scénario où vous devrez écrire du code dans un accesseur de propriété : pour prendre en charge l’interface `INotifyPropertyChanged`, qui notifie les changements de valeurs aux clients de liaison de données.</span><span class="sxs-lookup"><span data-stu-id="8a62c-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="8a62c-186">Quand la valeur d’une propriété change, l’objet déclenche l’événement `PropertyChanged` pour signaler le changement.</span><span class="sxs-lookup"><span data-stu-id="8a62c-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="8a62c-187">Les bibliothèques de liaison de données mettent ensuite à jour les éléments d’affichage en fonction de cette modification.</span><span class="sxs-lookup"><span data-stu-id="8a62c-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="8a62c-188">Le code ci-dessous montre comment implémenter `INotifyPropertyChanged` pour la propriété `FirstName` de la classe Person.</span><span class="sxs-lookup"><span data-stu-id="8a62c-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="8a62c-189">L’opérateur `?.` est appelé *opérateur conditionnel Null*.</span><span class="sxs-lookup"><span data-stu-id="8a62c-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="8a62c-190">Il recherche une référence null avant d’évaluer le côté droit de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="8a62c-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="8a62c-191">Au final, s’il n’y a pas d’abonné à l’événement `PropertyChanged`, le code devant déclencher l’événement n’est pas exécuté.</span><span class="sxs-lookup"><span data-stu-id="8a62c-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="8a62c-192">Dans ce cas précis, il lèverait une exception `NullReferenceException` sans cette vérification.</span><span class="sxs-lookup"><span data-stu-id="8a62c-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="8a62c-193">Pour plus d’informations, consultez la page [`events`](delegates-events.md).</span><span class="sxs-lookup"><span data-stu-id="8a62c-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="8a62c-194">Cet exemple utilise également le nouvel opérateur `nameof` pour convertir le symbole de nom de propriété en sa représentation textuelle.</span><span class="sxs-lookup"><span data-stu-id="8a62c-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="8a62c-195">L’utilisation de `nameof` peut vous éviter des erreurs dues à la saisie incorrecte du nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="8a62c-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="8a62c-196">Là encore, il s’agit d’un exemple de cas où vous pouvez écrire du code dans vos accesseurs pour prendre en charge les scénarios souhaités.</span><span class="sxs-lookup"><span data-stu-id="8a62c-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="8a62c-197">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="8a62c-197">Summing up</span></span>

<span data-ttu-id="8a62c-198">Les propriétés sont une forme de champs intelligents dans une classe ou un objet.</span><span class="sxs-lookup"><span data-stu-id="8a62c-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="8a62c-199">De l’extérieur de l’objet, elles apparaissent sous la forme de champs dans l’objet.</span><span class="sxs-lookup"><span data-stu-id="8a62c-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="8a62c-200">Toutefois, les propriétés peuvent être implémentées avec toutes les fonctionnalités C#.</span><span class="sxs-lookup"><span data-stu-id="8a62c-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="8a62c-201">Vous pouvez écrire du code qui remplit les exigences de validation, d’accessibilité, d’évaluation différée ou toute autre exigence requise dans vos scénarios.</span><span class="sxs-lookup"><span data-stu-id="8a62c-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>

