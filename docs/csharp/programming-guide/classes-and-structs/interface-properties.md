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
# <a name="interface-properties-c-programming-guide"></a>Propriétés d'interface (Guide de programmation C#)
Des propriétés peuvent être déclarées dans une [interface](../../../csharp/language-reference/keywords/interface.md). L’exemple ci-dessous porte sur un accesseur d’indexeur d’interface :  
  
 [!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 L’accesseur d’une propriété d’interface n’a pas de corps. Par conséquent, les accesseurs visent à indiquer si la propriété est en lecture-écriture, en lecture seule ou en écriture seule.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’interface `IEmployee` a une propriété en lecture-écriture, `Name`, et une propriété en lecture seule, `Counter`. La classe `Employee` implémente l’interface `IEmployee` et utilise ces deux propriétés. Le programme lit le nom d’un nouvel employé et le nombre actuel d’employés et affiche le nom de l’employé et le nombre d’employés calculé.  
  
 Vous pouvez utiliser le nom qualifié complet de la propriété, qui fait référence à l’interface dans laquelle le membre est déclaré. Exemple :  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Ceci s’appelle une [implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Par exemple, si la classe `Employee` implémente deux interfaces, `ICitizen` et `IEmployee`, et que les deux interfaces ont la même propriété `Name`, l’implémentation de membre d’interface explicite est nécessaire. Autrement dit, la déclaration de propriété suivante :  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implémente la propriété `Name` dans l’interface `IEmployee`, alors que la déclaration suivante :  
  
 [!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 implémente la propriété `Name` dans l’interface `ICitizen`.  
  
 [!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Résultat de l'exemple  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Utilisation de propriétés](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Comparaison entre propriétés et indexeurs](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)

