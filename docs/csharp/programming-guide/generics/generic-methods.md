---
title: "Méthodes génériques (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: 27
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
ms.openlocfilehash: 14461773303bafc098f79c3686b1f76827f11005
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generic-methods-c-programming-guide"></a>Méthodes génériques (guide de programmation C#)
Une méthode générique est une méthode qui est déclarée avec des paramètres de type, comme suit :  
  
 [!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 L’exemple de code suivant montre une manière d’appeler la méthode, avec `int` comme argument de type :  
  
 [!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Vous pouvez également omettre l’argument de type et le compilateur le déduira. L’appel suivant à `Swap` est équivalent à l’appel précédent :  
  
 [!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 Les mêmes règles d’inférence de type s’appliquent aux méthodes statiques et aux méthodes d’instance. Le compilateur peut déduire les paramètres de type d’après les arguments de méthode que vous passez. Il ne peut pas déduire les paramètres de type uniquement à partir d’une valeur de contrainte ou de retour. Par conséquent, l’inférence de type ne fonctionne pas avec les méthodes qui n’ont pas de paramètres. L’inférence de type se produit au moment de la compilation avant que le compilateur n’essaie de résoudre toute signature de méthode surchargée. Le compilateur applique la logique d’inférence de type à toutes les méthodes génériques qui partagent le même nom. À l’étape de résolution de la surcharge, le compilateur inclut uniquement les méthodes génériques sur lesquelles l’inférence de type a réussi.  
  
 Dans une classe générique, les méthodes non génériques peuvent accéder aux paramètres de type de niveau classe, comme suit :  
  
 [!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Si vous définissez une méthode générique qui accepte les mêmes paramètres de type que la classe conteneur, le compilateur génère l’avertissement CS0693, car l’argument fourni à l’intérieur de la portée de la méthode pour le `T` interne masque l’argument fourni pour le `T` externe. Si vous avez éventuellement besoin d’appeler une méthode de classe générique avec des arguments de type différents de ceux qui ont été fournis quand la classe a été instanciée, envisagez de fournir un autre identificateur pour le paramètre de type de la méthode, comme indiqué dans `GenericList2<T>` dans l’exemple suivant.  
  
 [!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Utilisez des contraintes pour permettre des opérations plus spécialisées sur les paramètres de type dans les méthodes. Cette version de `Swap<T>`, maintenant appelée `SwapIfGreater<T>`, peut être utilisée avec des arguments de type qui implémentent <xref:System.IComparable%601> uniquement.  
  
 [!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Les méthodes génériques peuvent être surchargées sur plusieurs paramètres de type. Par exemple, les méthodes suivantes peuvent toutes être dans la même classe :  
  
 [!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 Pour plus d'informations, consultez la [spécification du langage C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)

