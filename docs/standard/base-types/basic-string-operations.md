---
title: "Opérations de chaînes de base"
description: "Opérations de chaînes de base"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9658098d-de60-4868-ba5b-0c278748a90f
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: b8bdbeccd226c412e725200fcaf81ec568afc5bc
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="basic-string-operations"></a><span data-ttu-id="d246f-104">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="d246f-104">Basic string operations</span></span>

<span data-ttu-id="d246f-105">Les applications répondent souvent aux utilisateurs en construisant des messages selon l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d246f-105">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="d246f-106">Par exemple, il n’est pas rare pour les sites web de répondre à un utilisateur qui vient de se connecter par un message d’accueil spécialisé qui inclut le nom de cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d246f-106">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="d246f-107">Plusieurs méthodes dans les classes [System.String](xref:System.String) et [System.Text.StringBuilder](xref:System.Text.StringBuilder) vous permettent de construire de façon dynamique des chaînes personnalisées à afficher dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d246f-107">Several methods in the [System.String](xref:System.String) and [System.Text.StringBuilder](xref:System.Text.StringBuilder) classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="d246f-108">Ces méthodes vous aident également à effectuer plusieurs opérations de chaînes de base telles que la création de chaînes à partir de tableaux d’octets, la comparaison des valeurs de chaînes et la modification des chaînes existantes.</span><span class="sxs-lookup"><span data-stu-id="d246f-108">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d246f-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d246f-109">In This Section</span></span>

<span data-ttu-id="d246f-110">[Création de chaînes](creating-new.md) : décrit les manières basiques de convertir des objets en chaînes et de combiner des chaînes.</span><span class="sxs-lookup"><span data-stu-id="d246f-110">[Creating new strings](creating-new.md) - Describes basic ways to convert objects into strings and to combine strings.</span></span>

<span data-ttu-id="d246f-111">[Suppression d’espaces et de caractères](trimming.md) : décrit la manière de supprimer des caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d246f-111">[Trimming and removing characters](trimming.md) - Describes how to trim or remove characters in a string.</span></span> 

<span data-ttu-id="d246f-112">[Remplissage de chaînes](padding.md) : décrit la manière d’insérer des caractères ou des espaces vides dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d246f-112">[Padding strings](padding.md) - Describes how to insert characters or empty spaces into a string.</span></span>

<span data-ttu-id="d246f-113">[Comparaison de chaînes](comparing.md) : décrit la manière de comparer le contenu de deux chaînes ou plus.</span><span class="sxs-lookup"><span data-stu-id="d246f-113">[Comparing strings](comparing.md) - Describes how to compare the contents of two or more strings.</span></span>

<span data-ttu-id="d246f-114">[Changement de casse](changing-case.md) : décrit la manière de modifier la casse des caractères dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="d246f-114">[Changing case](changing-case.md) - Describes how to change the case of characters within a string.</span></span>

<span data-ttu-id="d246f-115">[Utilisation de la classe StringBuilder](stringbuilder.md) : décrit la manière de créer et modifier des objets String dynamiques avec la classe [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="d246f-115">[Using the StringBuilder class](stringbuilder.md) - Describes how to create and modify dynamic string objects with the [StringBuilder](xref:System.Text.StringBuilder) class.</span></span>

<span data-ttu-id="d246f-116">[Guide pratique : effectuer des manipulations de chaînes de base](basic-manipulations.md) : illustre l’utilisation des opérations de chaînes de base.</span><span class="sxs-lookup"><span data-stu-id="d246f-116">[How to: Perform basic string manipulations](basic-manipulations.md) - Demonstrates the use of basic string operations.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d246f-117">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d246f-117">Related Sections</span></span>

<span data-ttu-id="d246f-118">[Conversion de type](type-conversion.md) : explique comment convertir un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="d246f-118">[Type conversion](type-conversion.md) - Describes how to convert from one type to another.</span></span>

<span data-ttu-id="d246f-119">[Mise en forme des types](formatting-types.md) : explique comment mettre en forme des chaînes à l’aide de spécificateurs de format de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d246f-119">[Formatting types](formatting-types.md) - Describes how to format strings using the string format specifiers.</span></span>



