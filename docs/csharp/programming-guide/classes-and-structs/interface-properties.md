---
title: "Propriétés d'interface (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: 13
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
ms.openlocfilehash: 2b76cdc4e8419b08dcd95c3711eaead5513ae1d9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="9a858-102">Propriétés d'interface (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9a858-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="9a858-103">Des propriétés peuvent être déclarées dans une [interface](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="9a858-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="9a858-104">L’exemple ci-dessous porte sur un accesseur d’indexeur d’interface :</span><span class="sxs-lookup"><span data-stu-id="9a858-104">The following is an example of an interface indexer accessor:</span></span>  
  
 <span data-ttu-id="9a858-105">[!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a858-105">[!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]</span></span>  
  
 <span data-ttu-id="9a858-106">L’accesseur d’une propriété d’interface n’a pas de corps.</span><span class="sxs-lookup"><span data-stu-id="9a858-106">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="9a858-107">Par conséquent, les accesseurs visent à indiquer si la propriété est en lecture-écriture, en lecture seule ou en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="9a858-107">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a858-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9a858-108">Example</span></span>  
 <span data-ttu-id="9a858-109">Dans cet exemple, l’interface `IEmployee` a une propriété en lecture-écriture, `Name`, et une propriété en lecture seule, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="9a858-109">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="9a858-110">La classe `Employee` implémente l’interface `IEmployee` et utilise ces deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="9a858-110">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="9a858-111">Le programme lit le nom d’un nouvel employé et le nombre actuel d’employés et affiche le nom de l’employé et le nombre d’employés calculé.</span><span class="sxs-lookup"><span data-stu-id="9a858-111">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="9a858-112">Vous pouvez utiliser le nom qualifié complet de la propriété, qui fait référence à l’interface dans laquelle le membre est déclaré.</span><span class="sxs-lookup"><span data-stu-id="9a858-112">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="9a858-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9a858-113">For example:</span></span>  
  
 <span data-ttu-id="9a858-114">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a858-114">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span></span>  
  
 <span data-ttu-id="9a858-115">Ceci s’appelle une [implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="9a858-115">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="9a858-116">Par exemple, si la classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même propriété `Name`, l’implémentation de membre d’interface explicite est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9a858-116">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="9a858-117">Autrement dit, la déclaration de propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="9a858-117">That is, the following property declaration:</span></span>  
  
 <span data-ttu-id="9a858-118">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a858-118">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span></span>  
  
 <span data-ttu-id="9a858-119">implémente la propriété `Name` dans l’interface `IEmployee`, alors que la déclaration suivante :</span><span class="sxs-lookup"><span data-stu-id="9a858-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 <span data-ttu-id="9a858-120">[!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a858-120">[!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]</span></span>  
  
 <span data-ttu-id="9a858-121">implémente la propriété `Name` dans l’interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="9a858-121">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 <span data-ttu-id="9a858-122">[!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a858-122">[!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]</span></span>  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="9a858-123">Résultat de l'exemple</span><span class="sxs-lookup"><span data-stu-id="9a858-123">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="9a858-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a858-124">See Also</span></span>  
 <span data-ttu-id="9a858-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a858-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9a858-126">[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="9a858-126">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="9a858-127">[Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9a858-127">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="9a858-128">[Comparaison entre propriétés et indexeurs](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md) </span><span class="sxs-lookup"><span data-stu-id="9a858-128">[Comparison Between Properties and Indexers](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md) </span></span>  
 <span data-ttu-id="9a858-129">[Indexeurs](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a858-129">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="9a858-130">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9a858-130">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

