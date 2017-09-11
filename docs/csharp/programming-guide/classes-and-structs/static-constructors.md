---
title: Constructeurs statiques (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 73df76c61f393bf5fe09af66935acfbac4b5663f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="79b79-102">Constructeurs statiques (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="79b79-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="79b79-103">Un constructeur statique est utilisé pour initialiser des données [statiques](../../../csharp/language-reference/keywords/static.md) ou pour effectuer une action particulière qui ne doit être effectuée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="79b79-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="79b79-104">Il est automatiquement appelé avant la création de la première instance ou le référencement d’un membre statique.</span><span class="sxs-lookup"><span data-stu-id="79b79-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 <span data-ttu-id="79b79-105">[!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="79b79-105">[!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="79b79-106">Les constructeurs statiques ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="79b79-106">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="79b79-107">Un constructeur statique n’accepte pas de modificateur d’accès et n’a pas de paramètre.</span><span class="sxs-lookup"><span data-stu-id="79b79-107">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="79b79-108">Un constructeur statique est automatiquement appelé pour initialiser la [classe](../../../csharp/language-reference/keywords/class.md) avant la création de la première instance ou le référencement d’un membre statique.</span><span class="sxs-lookup"><span data-stu-id="79b79-108">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="79b79-109">Un constructeur statique ne peut pas être appelé directement.</span><span class="sxs-lookup"><span data-stu-id="79b79-109">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="79b79-110">L’utilisateur n’a aucun contrôle sur le moment d’exécution du constructeur statique dans le programme.</span><span class="sxs-lookup"><span data-stu-id="79b79-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="79b79-111">Généralement, on utilise des constructeurs statiques quand la classe utilise un fichier journal et que le constructeur sert à écrire des entrées dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="79b79-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="79b79-112">Les constructeurs statiques sont également utiles pour la création de classes wrapper pour du code non managé, quand le constructeur peut appeler la méthode `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="79b79-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="79b79-113">Si un constructeur statique lève une exception, le runtime ne l’appelle pas une deuxième fois et le type reste non initialisé pour la durée de vie du domaine d’application dans lequel votre programme s’exécute.</span><span class="sxs-lookup"><span data-stu-id="79b79-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79b79-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="79b79-114">Example</span></span>  
 <span data-ttu-id="79b79-115">Dans cet exemple, la classe `Bus` possède un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="79b79-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="79b79-116">Quand la première instance de `Bus` est créée (`bus1`), le constructeur statique est appelé pour initialiser la classe.</span><span class="sxs-lookup"><span data-stu-id="79b79-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="79b79-117">L’exemple de sortie vérifie que le constructeur statique s’exécute une seule fois, même si deux instances de `Bus` sont créées, et qu’il s’exécute avant le constructeur d’instance.</span><span class="sxs-lookup"><span data-stu-id="79b79-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 <span data-ttu-id="79b79-118">[!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="79b79-118">[!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b79-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79b79-119">See Also</span></span>  
 <span data-ttu-id="79b79-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="79b79-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="79b79-121">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="79b79-121">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="79b79-122">[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="79b79-122">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="79b79-123">[Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="79b79-123">[Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
 [<span data-ttu-id="79b79-124">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="79b79-124">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

