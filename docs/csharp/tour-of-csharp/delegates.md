---
title: "Délégués C# - Visite guidée du langage C#"
description: "Découvrez la liaison tardive avec les délégués C#"
keywords: ".NET, csharp, délégation, lambda, liaison tardive"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="3e3fb-104">Délégués</span><span class="sxs-lookup"><span data-stu-id="3e3fb-104">Delegates</span></span>

<span data-ttu-id="3e3fb-105">Un ***type délégué*** représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-105">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="3e3fb-106">Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-106">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="3e3fb-107">Les délégués sont similaires au concept de pointeurs de fonction dans d’autres langages, mais contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-107">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="3e3fb-108">L’exemple suivant déclare et utilise un type délégué nommé `Function`.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="3e3fb-109">Une instance du type délégué `Function` peut faire référence à toute méthode qui accepte un argument `double` et retourne une valeur `double`.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="3e3fb-110">La méthode `Apply` applique une fonction donnée aux éléments d’un `double[]`, et retourne un `double[]` avec les résultats.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="3e3fb-111">Dans la méthode `Main`, `Apply` sert à appliquer trois fonctions différentes à un `double[]`.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="3e3fb-112">Un délégué peut faire référence à une méthode statique (comme `Square` ou `Math.Sin` dans l’exemple précédent) ou à une méthode d’instance (comme `m.Multiply` dans l’exemple précédent).</span><span class="sxs-lookup"><span data-stu-id="3e3fb-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="3e3fb-113">Un délégué qui référence une méthode d’instance référence aussi un objet particulier, et quand la méthode d’instance est appelée via le délégué, cet objet devient `this` dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="3e3fb-114">Les délégués peuvent également être créés à l’aide de fonctions anonymes, qui sont des « méthodes inline » créées à la volée.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="3e3fb-115">Les fonctions anonymes peuvent voir les variables locales des méthodes qui l’entourent.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="3e3fb-116">Par conséquent, l’exemple de multiplicateur ci-dessus peut être écrit plus facilement sans utiliser une classe Multiplicateur :</span><span class="sxs-lookup"><span data-stu-id="3e3fb-116">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="3e3fb-117">Une propriété intéressante et utile d’un délégué est qu’il ne connaît pas la classe de la méthode qu’il référence, et cela lui est égal. Tout ce qui importe est que la méthode référencée ait les mêmes paramètres et type de retour que le délégué.</span><span class="sxs-lookup"><span data-stu-id="3e3fb-117">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="3e3fb-118">[Précédent](enums.md)
[Suivant](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="3e3fb-118">[Previous](enums.md)
[Next](attributes.md)</span></span>
