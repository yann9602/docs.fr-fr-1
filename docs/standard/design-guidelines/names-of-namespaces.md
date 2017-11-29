---
title: Noms d'espaces de noms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fc0cb9183fde33887a3e84bb30cc3f79892586e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-namespaces"></a><span data-ttu-id="04ab8-102">Noms d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="04ab8-102">Names of Namespaces</span></span>
<span data-ttu-id="04ab8-103">Comme avec les autres instructions d’affectation de noms, l’objectif lorsque vous nommez des espaces de noms consiste à créer suffisamment claire pour le programmeur immédiatement savoir ce que le contenu de l’espace de noms est susceptible d’être à l’aide de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="04ab8-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="04ab8-104">Le modèle suivant spécifie la règle générale pour nommer les espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="04ab8-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="04ab8-105">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="04ab8-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="04ab8-106">**✓ FAIRE** faites précéder les noms d’espace de noms avec un nom de société pour empêcher les espaces de noms provenant de différentes sociétés de ne pas avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="04ab8-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="04ab8-107">**✓ FAIRE** utiliser un nom de produit indépendant de la version stable au deuxième niveau d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="04ab8-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="04ab8-108">**X ne sont pas** utiliser des hiérarchies d’organisation comme base pour les noms dans les hiérarchies de l’espace de noms, étant donné que les noms de groupe au sein des entreprises ont tendance à être de courte durée de vie.</span><span class="sxs-lookup"><span data-stu-id="04ab8-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="04ab8-109">Organiser la hiérarchie d’espaces de noms autour des groupes des technologies connexes.</span><span class="sxs-lookup"><span data-stu-id="04ab8-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="04ab8-110">**✓ FAIRE** utilisent la casse Pascal et des composants de l’espace de noms distinct avec des périodes (par exemple, `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="04ab8-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="04ab8-111">Si votre marque utilise une casse non traditionnel, vous devez suivre la casse définie par votre marque, même s’il diffère de casse de l’espace de noms normal.</span><span class="sxs-lookup"><span data-stu-id="04ab8-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="04ab8-112">**✓ Envisagez** à l’aide de noms au pluriel, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="04ab8-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="04ab8-113">Par exemple, utilisez `System.Collections` au lieu de `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="04ab8-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="04ab8-114">Les marques et les acronymes sont toutefois des exceptions à cette règle.</span><span class="sxs-lookup"><span data-stu-id="04ab8-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="04ab8-115">Par exemple, utilisez `System.IO` au lieu de `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="04ab8-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="04ab8-116">**X ne sont pas** utiliser le même nom pour un espace de noms et un type dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="04ab8-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="04ab8-117">Par exemple, n’utilisez pas `Debug` comme un espace de noms nommer et puis fournissent également une classe nommée `Debug` dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="04ab8-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="04ab8-118">Plusieurs compilateurs exigent de tels types qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="04ab8-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="04ab8-119">Espaces de noms et le nom de Type est en conflit</span><span class="sxs-lookup"><span data-stu-id="04ab8-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="04ab8-120">**X ne sont pas** présentent des noms de type générique comme `Element`, `Node`, `Log`, et `Message`.</span><span class="sxs-lookup"><span data-stu-id="04ab8-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="04ab8-121">Il est fort probable que cela entraîne le nom de type est en conflit en commun des scénarios.</span><span class="sxs-lookup"><span data-stu-id="04ab8-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="04ab8-122">Vous devez qualifier les noms de type générique (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="04ab8-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="04ab8-123">Il existe des recommandations spécifiques pour éviter les conflits de nom de type pour différentes catégories d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="04ab8-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="04ab8-124">**Noms de modèle d’application**</span><span class="sxs-lookup"><span data-stu-id="04ab8-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="04ab8-125">Espaces de noms appartenant à un modèle d’application unique sont très souvent utilisés ensemble, mais ils sont presque jamais avec les espaces de noms des autres modèles d’application.</span><span class="sxs-lookup"><span data-stu-id="04ab8-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="04ab8-126">Par exemple, le <xref:System.Windows.Forms?displayProperty=nameWithType> espace de noms est très rarement utilisée conjointement avec la <xref:System.Web.UI?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="04ab8-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="04ab8-127">Voici une liste connue modèle espace de noms de groupes d’applications :</span><span class="sxs-lookup"><span data-stu-id="04ab8-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="04ab8-128">**X ne sont pas** donner le même nom aux types dans les espaces de noms dans un modèle d’application unique.</span><span class="sxs-lookup"><span data-stu-id="04ab8-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="04ab8-129">Par exemple, n’ajoutez pas d’un type nommé `Page` à la <xref:System.Web.UI.Adapters?displayProperty=nameWithType> espace de noms, étant donné que la <xref:System.Web.UI?displayProperty=nameWithType> espace de noms contient déjà un type nommé `Page`.</span><span class="sxs-lookup"><span data-stu-id="04ab8-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="04ab8-130">**Espaces de noms infrastructure**</span><span class="sxs-lookup"><span data-stu-id="04ab8-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="04ab8-131">Ce groupe contient des espaces de noms qui sont rarement importés pendant le développement d’applications courantes.</span><span class="sxs-lookup"><span data-stu-id="04ab8-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="04ab8-132">Par exemple, `.Design` espaces de noms sont utilisés principalement lorsque les outils de développement de programmation.</span><span class="sxs-lookup"><span data-stu-id="04ab8-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="04ab8-133">Éviter les conflits avec les types dans ces espaces de noms n’est pas critique.</span><span class="sxs-lookup"><span data-stu-id="04ab8-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="04ab8-134">**Espaces de noms principaux**</span><span class="sxs-lookup"><span data-stu-id="04ab8-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="04ab8-135">Espaces de noms principaux incluent tous les `System` espaces de noms, à l’exclusion des espaces de noms des modèles d’application et les espaces de noms d’Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="04ab8-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="04ab8-136">Espaces de noms principaux incluent, entre autres, `System`, `System.IO`, `System.Xml`, et `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="04ab8-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="04ab8-137">**X ne sont pas** permettent de types de noms qui sont en conflit avec un type dans les espaces de noms de base.</span><span class="sxs-lookup"><span data-stu-id="04ab8-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="04ab8-138">Par exemple, n’utilisez jamais `Stream` comme nom de type.</span><span class="sxs-lookup"><span data-stu-id="04ab8-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="04ab8-139">Elle serait en conflit avec <xref:System.IO.Stream?displayProperty=nameWithType>, une très courants de type.</span><span class="sxs-lookup"><span data-stu-id="04ab8-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="04ab8-140">**Groupes d’espace de noms de technologie**</span><span class="sxs-lookup"><span data-stu-id="04ab8-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="04ab8-141">Cette catégorie comprend tous les espaces de noms avec les deux premiers nœuds d’espace de noms même `(<Company>.<Technology>*`), tel que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="04ab8-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="04ab8-142">Il est important que les types appartenant à une technologie unique ne sont pas en conflit entre eux.</span><span class="sxs-lookup"><span data-stu-id="04ab8-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="04ab8-143">**X ne sont pas** affecter des noms de type qui sont en conflit avec d’autres types au sein d’une seule technologie.</span><span class="sxs-lookup"><span data-stu-id="04ab8-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="04ab8-144">**X ne sont pas** présentent des conflits de nom de type entre les types dans les espaces de noms de technologie et un espace de noms de modèle d’application (à moins que la technologie n’est pas destinée à être utilisée avec le modèle d’application).</span><span class="sxs-lookup"><span data-stu-id="04ab8-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="04ab8-145">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="04ab8-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="04ab8-146">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="04ab8-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ab8-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04ab8-147">See Also</span></span>  
 [<span data-ttu-id="04ab8-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="04ab8-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="04ab8-149">Affectation de noms</span><span class="sxs-lookup"><span data-stu-id="04ab8-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
