---
title: "Attributs C# - Visite guidée du langage C#"
description: "Découvrir la programmation déclarative à l’aide des attributs en C#"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 6878a408ef892ee47a03bfa04f736b9bf9671696
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="attributes"></a><span data-ttu-id="7263d-104">Attributs</span><span class="sxs-lookup"><span data-stu-id="7263d-104">Attributes</span></span>

<span data-ttu-id="7263d-105">Les types, membres et autres entités d’un programme C# prennent en charge les modificateurs qui contrôlent certains aspects de leur comportement.</span><span class="sxs-lookup"><span data-stu-id="7263d-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="7263d-106">Par exemple, l’accessibilité d’une méthode est contrôlée à l’aide des modificateurs `public`, `protected`, `internal` et `private`.</span><span class="sxs-lookup"><span data-stu-id="7263d-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="7263d-107">C# généralise cette fonctionnalité pour que les types d’informations déclaratives définis par l’utilisateur puissent être associés aux entités de programme et récupérés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7263d-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="7263d-108">Les programmes spécifient ces informations déclaratives supplémentaires en définissant et en utilisant les ***attributs***.</span><span class="sxs-lookup"><span data-stu-id="7263d-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="7263d-109">L’exemple suivant déclare un attribut `HelpAttribute` qui peut être placé sur des entités de programme pour fournir des liens vers leur documentation associée.</span><span class="sxs-lookup"><span data-stu-id="7263d-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="7263d-110">Toutes les classes d’attributs dérivent de la classe de base <xref:System.Attribute> fournie par la bibliothèque standard.</span><span class="sxs-lookup"><span data-stu-id="7263d-110">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="7263d-111">Les attributs peuvent être appliqués en donnant leur nom, ainsi que les éventuels arguments, à l’intérieur de crochets juste avant la déclaration associée.</span><span class="sxs-lookup"><span data-stu-id="7263d-111">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="7263d-112">Si le nom d’un attribut se termine en `Attribute`, cette partie du nom peut être omise lorsque l’attribut est référencé.</span><span class="sxs-lookup"><span data-stu-id="7263d-112">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="7263d-113">Par exemple, l’attribut `HelpAttribute` peut être utilisé comme suit.</span><span class="sxs-lookup"><span data-stu-id="7263d-113">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="7263d-114">Cet exemple joint un `HelpAttribute` à la classe `Widget`.</span><span class="sxs-lookup"><span data-stu-id="7263d-114">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="7263d-115">Il ajoute un autre `HelpAttribute` à la méthode `Display` dans la classe.</span><span class="sxs-lookup"><span data-stu-id="7263d-115">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="7263d-116">Les constructeurs publics d’une classe d’attributs contrôlent les informations qui doivent être fournies lorsque l’attribut est joint à une entité de programme.</span><span class="sxs-lookup"><span data-stu-id="7263d-116">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="7263d-117">Des informations supplémentaires peuvent être fournies en référençant les propriétés en lecture-écriture publiques de la classe d’attributs (comme la référence à la propriété `Topic`, précédemment).</span><span class="sxs-lookup"><span data-stu-id="7263d-117">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="7263d-118">Lorsqu’un attribut particulier est demandé par réflexion, le constructeur de la classe d’attributs est appelé avec les informations fournies dans la source du programme, et l’instance d’attribut qui en résulte est retournée.</span><span class="sxs-lookup"><span data-stu-id="7263d-118">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="7263d-119">Si des informations supplémentaires ont été fournies via les propriétés, ces propriétés sont définies sur les valeurs données avant que le renvoi de l’instance de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="7263d-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="7263d-120">Précédent</span><span class="sxs-lookup"><span data-stu-id="7263d-120">Previous</span></span>](delegates.md)
