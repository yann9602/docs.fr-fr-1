---
title: Indications concernant l'attribution d'un nom
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 713a11f822dd30e77e6442c0bb082a40755b1832
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-guidelines"></a><span data-ttu-id="677ec-102">Indications concernant l'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="677ec-102">Naming Guidelines</span></span>
<span data-ttu-id="677ec-103">Après un jeu cohérent de conventions d’affectation de noms dans le développement d’une infrastructure peut être une contribution importante à la facilité d’utilisation de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="677ec-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="677ec-104">Il permet à l’infrastructure être utilisé par de nombreux développeurs sur projets largement séparés.</span><span class="sxs-lookup"><span data-stu-id="677ec-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="677ec-105">Au-delà de la cohérence du formulaire, les noms d’éléments d’infrastructure doivent être compréhensible et doivent communiquer la fonction de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="677ec-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="677ec-106">L’objectif de ce chapitre est pour fournir un jeu cohérent de conventions d’affectation de noms qui aboutit à des noms qui sens immédiate aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="677ec-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="677ec-107">Bien que l’adoption de ces conventions d’affectation de noms comme indications de développement général du code entraînerait la désignation plus cohérente dans tout votre code, vous devez uniquement pour les appliquer à des API qui est exposés publiquement (publics ou protégés des types et membres, et implémenté explicitement les interfaces).</span><span class="sxs-lookup"><span data-stu-id="677ec-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="677ec-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="677ec-108">In This Section</span></span>  
 [<span data-ttu-id="677ec-109">Conventions de mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="677ec-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="677ec-110">Conventions générales de nommage</span><span class="sxs-lookup"><span data-stu-id="677ec-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="677ec-111">Noms d’assemblys et de DLL</span><span class="sxs-lookup"><span data-stu-id="677ec-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="677ec-112">Noms d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="677ec-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="677ec-113">Noms de classes, de structures et d’interfaces</span><span class="sxs-lookup"><span data-stu-id="677ec-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="677ec-114">Noms de membres de type</span><span class="sxs-lookup"><span data-stu-id="677ec-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="677ec-115">Nommage des paramètres</span><span class="sxs-lookup"><span data-stu-id="677ec-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="677ec-116">Nommage des ressources</span><span class="sxs-lookup"><span data-stu-id="677ec-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="677ec-117">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="677ec-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="677ec-118">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="677ec-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677ec-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="677ec-119">See Also</span></span>  
 [<span data-ttu-id="677ec-120">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="677ec-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
