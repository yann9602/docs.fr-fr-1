---
title: "Guide pratique pour initialiser des objets à l'aide d'un initialiseur d'objet (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
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
ms.openlocfilehash: 01f2391680d9236b42f0d015b944b8f12455d0c8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="f9b5e-102">Guide pratique pour initialiser des objets à l'aide d'un initialiseur d'objet (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f9b5e-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="f9b5e-103">Vous pouvez utiliser des initialiseurs d’objets pour initialiser des objets de type de façon déclarative sans appeler explicitement un constructeur pour le type.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="f9b5e-104">Les exemples suivants montrent comment utiliser des initialiseurs d’objets avec des objets nommés.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="f9b5e-105">Le compilateur traite les initialiseurs d’objets en accédant d’abord au constructeur d’instance par défaut, puis en traitant les initialisations des membres.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="f9b5e-106">Ainsi, si le constructeur par défaut est déclaré comme `private` dans la classe, les initialiseurs d’objets qui nécessitent un accès public échoueront.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="f9b5e-107">Vous devez utiliser un initialiseur d’objet si vous définissez un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="f9b5e-108">Pour plus d’informations, consultez [Guide pratique pour retourner des sous-ensembles de propriétés d’éléments dans une requête](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="f9b5e-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b5e-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9b5e-109">Example</span></span>  
 <span data-ttu-id="f9b5e-110">L’exemple suivant montre comment initialiser un nouveau type `StudentName` à l’aide d’initialiseurs d’objets.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 <span data-ttu-id="f9b5e-111">[!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f9b5e-111">[!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b5e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9b5e-112">Example</span></span>  
 <span data-ttu-id="f9b5e-113">L’exemple suivant montre comment initialiser une collection de types `StudentName` à l’aide d’un initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-113">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="f9b5e-114">Notez qu’un initialiseur de collection est une série d’initialiseurs d’objets séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f9b5e-114">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 <span data-ttu-id="f9b5e-115">[!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f9b5e-115">[!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9b5e-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f9b5e-116">Compiling the Code</span></span>  
 <span data-ttu-id="f9b5e-117">Pour exécuter ce code, copiez et collez la classe dans un projet d’application console Visual C# qui a été créé dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9b5e-117">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="f9b5e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9b5e-118">See Also</span></span>  
 <span data-ttu-id="f9b5e-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9b5e-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f9b5e-120">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="f9b5e-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

