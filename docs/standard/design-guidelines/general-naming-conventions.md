---
title: "Conventions générales d'affectation de noms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5e5c09c4db8e65d836c7afc7cb78c1f9e32bab65
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="general-naming-conventions"></a><span data-ttu-id="fd9f9-102">Conventions générales d'affectation de noms</span><span class="sxs-lookup"><span data-stu-id="fd9f9-102">General Naming Conventions</span></span>
<span data-ttu-id="fd9f9-103">Cette section décrit d’affectation de noms conventions générales relatives au choix des mots, des recommandations sur l’utilisation des abréviations et les acronymes et les recommandations sur la façon d’éviter l’utilisation de noms spécifiques au langage.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="fd9f9-104">Choix des mots</span><span class="sxs-lookup"><span data-stu-id="fd9f9-104">Word Choice</span></span>  
 <span data-ttu-id="fd9f9-105">**✓ FAIRE** choisir des noms d’identificateurs lisibles.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="fd9f9-106">Par exemple, une propriété nommée `HorizontalAlignment` est plus anglais-lisible que `AlignmentHorizontal`.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="fd9f9-107">**✓ FAIRE** privilégier la lisibilité des raisons de concision.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="fd9f9-108">Le nom de propriété `CanScrollHorizontally` est meilleure que `ScrollableX` (une référence à l’axe x).</span><span class="sxs-lookup"><span data-stu-id="fd9f9-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="fd9f9-109">**X ne sont pas** utiliser d’autres caractères non alphanumériques, des traits d’union ou des traits de soulignement.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="fd9f9-110">**X ne sont pas** utilisent une notation hongroise.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="fd9f9-111">**X Évitez** à l’aide d’identificateurs qui entrent en conflit avec les mots clés de largement utilisé des langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="fd9f9-112">En fonction de la règle 4 du Common Language Specification (CLS), tous les langages conformes doivent fournir un mécanisme qui permet d’accéder à des éléments nommés qui utilisent un mot clé de cette langue en tant qu’identificateur.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="fd9f9-113">En c#, par exemple, utilise le signe comme un mécanisme d’échappement dans ce cas @.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="fd9f9-114">Toutefois, il est toujours conseillé d’éviter les mots clés courants, car il est beaucoup plus difficile d’utiliser une méthode avec la séquence d’échappement à l’autre sans.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="fd9f9-115">À l’aide des acronymes et les abréviations</span><span class="sxs-lookup"><span data-stu-id="fd9f9-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="fd9f9-116">**X ne sont pas** utiliser des abréviations ou contractions comme faisant partie des noms d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="fd9f9-117">Par exemple, utilisez `GetWindow` plutôt que `GetWin`.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="fd9f9-118">**X ne sont pas** utiliser des acronymes ne sont pas largement reconnue et même si elles sont uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="fd9f9-119">Éviter des noms spécifiques au langage</span><span class="sxs-lookup"><span data-stu-id="fd9f9-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="fd9f9-120">**✓ FAIRE** utiliser des noms sémantiquement intéressants plutôt que des mots clés spécifiques à la langue pour les noms de type.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="fd9f9-121">Par exemple, `GetLength` est un nom plus approprié que `GetInt`.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="fd9f9-122">**✓ FAIRE** utiliser un nom de type CLR générique, plutôt que d’un nom spécifique au langage, dans les rares cas où un identificateur n’a aucune signification sémantique au-delà de son type.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="fd9f9-123">Par exemple, une méthode de conversion en <xref:System.Int64> doivent être nommés `ToInt64`, et non `ToLong` (car <xref:System.Int64> est un nom CLR pour c#-alias spécifique `long`).</span><span class="sxs-lookup"><span data-stu-id="fd9f9-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="fd9f9-124">Le tableau suivant présente plusieurs types de base de données utilisant les noms de types CLR (ainsi que les noms de types correspondants pour c#, Visual Basic et C++).</span><span class="sxs-lookup"><span data-stu-id="fd9f9-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="fd9f9-125">C#</span><span class="sxs-lookup"><span data-stu-id="fd9f9-125">C#</span></span>|<span data-ttu-id="fd9f9-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd9f9-126">Visual Basic</span></span>|<span data-ttu-id="fd9f9-127">C++</span><span class="sxs-lookup"><span data-stu-id="fd9f9-127">C++</span></span>|<span data-ttu-id="fd9f9-128">CLR</span><span class="sxs-lookup"><span data-stu-id="fd9f9-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="fd9f9-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-129">**sbyte**</span></span>|<span data-ttu-id="fd9f9-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-130">**SByte**</span></span>|<span data-ttu-id="fd9f9-131">**char**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-131">**char**</span></span>|<span data-ttu-id="fd9f9-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-132">**SByte**</span></span>|  
|<span data-ttu-id="fd9f9-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-133">**byte**</span></span>|<span data-ttu-id="fd9f9-134">**Byte**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-134">**Byte**</span></span>|<span data-ttu-id="fd9f9-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-135">**unsigned char**</span></span>|<span data-ttu-id="fd9f9-136">**Byte**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-136">**Byte**</span></span>|  
|<span data-ttu-id="fd9f9-137">**short**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-137">**short**</span></span>|<span data-ttu-id="fd9f9-138">**short**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-138">**Short**</span></span>|<span data-ttu-id="fd9f9-139">**short**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-139">**short**</span></span>|<span data-ttu-id="fd9f9-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-140">**Int16**</span></span>|  
|<span data-ttu-id="fd9f9-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-141">**ushort**</span></span>|<span data-ttu-id="fd9f9-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-142">**UInt16**</span></span>|<span data-ttu-id="fd9f9-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-143">**unsigned short**</span></span>|<span data-ttu-id="fd9f9-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-144">**UInt16**</span></span>|  
|<span data-ttu-id="fd9f9-145">**int**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-145">**int**</span></span>|<span data-ttu-id="fd9f9-146">**Integer**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-146">**Integer**</span></span>|<span data-ttu-id="fd9f9-147">**int**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-147">**int**</span></span>|<span data-ttu-id="fd9f9-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-148">**Int32**</span></span>|  
|<span data-ttu-id="fd9f9-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-149">**uint**</span></span>|<span data-ttu-id="fd9f9-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-150">**UInt32**</span></span>|<span data-ttu-id="fd9f9-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-151">**unsigned int**</span></span>|<span data-ttu-id="fd9f9-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-152">**UInt32**</span></span>|  
|<span data-ttu-id="fd9f9-153">**long**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-153">**long**</span></span>|<span data-ttu-id="fd9f9-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-154">**Long**</span></span>|<span data-ttu-id="fd9f9-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-155">**__int64**</span></span>|<span data-ttu-id="fd9f9-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-156">**Int64**</span></span>|  
|<span data-ttu-id="fd9f9-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-157">**ulong**</span></span>|<span data-ttu-id="fd9f9-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-158">**UInt64**</span></span>|<span data-ttu-id="fd9f9-159">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-159">**unsigned __int64**</span></span>|<span data-ttu-id="fd9f9-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-160">**UInt64**</span></span>|  
|<span data-ttu-id="fd9f9-161">**float**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-161">**float**</span></span>|<span data-ttu-id="fd9f9-162">**Single**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-162">**Single**</span></span>|<span data-ttu-id="fd9f9-163">**float**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-163">**float**</span></span>|<span data-ttu-id="fd9f9-164">**Single**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-164">**Single**</span></span>|  
|<span data-ttu-id="fd9f9-165">**double**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-165">**double**</span></span>|<span data-ttu-id="fd9f9-166">**Double**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-166">**Double**</span></span>|<span data-ttu-id="fd9f9-167">**double**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-167">**double**</span></span>|<span data-ttu-id="fd9f9-168">**Double**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-168">**Double**</span></span>|  
|<span data-ttu-id="fd9f9-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-169">**bool**</span></span>|<span data-ttu-id="fd9f9-170">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-170">**Boolean**</span></span>|<span data-ttu-id="fd9f9-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-171">**bool**</span></span>|<span data-ttu-id="fd9f9-172">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-172">**Boolean**</span></span>|  
|<span data-ttu-id="fd9f9-173">**char**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-173">**char**</span></span>|<span data-ttu-id="fd9f9-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-174">**Char**</span></span>|<span data-ttu-id="fd9f9-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-175">**wchar_t**</span></span>|<span data-ttu-id="fd9f9-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-176">**Char**</span></span>|  
|<span data-ttu-id="fd9f9-177">**string**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-177">**string**</span></span>|<span data-ttu-id="fd9f9-178">**String**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-178">**String**</span></span>|<span data-ttu-id="fd9f9-179">**String**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-179">**String**</span></span>|<span data-ttu-id="fd9f9-180">**String**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-180">**String**</span></span>|  
|<span data-ttu-id="fd9f9-181">**object**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-181">**object**</span></span>|<span data-ttu-id="fd9f9-182">**Objet**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-182">**Object**</span></span>|<span data-ttu-id="fd9f9-183">**Objet**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-183">**Object**</span></span>|<span data-ttu-id="fd9f9-184">**Objet**</span><span class="sxs-lookup"><span data-stu-id="fd9f9-184">**Object**</span></span>|  
  
 <span data-ttu-id="fd9f9-185">**✓ FAIRE** utiliser un nom commun, tel que `value` ou `item`, plutôt que de répéter le nom de type dans les rares cas où un identificateur n’a aucune signification sémantique et le type du paramètre n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="fd9f9-186">D’affectation de noms de nouvelles Versions d’API existantes</span><span class="sxs-lookup"><span data-stu-id="fd9f9-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="fd9f9-187">**✓ FAIRE** utiliser un nom semblable à l’ancien API lors de la création de nouvelles versions d’une API existante.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="fd9f9-188">Cela permet de mettre en évidence la relation entre les API.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="fd9f9-189">**✓ FAIRE** préférez l’ajout d’un suffixe au lieu d’un préfixe pour indiquer une nouvelle version d’une API existante.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="fd9f9-190">Cela est utile pour la détection lorsque vous parcourez la documentation, ou à l’aide d’Intellisense.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-190">This will assist discovery when browsing documentation, or using Intellisense.</span></span> <span data-ttu-id="fd9f9-191">L’ancienne version de l’API est organisée proches les nouvelles API, car la plupart des navigateurs et Intellisense affichent les identificateurs dans l’ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-191">The old version of the API will be organized close to the new APIs, because most browsers and Intellisense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="fd9f9-192">**✓ Envisagez** à l’aide d’un identificateur de tout nouveau, mais significatif, au lieu d’ajouter un préfixe ou un suffixe.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="fd9f9-193">**✓ FAIRE** un suffixe numérique permet d’indiquer une nouvelle version d’une API existante, en particulier si le nom existant de l’API est le seul nom logique (par exemple, si elle est une norme sectorielle) et si l’ajout explicite tout suffixe (ou la modification du nom) n’est pas une application option de ropriate.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="fd9f9-194">**X ne sont pas** utiliser le « Ex » (ou un texte similaire) suffixe pour un identificateur pour le distinguer d’une version antérieure de la même API.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="fd9f9-195">**✓ FAIRE** utiliser le suffixe « 64 » lorsque vous introduisez des versions d’API qui fonctionnent sur un entier 64 bits (un entier long) au lieu d’un entier 32 bits.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="fd9f9-196">Vous pouvez suivre cette approche lorsqu’il existe de l’API 32 bits existante ; ne le faites pour toute nouvelle API avec uniquement une version 64 bits.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="fd9f9-197">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="fd9f9-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fd9f9-198">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fd9f9-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9f9-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9f9-199">See Also</span></span>  
 [<span data-ttu-id="fd9f9-200">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd9f9-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="fd9f9-201">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="fd9f9-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
