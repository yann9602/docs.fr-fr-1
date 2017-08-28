---
title: "Guide pratique pour accéder à une classe de collection à l’aide de foreach (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
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
ms.openlocfilehash: 2ad81ab699b079f4aabb04a886211e94a937335d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a>Guide pratique pour accéder à une classe de collection à l’aide de foreach (Guide de programmation C#)
L’exemple de code suivant montre comment écrire une classe de collection non générique qui peut être utilisée avec [foreach](../../../csharp/language-reference/keywords/foreach-in.md). L’exemple définit une classe de générateurs de jetons de chaînes.  
  
> [!NOTE]
>  Cet exemple représente la méthode recommandée uniquement quand vous ne pouvez pas utiliser une classe de collection générique. Pour obtenir un exemple montrant comment implémenter une classe de collection générique de type sécurisé qui prend en charge <xref:System.Collections.Generic.IEnumerable%601>, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
 Dans l’exemple, le segment de code suivant utilise la classe `Tokens` pour décomposer la phrase « This is a sample sentence. » en jetons en utilisant ' ' et '-' comme séparateurs. Le code affiche ensuite ces jetons à l’aide d’une instruction `foreach`.  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>Exemple  
 En interne, la classe `Tokens` utilise un tableau pour stocker les jetons. Étant donné que les tableaux implémentent <xref:System.Collections.IEnumerator> et <xref:System.Collections.IEnumerable>, l’exemple de code aurait pu utiliser les méthodes d’énumération du tableau (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.Current%2A>) au lieu de les définir dans la classe `Tokens`. Les définitions de méthode sont incluses dans l’exemple pour clarifier la façon dont elles sont définies et ce que chacune d’elles fait.  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 En C#, une classe de collection n’est pas obligée d’implémenter <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour être compatible avec `foreach`. Si la classe a les membres <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.Current%2A> nécessaires, elle fonctionnera avec `foreach`. L’omission des interfaces vous permet de définir un type de retour pour `Current` qui est plus spécifique qu’<xref:System.Object>. Cela garantit la sécurité de type.  
  
 Par exemple, changez les lignes suivantes dans l’exemple précédent.  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 Étant donné que `Current` retourne une chaîne, le compilateur peut détecter quand un type incompatible est utilisé dans une instruction `foreach`, comme illustré dans le code suivant.  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 L’omission d’<xref:System.Collections.IEnumerable> et d’<xref:System.Collections.IEnumerator> a toutefois un inconvénient : la classe de collection n’est plus interopérable avec les instructions `foreach` (ou instructions équivalentes) d’autres langages du common language runtime.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)

