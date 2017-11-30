---
title: "Création d'une classe pour contenir des fonctions DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="a0108-102">Création d'une classe pour contenir des fonctions DLL</span><span class="sxs-lookup"><span data-stu-id="a0108-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="a0108-103">L’enveloppement d’une fonction DLL fréquemment utilisée dans une classe managée est une stratégie efficace d’encapsulation des fonctionnalités de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="a0108-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="a0108-104">Bien que cette opération ne soit pas obligatoire dans tous les cas, un wrapper de classe s’avère pratique, car la définition de fonctions DLL peut être fastidieuse et sujette à erreurs.</span><span class="sxs-lookup"><span data-stu-id="a0108-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="a0108-105">En cas de programmation en Visual Basic ou C#, vous devez déclarer les fonctions DLL dans une classe ou un module Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a0108-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="a0108-106">Dans une classe, vous définissez une méthode statique pour chaque fonction DLL que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="a0108-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="a0108-107">La définition peut inclure des informations supplémentaires, telles que le jeu de caractères ou la convention d’appel qui sont utilisés lors du passage des arguments des méthodes. Si vous ne renseignez pas ces informations, les paramètres par défaut sont alors sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="a0108-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="a0108-108">Pour obtenir une liste complète des options de déclaration et de leurs paramètres par défaut, consultez [Création de prototypes dans du code managé](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="a0108-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="a0108-109">Une fois l’encapsulation effectuée, vous pouvez appeler les méthodes sur la fonction de la même manière que vous appelez des méthodes sur toute autre fonction statique.</span><span class="sxs-lookup"><span data-stu-id="a0108-109">Once wrapped, you can call methods on the function as you call methods on any other static function.</span></span> <span data-ttu-id="a0108-110">L’appel de code non managé gère automatiquement la fonction exportée sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="a0108-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="a0108-111">Lors de la conception d’une classe managée pour l’appel de code non managé, tenez compte des relations entre les classes et les fonctions DLL.</span><span class="sxs-lookup"><span data-stu-id="a0108-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="a0108-112">Par exemple, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="a0108-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="a0108-113">déclarer des fonctions DLL dans une classe existante ;</span><span class="sxs-lookup"><span data-stu-id="a0108-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="a0108-114">créer une classe individuelle pour chaque fonction DLL, en maintenant les fonctions isolées et facilement localisables ;</span><span class="sxs-lookup"><span data-stu-id="a0108-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="a0108-115">créer une classe pour un ensemble de fonctions DLL associées afin de former des regroupements logiques et réduire la charge mémoire.</span><span class="sxs-lookup"><span data-stu-id="a0108-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="a0108-116">Vous pouvez nommer la classe et ses méthodes à votre convenance.</span><span class="sxs-lookup"><span data-stu-id="a0108-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="a0108-117">Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="a0108-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0108-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0108-118">See Also</span></span>  
 [<span data-ttu-id="a0108-119">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="a0108-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="a0108-120">Identification des fonctions des DLL</span><span class="sxs-lookup"><span data-stu-id="a0108-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="a0108-121">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="a0108-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="a0108-122">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="a0108-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
