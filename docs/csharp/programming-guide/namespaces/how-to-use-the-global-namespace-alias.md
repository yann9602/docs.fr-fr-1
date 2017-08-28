---
title: "Guide pratique pour utiliser l’alias de l’espace de noms global (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
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
ms.openlocfilehash: 1252fc107d46b1d3a1cbef0a61708edc57253910
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>Guide pratique pour utiliser l’alias de l’espace de noms global (Guide de programmation C#)
La possibilité d’accéder à un membre dans l’[espace de noms ](../../../csharp/language-reference/keywords/namespace.md) global est utile quand le membre peut être masqué par une autre entité de même nom.  
  
 Par exemple, dans le code suivant, `Console` est résolu en `TestApp.Console` plutôt qu’en type `Console` dans l’espace de noms <xref:System>.  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 L’utilisation de `System.Console` continue de générer une erreur, car l’espace de noms `System` est masqué par la classe `TestApp.System` :  
  
 [!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 Cependant, vous pouvez contourner cette erreur en utilisant `global::System.Console`, comme ceci :  
  
 [!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 Quand l’identificateur de gauche est `global`, la recherche de l’identificateur de droite débute dans l’espace de noms global. Par exemple, la déclaration suivante fait référence à `TestApp` en tant que membre de l’espace global.  
  
 [!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 Bien entendu, il n’est pas recommandé de créer des espaces de noms personnalisés sous le nom `System`, et il est peu probable que vous en rencontriez dans du code. Cependant, dans les projets à grande échelle, il est tout à fait possible qu’un espace de noms soit dupliqué d’une façon ou d’une autre. En pareil cas, le qualificateur d’espace de noms global est la garantie que vous pouvez spécifier l’espace de noms racine.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’espace de noms `System` est utilisé pour inclure la classe `TestClass`. De ce fait, `global::System.Console` doit être utilisé pour faire référence à la classe `System.Console`, qui est masquée par l’espace de noms `System`. Par ailleurs, l’alias `colAlias` est utilisé pour faire référence à l’espace de noms `System.Collections` ; par conséquent, l’instance d’un <xref:System.Collections.Hashtable?displayProperty=fullName> a été créée en utilisant cet alias plutôt que l’espace de noms.  
  
 [!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 **A 1**  
**B 2**  
**C 3**   
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
 [. , opérateur](../../../csharp/language-reference/operators/member-access-operator.md)   
 [::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)

