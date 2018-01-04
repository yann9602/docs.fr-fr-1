---
title: Noms de classes, de structures et d'interfaces
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c76fccec77454cb4551e427e254fe84d9a60299
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="a65ce-102">Noms de classes, de structures et d'interfaces</span><span class="sxs-lookup"><span data-stu-id="a65ce-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="a65ce-103">Les instructions d’affectation de noms qui suivent s’appliquent aux noms de type général.</span><span class="sxs-lookup"><span data-stu-id="a65ce-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="a65ce-104">**✓ FAIRE** un nom de classes et structs avec des noms ou des expressions nominales, à l’aide de la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="a65ce-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="a65ce-105">Cela permet de différencier les noms de types, ces méthodes sont nommées avec verbaux.</span><span class="sxs-lookup"><span data-stu-id="a65ce-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="a65ce-106">**✓ FAIRE** nom interfaces phrases adjectivales ou parfois avec des noms ou des expressions nominales.</span><span class="sxs-lookup"><span data-stu-id="a65ce-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="a65ce-107">Les noms et des expressions nominales doivent être utilisées rarement et ils peuvent indiquer que le type doit être une classe abstraite et pas une interface.</span><span class="sxs-lookup"><span data-stu-id="a65ce-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="a65ce-108">**X ne sont pas** donner des noms de classe un préfixe (par exemple, « C »).</span><span class="sxs-lookup"><span data-stu-id="a65ce-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="a65ce-109">**✓ Envisagez** se terminant par le nom de classes dérivées portant le nom de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="a65ce-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="a65ce-110">Cela est très lisible et explique la relation clairement.</span><span class="sxs-lookup"><span data-stu-id="a65ce-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="a65ce-111">Voici quelques exemples de ce code : `ArgumentOutOfRangeException`, qui est une sorte de `Exception`, et `SerializableAttribute`, qui est un type de `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="a65ce-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="a65ce-112">Toutefois, il est important d’utiliser les Réfléchissez soigneusement en appliquant cette indication ; par exemple, le `Button` classe est une sorte de `Control` événement, bien que `Control` n’apparaît pas dans son nom.</span><span class="sxs-lookup"><span data-stu-id="a65ce-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="a65ce-113">**✓ FAIRE** préfixe les noms d’interface avec la lettre I, pour indiquer que le type est une interface.</span><span class="sxs-lookup"><span data-stu-id="a65ce-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="a65ce-114">Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression nominale), et `IPersistable` (adjectif) sont des noms de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="a65ce-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="a65ce-115">Comme avec d’autres noms de types, évitez d’abréviations.</span><span class="sxs-lookup"><span data-stu-id="a65ce-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="a65ce-116">**✓ FAIRE** vous assurer que les noms diffèrent uniquement par « I » du préfixe du nom de l’interface lorsque vous définissez une paire : interface de classe dans laquelle la classe est une implémentation standard de l’interface.</span><span class="sxs-lookup"><span data-stu-id="a65ce-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="a65ce-117">Noms des paramètres de Type générique</span><span class="sxs-lookup"><span data-stu-id="a65ce-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="a65ce-118">Les génériques ont été ajoutés à .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a65ce-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="a65ce-119">La fonctionnalité introduit un nouveau type d’identificateur appelé *le paramètre de type*.</span><span class="sxs-lookup"><span data-stu-id="a65ce-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="a65ce-120">**✓ FAIRE** nom des paramètres de type générique avec des noms descriptifs, sauf si un nom de lettre unique est complètement explicite et un nom descriptif ajouterait pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="a65ce-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="a65ce-121">**ENVISAGEZ de ✓** à l’aide de `T` comme nom de paramètre de type pour les types avec un paramètre de type de lettre unique.</span><span class="sxs-lookup"><span data-stu-id="a65ce-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="a65ce-122">**✓ FAIRE** préfixe des noms de paramètre de type descriptifs avec `T`.</span><span class="sxs-lookup"><span data-stu-id="a65ce-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="a65ce-123">**✓ Envisagez** indiquer les contraintes placées sur un paramètre de type dans le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a65ce-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="a65ce-124">Par exemple, un paramètre contraint à `ISession` peut être appelée `TSession`.</span><span class="sxs-lookup"><span data-stu-id="a65ce-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="a65ce-125">Noms des Types courants</span><span class="sxs-lookup"><span data-stu-id="a65ce-125">Names of Common Types</span></span>  
 <span data-ttu-id="a65ce-126">**✓ FAIRE** suivez les instructions décrites dans le tableau suivant lorsque vous nommez des types dérivés ou implémenter certains types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a65ce-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="a65ce-127">Base Type</span><span class="sxs-lookup"><span data-stu-id="a65ce-127">Base Type</span></span>|<span data-ttu-id="a65ce-128">Règle de Type dérivé/de mise en œuvre</span><span class="sxs-lookup"><span data-stu-id="a65ce-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="a65ce-129">**✓ FAIRE** ajouter le suffixe « Attribute » aux noms des classes d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a65ce-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="a65ce-130">**✓ FAIRE** ajouter le suffixe « EventHandler » aux noms de délégués qui sont utilisés dans les événements.</span><span class="sxs-lookup"><span data-stu-id="a65ce-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="a65ce-131">**✓ FAIRE** ajouter le suffixe « Rappel » aux noms de délégués autres que ceux utilisés en tant que gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="a65ce-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="a65ce-132">**X ne sont pas** ajouter le suffixe « Délégué » à un délégué.</span><span class="sxs-lookup"><span data-stu-id="a65ce-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="a65ce-133">**✓ FAIRE** ajouter le suffixe « EventArgs ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="a65ce-134">**X ne sont pas** dériver de cette classe ; utilisez le mot clé pris en charge par votre langage à la place ; par exemple, en c#, utilisez le `enum` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="a65ce-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="a65ce-135">**X ne sont pas** ajouter le suffixe « Enum » ou « Indicateur ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="a65ce-136">**✓ FAIRE** ajouter le suffixe « Exception ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="a65ce-137">**✓ FAIRE** ajouter le suffixe « Dictionnaire ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="a65ce-138">Notez que `IDictionary` est un type spécifique de la collection, mais cette instruction est prioritaire sur la règle de collections plus générale qui suit.</span><span class="sxs-lookup"><span data-stu-id="a65ce-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="a65ce-139">**✓ FAIRE** ajouter le suffixe « Collection ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="a65ce-140">**✓ FAIRE** ajouter le suffixe « Stream ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="a65ce-141">**✓ FAIRE** ajouter le suffixe « Autorisation ».</span><span class="sxs-lookup"><span data-stu-id="a65ce-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="a65ce-142">Énumérations d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="a65ce-142">Naming Enumerations</span></span>  
 <span data-ttu-id="a65ce-143">Noms des types énumération (également appelés enums) en général doivent respecter les règles d’affectation de noms de type standard (casse Pascal, etc.).</span><span class="sxs-lookup"><span data-stu-id="a65ce-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="a65ce-144">Toutefois, il existe des instructions supplémentaires qui s’appliquent spécifiquement aux enums.</span><span class="sxs-lookup"><span data-stu-id="a65ce-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="a65ce-145">**✓ FAIRE** utiliser un nom de type au singulier pour une énumération, sauf si ses valeurs sont les champs de bits.</span><span class="sxs-lookup"><span data-stu-id="a65ce-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="a65ce-146">**✓ FAIRE** utiliser un nom de type au pluriel pour une énumération avec les champs de bits sous forme de valeurs, également appelés enum d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="a65ce-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="a65ce-147">**X ne sont pas** utiliser le suffixe « Enum » dans les noms de type enum.</span><span class="sxs-lookup"><span data-stu-id="a65ce-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="a65ce-148">**X ne sont pas** utiliser « Indicateur » ou tapez les noms des suffixes « Indicateurs » dans l’enum.</span><span class="sxs-lookup"><span data-stu-id="a65ce-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="a65ce-149">**X ne sont pas** utiliser un préfixe sur les noms de valeur d’énumération (par exemple, « ad » pour les énumérations ADO.), « rtf » pour les énumérations de texte enrichi, etc.</span><span class="sxs-lookup"><span data-stu-id="a65ce-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="a65ce-150">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="a65ce-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a65ce-151">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="a65ce-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65ce-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a65ce-152">See Also</span></span>  
 [<span data-ttu-id="a65ce-153">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a65ce-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="a65ce-154">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="a65ce-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
