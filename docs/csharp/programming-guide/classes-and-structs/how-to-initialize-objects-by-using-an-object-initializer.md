---
title: "Guide pratique pour initialiser des objets à l'aide d'un initialiseur d'objet (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1e65f8519062f6bceeb466a3b72c5719c0918f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="b63ef-102">Guide pratique pour initialiser des objets à l'aide d'un initialiseur d'objet (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b63ef-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="b63ef-103">Vous pouvez utiliser des initialiseurs d’objets pour initialiser des objets de type de façon déclarative sans appeler explicitement un constructeur pour le type.</span><span class="sxs-lookup"><span data-stu-id="b63ef-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="b63ef-104">Les exemples suivants montrent comment utiliser des initialiseurs d’objets avec des objets nommés.</span><span class="sxs-lookup"><span data-stu-id="b63ef-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="b63ef-105">Le compilateur traite les initialiseurs d’objets en accédant d’abord au constructeur d’instance par défaut, puis en traitant les initialisations des membres.</span><span class="sxs-lookup"><span data-stu-id="b63ef-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="b63ef-106">Ainsi, si le constructeur par défaut est déclaré comme `private` dans la classe, les initialiseurs d’objets qui nécessitent un accès public échoueront.</span><span class="sxs-lookup"><span data-stu-id="b63ef-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="b63ef-107">Vous devez utiliser un initialiseur d’objet si vous définissez un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="b63ef-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="b63ef-108">Pour plus d’informations, consultez [Guide pratique pour retourner des sous-ensembles de propriétés d’éléments dans une requête](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="b63ef-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b63ef-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b63ef-109">Example</span></span>  
 <span data-ttu-id="b63ef-110">L’exemple suivant montre comment initialiser un nouveau type `StudentName` à l’aide d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="b63ef-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="b63ef-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b63ef-111">Example</span></span>  
 <span data-ttu-id="b63ef-112">L’exemple suivant montre comment initialiser une collection de types `StudentName` à l’aide d’un initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="b63ef-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="b63ef-113">Notez qu’un initialiseur de collection est une série d’initialiseurs d’objets séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="b63ef-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b63ef-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b63ef-114">Compiling the Code</span></span>  
 <span data-ttu-id="b63ef-115">Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b63ef-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63ef-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b63ef-116">See Also</span></span>  
 [<span data-ttu-id="b63ef-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b63ef-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b63ef-118">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="b63ef-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
