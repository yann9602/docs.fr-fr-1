---
title: "Conception d'énumérations"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ee73e8677ca3fd48f4bb3c94bd4e15c49a564c7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="enum-design"></a><span data-ttu-id="0ee89-102">Conception d'énumérations</span><span class="sxs-lookup"><span data-stu-id="0ee89-102">Enum Design</span></span>
<span data-ttu-id="0ee89-103">Les énumérations sont un type spécial de type valeur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="0ee89-104">Il existe deux genres d’enums : les enums enums et indicateur simples.</span><span class="sxs-lookup"><span data-stu-id="0ee89-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="0ee89-105">Les énumérations simples représentent des petits ensembles fermés de choix.</span><span class="sxs-lookup"><span data-stu-id="0ee89-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="0ee89-106">Un exemple courant de l’enum simple est un jeu de couleurs.</span><span class="sxs-lookup"><span data-stu-id="0ee89-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="0ee89-107">Les énumérations d’indicateur sont conçues pour prendre en charge les opérations de bits des valeurs enum.</span><span class="sxs-lookup"><span data-stu-id="0ee89-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="0ee89-108">Un exemple courant de l’énumération d’indicateurs est une liste d’options.</span><span class="sxs-lookup"><span data-stu-id="0ee89-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="0ee89-109">**✓ FAIRE** permet un enum de type fort aux paramètres, propriétés et retourner des valeurs qui représentent les ensembles de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0ee89-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="0ee89-110">**✓ FAIRE** sont favorables à l’aide d’un enum au lieu de constantes statiques.</span><span class="sxs-lookup"><span data-stu-id="0ee89-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="0ee89-111">**X ne sont pas** utiliser un enum pour les ensembles ouverts (par exemple, la version du système d’exploitation, les noms de vos amis, un etc.).</span><span class="sxs-lookup"><span data-stu-id="0ee89-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="0ee89-112">**X ne sont pas** fournissent des valeurs d’enum réservé qui sont destinés à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="0ee89-113">Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un stade ultérieur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="0ee89-114">Consultez [Ajout de valeurs pour les Enums](#add_value) pour plus d’informations sur l’ajout de valeurs pour les enums.</span><span class="sxs-lookup"><span data-stu-id="0ee89-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="0ee89-115">Valeurs réservées simplement pollue pas l’ensemble de valeurs réelles et sont susceptibles d’entraîner des erreurs de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="0ee89-116">**X Évitez** exposer publiquement des énumérations avec une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="0ee89-117">Une pratique courante pour assurer une extensibilité future d’API C consiste à ajouter des paramètres réservés pour les signatures de méthode.</span><span class="sxs-lookup"><span data-stu-id="0ee89-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="0ee89-118">Ces paramètres réservés peuvent être exprimées comme les enums avec une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ee89-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="0ee89-119">Cela ne doit pas être effectuée dans les API managées.</span><span class="sxs-lookup"><span data-stu-id="0ee89-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="0ee89-120">La surcharge de méthode permet d’ajouter des paramètres dans les futures versions.</span><span class="sxs-lookup"><span data-stu-id="0ee89-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="0ee89-121">**X ne sont pas** inclure des valeurs de sentinelle dans les énumérations.</span><span class="sxs-lookup"><span data-stu-id="0ee89-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="0ee89-122">Même s’ils sont parfois utiles aux développeurs de framework, les valeurs de sentinelle sont source de confusion pour les utilisateurs de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="0ee89-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="0ee89-123">Ils sont utilisés pour suivre l’état de l’enum plutôt que d’être l’une des valeurs à partir de l’ensemble représenté par l’énumération.</span><span class="sxs-lookup"><span data-stu-id="0ee89-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="0ee89-124">**✓ FAIRE** fournir une valeur de zéro sur les énumérations simples.</span><span class="sxs-lookup"><span data-stu-id="0ee89-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="0ee89-125">La valeur, appelez quelque chose comme « None ».</span><span class="sxs-lookup"><span data-stu-id="0ee89-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="0ee89-126">Si une telle valeur n’est pas appropriée pour cet enum particulier, la valeur par défaut plus courante pour l’énumération doit avoir la valeur sous-jacente égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="0ee89-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="0ee89-127">**✓ Envisagez** à l’aide de <xref:System.Int32> (la valeur par défaut dans la plupart des langages de programmation) en tant que le type sous-jacent d’une énumération, sauf si une des opérations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="0ee89-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="0ee89-128">L’enum est un enum et que vous disposez de plus de 32 indicateurs ou est censé avoir plus d’informations à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="0ee89-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="0ee89-129">Le type sous-jacent doit être différent de celui <xref:System.Int32> pour simplifier l’interopérabilité avec du code non managé attendu enums de taille différente.</span><span class="sxs-lookup"><span data-stu-id="0ee89-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="0ee89-130">Un type sous-jacent plus petit entraînerait des économies substantielles en espace.</span><span class="sxs-lookup"><span data-stu-id="0ee89-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="0ee89-131">Si vous pensez que l’énumération sera principalement utilisée comme argument d’un flux de contrôle, la taille importe peu.</span><span class="sxs-lookup"><span data-stu-id="0ee89-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="0ee89-132">Les économies de taille peuvent être importantes si :</span><span class="sxs-lookup"><span data-stu-id="0ee89-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="0ee89-133">Vous vous attendez l’enum à utiliser en tant que champ dans une structure très fréquemment instanciée ou une classe.</span><span class="sxs-lookup"><span data-stu-id="0ee89-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="0ee89-134">Vous pensez que les utilisateurs à créer des tableaux volumineux ou des collections d’instances de l’enum.</span><span class="sxs-lookup"><span data-stu-id="0ee89-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="0ee89-135">Vous prévoyez un grand nombre d’instances de l’enum doit être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="0ee89-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="0ee89-136">Pour l’utilisation de mémoire, gardez à l’esprit que les objets managés sont toujours `DWORD`-alignés, vous devez efficacement plusieurs énumérations ou autres structures de petite dans une instance compresser un enum plus petit avec afin de faire la différence, car la taille du nombre total d’instances est toujours continue à être arrondi à un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="0ee89-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="0ee89-137">**✓ FAIRE** nommer les énumérations d’indicateur avec des noms au pluriel ou des expressions nominales et énumérations simples avec des noms au singulier ou des expressions nominales.</span><span class="sxs-lookup"><span data-stu-id="0ee89-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="0ee89-138">**X ne sont pas** étendre <xref:System.Enum?displayProperty=nameWithType> directement.</span><span class="sxs-lookup"><span data-stu-id="0ee89-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="0ee89-139"><xref:System.Enum?displayProperty=nameWithType>est un type spécial utilisé par le CLR pour créer des énumérations de défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="0ee89-140">La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0ee89-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="0ee89-141">Par exemple, en c# le `enum` est utilisé pour définir une énumération.</span><span class="sxs-lookup"><span data-stu-id="0ee89-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="0ee89-142">Conception énumérations d’indicateur</span><span class="sxs-lookup"><span data-stu-id="0ee89-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="0ee89-143">**✓ FAIRE** appliquer le <xref:System.FlagsAttribute?displayProperty=nameWithType> pour les énumérations d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="0ee89-144">N’appliquez pas cet attribut pour les énumérations simples.</span><span class="sxs-lookup"><span data-stu-id="0ee89-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="0ee89-145">**✓ FAIRE** utiliser des puissances de deux pour les valeurs d’énumération indicateur afin qu’ils peuvent être combinés librement à l’aide de l’opération OR au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="0ee89-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="0ee89-146">**✓ Envisagez** fournissant des valeurs enum spécial pour couramment utilisé les combinaisons d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="0ee89-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="0ee89-147">Opérations de bits sont un concept avancé et ne doivent pas être requises pour les tâches simples.</span><span class="sxs-lookup"><span data-stu-id="0ee89-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="0ee89-148"><xref:System.IO.FileAccess.ReadWrite>est un exemple d’une telle valeur spéciale.</span><span class="sxs-lookup"><span data-stu-id="0ee89-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="0ee89-149">**X Évitez** création enums indicateur où certaines combinaisons de valeurs ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="0ee89-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="0ee89-150">**X Évitez** à l’aide de valeurs de l’indicateur enum de zéro, sauf si la valeur représente « tous les indicateurs sont effacés » et est nommée de façon appropriée, comme indiqué par l’instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="0ee89-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="0ee89-151">**✓ FAIRE** nom de la valeur zéro des énumérations d’indicateur `None`.</span><span class="sxs-lookup"><span data-stu-id="0ee89-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="0ee89-152">Pour une énumération d’indicateur, la valeur doit toujours signifier « tous les indicateurs sont effacés. »</span><span class="sxs-lookup"><span data-stu-id="0ee89-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="0ee89-153">L’ajout de valeur pour les Enums</span><span class="sxs-lookup"><span data-stu-id="0ee89-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="0ee89-154">Il est très courant pour découvrir que vous devez ajouter des valeurs à une énumération une fois que vous l’avez déjà expédié.</span><span class="sxs-lookup"><span data-stu-id="0ee89-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="0ee89-155">A un problème de compatibilité d’application potentiel la valeur nouvellement ajoutée est retournée à partir d’une API existante, car des applications mal écrites peut ne pas gérer correctement la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="0ee89-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="0ee89-156">**✓ Envisagez** Ajout de valeurs pour les enums, en dépit d’un léger risque de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="0ee89-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="0ee89-157">Si vous avez des données réelles concernant les incompatibilités application dus à des ajouts à un enum, envisagez d’ajouter une nouvelle API qui renvoie les valeurs anciennes et nouvelles et désapprouver l’ancien API, ce qui doit continuer à retourner uniquement les anciennes valeurs.</span><span class="sxs-lookup"><span data-stu-id="0ee89-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="0ee89-158">Cela garantit que vos applications existantes restent compatibles.</span><span class="sxs-lookup"><span data-stu-id="0ee89-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="0ee89-159">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="0ee89-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0ee89-160">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0ee89-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee89-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ee89-161">See Also</span></span>  
 [<span data-ttu-id="0ee89-162">Instructions pour la conception des types</span><span class="sxs-lookup"><span data-stu-id="0ee89-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="0ee89-163">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ee89-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
