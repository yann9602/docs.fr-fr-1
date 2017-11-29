---
title: Constructeurs statiques (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="0fb3d-102">Constructeurs statiques (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="0fb3d-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="0fb3d-103">Un constructeur statique est utilisé pour initialiser des données [statiques](../../../csharp/language-reference/keywords/static.md) ou pour effectuer une action particulière qui ne doit être effectuée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="0fb3d-104">Il est automatiquement appelé avant la création de la première instance ou le référencement d’un membre statique.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="0fb3d-105">Les constructeurs statiques ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="0fb3d-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="0fb3d-106">Un constructeur statique n’accepte pas de modificateur d’accès et n’a pas de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="0fb3d-107">Un constructeur statique est automatiquement appelé pour initialiser la [classe](../../../csharp/language-reference/keywords/class.md) avant la création de la première instance ou le référencement d’un membre statique.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="0fb3d-108">Un constructeur statique ne peut pas être appelé directement.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="0fb3d-109">L’utilisateur n’a aucun contrôle sur le moment d’exécution du constructeur statique dans le programme.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="0fb3d-110">Généralement, on utilise des constructeurs statiques quand la classe utilise un fichier journal et que le constructeur sert à écrire des entrées dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="0fb3d-111">Les constructeurs statiques sont également utiles pour la création de classes wrapper pour du code non managé, quand le constructeur peut appeler la méthode `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="0fb3d-112">Si un constructeur statique lève une exception, le runtime ne l’appelle pas une deuxième fois et le type reste non initialisé pour la durée de vie du domaine d’application dans lequel votre programme s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fb3d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fb3d-113">Example</span></span>  
 <span data-ttu-id="0fb3d-114">Dans cet exemple, la classe `Bus` possède un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="0fb3d-115">Quand la première instance de `Bus` est créée (`bus1`), le constructeur statique est appelé pour initialiser la classe.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="0fb3d-116">L’exemple de sortie vérifie que le constructeur statique s’exécute une seule fois, même si deux instances de `Bus` sont créées, et qu’il s’exécute avant le constructeur d’instance.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0fb3d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fb3d-117">See Also</span></span>  
 [<span data-ttu-id="0fb3d-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0fb3d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0fb3d-119">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="0fb3d-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="0fb3d-120">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="0fb3d-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="0fb3d-121">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="0fb3d-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="0fb3d-122">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="0fb3d-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
