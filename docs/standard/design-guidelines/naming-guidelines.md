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
ms.openlocfilehash: 40da7449c88eaaba92e34374c002c7e175b2ef16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="naming-guidelines"></a><span data-ttu-id="4c54f-102">Indications concernant l'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="4c54f-102">Naming Guidelines</span></span>
<span data-ttu-id="4c54f-103">Après un jeu cohérent de conventions d’affectation de noms dans le développement d’une infrastructure peut être une contribution importante à la facilité d’utilisation de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="4c54f-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="4c54f-104">Il permet à l’infrastructure être utilisé par de nombreux développeurs sur projets largement séparés.</span><span class="sxs-lookup"><span data-stu-id="4c54f-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="4c54f-105">Au-delà de la cohérence du formulaire, les noms d’éléments d’infrastructure doivent être compréhensible et doivent communiquer la fonction de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="4c54f-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="4c54f-106">L’objectif de ce chapitre est pour fournir un jeu cohérent de conventions d’affectation de noms qui aboutit à des noms qui sens immédiate aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="4c54f-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="4c54f-107">Bien que l’adoption de ces conventions d’affectation de noms comme indications de développement général du code entraînerait la désignation plus cohérente dans tout votre code, vous devez uniquement pour les appliquer à des API qui est exposés publiquement (publics ou protégés des types et membres, et implémenté explicitement les interfaces).</span><span class="sxs-lookup"><span data-stu-id="4c54f-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c54f-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4c54f-108">In This Section</span></span>  
 [<span data-ttu-id="4c54f-109">Conventions de mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="4c54f-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="4c54f-110">Conventions d’affectation de noms générales</span><span class="sxs-lookup"><span data-stu-id="4c54f-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="4c54f-111">Noms des assemblys et des DLL</span><span class="sxs-lookup"><span data-stu-id="4c54f-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="4c54f-112">Noms d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="4c54f-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="4c54f-113">Noms de Classes, structures et Interfaces</span><span class="sxs-lookup"><span data-stu-id="4c54f-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="4c54f-114">Noms des membres de Type</span><span class="sxs-lookup"><span data-stu-id="4c54f-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="4c54f-115">Paramètres d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="4c54f-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="4c54f-116">Ressources d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="4c54f-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="4c54f-117">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="4c54f-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4c54f-118">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="4c54f-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c54f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c54f-119">See Also</span></span>  
 [<span data-ttu-id="4c54f-120">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c54f-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
