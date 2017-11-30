---
title: "Opérations de chaînes de base dans .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f241b99f97cad081a65fd8654169e444a1b588cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="a403b-102">Opérations de base sur les chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="a403b-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="a403b-103">Les applications répondent souvent aux utilisateurs en construisant des messages selon l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a403b-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="a403b-104">Par exemple, il n’est pas rare pour les sites web de répondre à un utilisateur qui vient de se connecter par un message d’accueil spécialisé qui inclut le nom de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a403b-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="a403b-105">Plusieurs méthodes dans les <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes permettent de construire de façon dynamique des chaînes personnalisées à afficher dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a403b-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="a403b-106">Ces méthodes vous aident également à effectuer plusieurs opérations de chaînes de base telles que la création de chaînes à partir de tableaux d’octets, la comparaison des valeurs de chaînes et la modification des chaînes existantes.</span><span class="sxs-lookup"><span data-stu-id="a403b-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a403b-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a403b-107">In This Section</span></span>  
 [<span data-ttu-id="a403b-108">Création de chaînes</span><span class="sxs-lookup"><span data-stu-id="a403b-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="a403b-109">Décrit les méthodes de base pour convertir des objets en chaînes et combiner des chaînes.</span><span class="sxs-lookup"><span data-stu-id="a403b-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="a403b-110">Suppression d'espaces et de caractères</span><span class="sxs-lookup"><span data-stu-id="a403b-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="a403b-111">Décrit comment supprimer des espaces ou des caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a403b-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="a403b-112">Remplissage de chaînes</span><span class="sxs-lookup"><span data-stu-id="a403b-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="a403b-113">Décrit comment insérer des caractères ou des espaces vides dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a403b-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="a403b-114">Comparaison de chaînes</span><span class="sxs-lookup"><span data-stu-id="a403b-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="a403b-115">Décrit comment comparer le contenu de deux ou plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="a403b-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="a403b-116">Changement de casse</span><span class="sxs-lookup"><span data-stu-id="a403b-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="a403b-117">Décrit comment modifier la casse des caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="a403b-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="a403b-118">Utilisation de la classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="a403b-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="a403b-119">Décrit comment créer et modifier des objets de chaîne dynamique avec le <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="a403b-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="a403b-120">Guide pratique pour effectuer des manipulations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="a403b-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="a403b-121">Illustre l’utilisation des opérations de chaînes de base.</span><span class="sxs-lookup"><span data-stu-id="a403b-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a403b-122">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a403b-122">Related Sections</span></span>  
 [<span data-ttu-id="a403b-123">Conversion de type dans .NET</span><span class="sxs-lookup"><span data-stu-id="a403b-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="a403b-124">Décrit comment convertir un type en un autre type.</span><span class="sxs-lookup"><span data-stu-id="a403b-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="a403b-125">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="a403b-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="a403b-126">Décrit la mise en forme des chaînes à l’aide de spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="a403b-126">Describes how to format strings using format specifiers.</span></span>
