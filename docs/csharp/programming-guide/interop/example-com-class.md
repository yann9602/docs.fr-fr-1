---
title: Exemple de classe COM (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad14b414c037d38da55ce0ec82685b790cc46d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="bd70c-102">Exemple de classe COM (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bd70c-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="bd70c-103">Voici un exemple de classe pouvant être exposée en tant qu’objet COM.</span><span class="sxs-lookup"><span data-stu-id="bd70c-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="bd70c-104">Après avoir placé ce code dans un fichier .cs et l’avoir ajouté à votre projet, affectez la valeur **True** à la propriété **Inscrire pour COM Interop**.</span><span class="sxs-lookup"><span data-stu-id="bd70c-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="bd70c-105">Pour plus d’informations, consultez [NIB : Guide pratique pour inscrire un composant pour COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span><span class="sxs-lookup"><span data-stu-id="bd70c-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="bd70c-106">L’exposition d’objets Visual C# à COM nécessite de déclarer une interface de classe, une interface d’événements si nécessaire, et la classe proprement dite.</span><span class="sxs-lookup"><span data-stu-id="bd70c-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="bd70c-107">Les membres de classe doivent suivre ces règles pour être visibles par COM :</span><span class="sxs-lookup"><span data-stu-id="bd70c-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="bd70c-108">La classe doit être publique.</span><span class="sxs-lookup"><span data-stu-id="bd70c-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="bd70c-109">Les propriétés, méthodes et événements doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="bd70c-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="bd70c-110">Les propriétés et méthodes doivent être déclarées dans l’interface de classe.</span><span class="sxs-lookup"><span data-stu-id="bd70c-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="bd70c-111">Les événements doivent être déclarés dans l’interface d’événement.</span><span class="sxs-lookup"><span data-stu-id="bd70c-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="bd70c-112">Les autres membres publics de la classe qui ne sont pas déclarés dans ces interfaces ne seront pas visibles par COM, mais ils seront visibles par d’autres objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd70c-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="bd70c-113">Pour exposer des propriétés et des méthodes à COM, vous devez les déclarer sur l’interface de classe, les marquer avec un attribut `DispId` et les implémenter dans la classe.</span><span class="sxs-lookup"><span data-stu-id="bd70c-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="bd70c-114">L’ordre dans lequel les membres sont déclarés dans l’interface est l’ordre utilisé pour la vtable COM.</span><span class="sxs-lookup"><span data-stu-id="bd70c-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="bd70c-115">Pour exposer des événements à partir de votre classe, vous devez les déclarer sur l’interface d’événement et les marquer avec un attribut `DispId`.</span><span class="sxs-lookup"><span data-stu-id="bd70c-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="bd70c-116">La classe ne doit pas implémenter cette interface.</span><span class="sxs-lookup"><span data-stu-id="bd70c-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="bd70c-117">La classe implémente l’interface de classe ; elle peut implémenter plusieurs interfaces, mais la première implémentation sera l’interface de classe par défaut.</span><span class="sxs-lookup"><span data-stu-id="bd70c-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="bd70c-118">Implémentez ici les méthodes et propriétés exposées à COM.</span><span class="sxs-lookup"><span data-stu-id="bd70c-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="bd70c-119">Elles doivent être marquées comme publiques et doivent correspondre aux déclarations dans l’interface de classe.</span><span class="sxs-lookup"><span data-stu-id="bd70c-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="bd70c-120">Vous devez aussi déclarer ici les événements déclenchés par la classe.</span><span class="sxs-lookup"><span data-stu-id="bd70c-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="bd70c-121">Ils doivent être marqués comme publics et doivent correspondre aux déclarations dans l’interface d’événement.</span><span class="sxs-lookup"><span data-stu-id="bd70c-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd70c-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd70c-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bd70c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd70c-123">See Also</span></span>  
 [<span data-ttu-id="bd70c-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bd70c-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bd70c-125">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="bd70c-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
 [<span data-ttu-id="bd70c-126">Page Générer, Concepteur de projet (C#)</span><span class="sxs-lookup"><span data-stu-id="bd70c-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
