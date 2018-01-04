---
title: Conventions de mise en majuscules
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b36f230c9a5f8653f3e252d26fe6464bb9cac4bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="capitalization-conventions"></a><span data-ttu-id="e52df-102">Conventions de mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="e52df-102">Capitalization Conventions</span></span>
<span data-ttu-id="e52df-103">Les instructions de cette mise en page chapitre une méthode simple pour l’utilisation de cas qui, en cas d’application constamment, assurez-vous des identificateurs pour les types, membres et paramètres faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="e52df-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="e52df-104">Règles de casse des identificateurs</span><span class="sxs-lookup"><span data-stu-id="e52df-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="e52df-105">Afin de distinguer des mots dans un identificateur, pour mettre en majuscule la première lettre de chaque mot dans l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="e52df-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="e52df-106">N’utilisez pas de traits de soulignement pour différencier des mots, ou d’ailleurs, n’importe où dans les identificateurs.</span><span class="sxs-lookup"><span data-stu-id="e52df-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="e52df-107">Il existe deux façons appropriés pour tirer profit des identificateurs, en fonction de l’utilisation de l’identificateur :</span><span class="sxs-lookup"><span data-stu-id="e52df-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="e52df-108">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="e52df-109">casse mixte</span><span class="sxs-lookup"><span data-stu-id="e52df-109">camelCasing</span></span>  
  
 <span data-ttu-id="e52df-110">La convention de casse Pascal, utilisée pour tous les identificateurs à l’exception des noms de paramètres, met en majuscule le premier caractère de chaque mot (y compris les acronymes sur les deux lettres longueur), comme indiqué dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="e52df-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="e52df-111">Un cas particulier concerne des acronymes de deux lettres correspondant à la fois des lettres sont en majuscules, comme indiqué dans l’identificateur suivant :</span><span class="sxs-lookup"><span data-stu-id="e52df-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="e52df-112">La convention de casse mixte, utilisée uniquement pour les noms de paramètres, met en majuscule le premier caractère de chaque mot, sauf le premier mot, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="e52df-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="e52df-113">Comme dans l’exemple également, les acronymes de deux lettres qui commencent un identificateur à casse mixte sont en minuscules.</span><span class="sxs-lookup"><span data-stu-id="e52df-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="e52df-114">**✓ FAIRE** utilisent la casse Pascal pour tous les noms de membre, le type et espace de noms publics constitué de plusieurs mots.</span><span class="sxs-lookup"><span data-stu-id="e52df-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="e52df-115">**✓ FAIRE** utilisez la casse mixte pour les noms de paramètre.</span><span class="sxs-lookup"><span data-stu-id="e52df-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="e52df-116">Le tableau suivant décrit les règles de mise en majuscules pour différents types d’identificateurs.</span><span class="sxs-lookup"><span data-stu-id="e52df-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="e52df-117">Identificateur</span><span class="sxs-lookup"><span data-stu-id="e52df-117">Identifier</span></span>|<span data-ttu-id="e52df-118">Casse</span><span class="sxs-lookup"><span data-stu-id="e52df-118">Casing</span></span>|<span data-ttu-id="e52df-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="e52df-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="e52df-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e52df-120">Namespace</span></span>|<span data-ttu-id="e52df-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="e52df-122">Type</span><span class="sxs-lookup"><span data-stu-id="e52df-122">Type</span></span>|<span data-ttu-id="e52df-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="e52df-124">Interface</span><span class="sxs-lookup"><span data-stu-id="e52df-124">Interface</span></span>|<span data-ttu-id="e52df-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="e52df-126">Méthode</span><span class="sxs-lookup"><span data-stu-id="e52df-126">Method</span></span>|<span data-ttu-id="e52df-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="e52df-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="e52df-128">Property</span></span>|<span data-ttu-id="e52df-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="e52df-130">événement</span><span class="sxs-lookup"><span data-stu-id="e52df-130">Event</span></span>|<span data-ttu-id="e52df-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="e52df-132">Champ</span><span class="sxs-lookup"><span data-stu-id="e52df-132">Field</span></span>|<span data-ttu-id="e52df-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="e52df-134">Valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="e52df-134">Enum value</span></span>|<span data-ttu-id="e52df-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="e52df-136">Paramètre</span><span class="sxs-lookup"><span data-stu-id="e52df-136">Parameter</span></span>|<span data-ttu-id="e52df-137">Mixte</span><span class="sxs-lookup"><span data-stu-id="e52df-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="e52df-138">Mise en majuscule de mots composés et les termes courants</span><span class="sxs-lookup"><span data-stu-id="e52df-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="e52df-139">La plupart des termes composés sont traités comme des mots isolés pour les besoins de mise en majuscules.</span><span class="sxs-lookup"><span data-stu-id="e52df-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="e52df-140">**X ne sont pas** majuscule chaque soi-disant fermé mots composés.</span><span class="sxs-lookup"><span data-stu-id="e52df-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="e52df-141">Il s’agit de mots composés écrits comme un mot unique, comme point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e52df-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="e52df-142">Les instructions de la casse, à des fins de traiter un mot composé fermé comme un mot unique.</span><span class="sxs-lookup"><span data-stu-id="e52df-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="e52df-143">Utiliser un dictionnaire actuel pour déterminer si un mot composé est écrit dans une forme fermée.</span><span class="sxs-lookup"><span data-stu-id="e52df-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="e52df-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="e52df-144">Pascal</span></span>|<span data-ttu-id="e52df-145">Mixte</span><span class="sxs-lookup"><span data-stu-id="e52df-145">Camel</span></span>|<span data-ttu-id="e52df-146">pas</span><span class="sxs-lookup"><span data-stu-id="e52df-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="e52df-147">Respect de la casse</span><span class="sxs-lookup"><span data-stu-id="e52df-147">Case Sensitivity</span></span>  
 <span data-ttu-id="e52df-148">Les langues qui peuvent s’exécuter sur le CLR ne sont pas requis pour prendre en charge le respect de la casse, bien que certains.</span><span class="sxs-lookup"><span data-stu-id="e52df-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="e52df-149">Même si votre langage prend en charge, autres langages qui peuvent accéder à votre version de framework ne le font pas.</span><span class="sxs-lookup"><span data-stu-id="e52df-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="e52df-150">Des API qui sont accessibles de l’extérieur, par conséquent, ne peut pas vous fier cas seul pour faire la distinction entre les deux noms dans le même contexte.</span><span class="sxs-lookup"><span data-stu-id="e52df-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="e52df-151">**X ne sont pas** supposent que tous les langages de programmation respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="e52df-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="e52df-152">mais ils ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="e52df-152">They are not.</span></span> <span data-ttu-id="e52df-153">Les noms ne peuvent pas différer par la casse uniquement.</span><span class="sxs-lookup"><span data-stu-id="e52df-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="e52df-154">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="e52df-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e52df-155">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e52df-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e52df-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e52df-156">See Also</span></span>  
 [<span data-ttu-id="e52df-157">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e52df-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e52df-158">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="e52df-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
