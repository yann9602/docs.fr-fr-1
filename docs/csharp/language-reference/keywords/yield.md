---
title: "yield (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords: yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4735ab33faea71b792cbc6b567884b64bd6ca029
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="yield-c-reference"></a>yield (Référence C#)
Lorsque vous utilisez le mot clé `yield` dans une instruction, vous indiquez que la méthode, l'opérateur, ou l'accesseur `get` dans lequel elle apparaît est un itérateur. L'utilisation de `yield` pour définir un itérateur rend une classe explicite supplémentaire inutile (la classe qui contient l'état d'une énumération ; pour obtenir un exemple, consultez <xref:System.Collections.Generic.IEnumerator%601>) lorsque vous implémentez les modèles <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour un type de collection personnalisé.  
  
 L'exemple suivant montre les deux formulaires de l'instruction `yield`.  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>Remarques  
 Utilisez une instruction `yield return` pour retourner chaque élément un par un.  
  
 Vous consommez une méthode Iterator à l’aide d’une instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ou d’une requête LINQ. Chaque itération de la boucle `foreach` appelle la méthode Iterator. Lorsqu'une instruction `yield return` est atteinte dans la méthode Iterator, `expression` est retourné, et l'emplacement dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Utilisez une instruction `yield break` pour terminer l'itération.  
  
 Pour plus d’informations sur les itérateurs, consultez [Itérateurs](../../iterators.md).  
  
## <a name="iterator-methods-and-get-accessors"></a>Méthodes Iterator et accesseurs get  
 La déclaration d'un itérateur doit respecter les spécifications suivantes :  
  
-   Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   La déclaration ne peut pas contenir des paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ni [out](../../../csharp/language-reference/keywords/out.md).  
  
 Le type `yield` d'un itérateur qui retourne <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> est `object`.  Si l'itérateur retourne <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, il doit exister une conversion implicite du type de l'expression dans l'instruction `yield return` au paramètre de type générique.  
  
 Vous ne pouvez pas inclure une instruction `yield return` ou `yield break` dans les méthodes qui présentent les caractéristiques suivantes :  
  
-   Méthodes anonymes. Pour plus d’informations, consultez [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
-   Méthodes qui contiennent des blocs unsafe. Pour plus d’informations, consultez [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 Il ne peut pas y avoir d'instruction `yield return` dans un bloc try-catch. Une instruction `yield return` peut se trouver dans le bloc try d'une instruction try-finally.  
  
 Une instruction `yield break` peut se trouver dans un bloc try ou un bloc catch mais pas dans un bloc finally.  
  
 Si le corps `foreach` (en dehors de la méthode Iterator) lève une exception, un bloc `finally` de la méthode Iterator est exécuté.  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Le code suivant retourne `IEnumerable<string>` depuis une méthode Iterator, puis itère au sein de ses éléments.  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 L'appel à `MyIteratorMethod` n'exécute pas le corps de la méthode. À la place, l'appel retourne `IEnumerable<string>` dans la variable `elements`.  
  
 Dans une itération de la boucle `foreach`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`. Cet appel exécute le corps de `MyIteratorMethod` jusqu'à ce que l'instruction `yield return` suivante soit atteinte. L’expression retournée par le `yield return` instruction détermine non seulement la valeur de la `element` variable pour la consommation par le corps de la boucle, mais également le <xref:System.Collections.Generic.IEnumerator%601.Current%2A> propriété de `elements`, qui est un `IEnumerable<string>`.  
  
 À chaque itération suivante de la boucle `foreach`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `yield return`. La boucle `foreach` se termine lorsque à la fin de la méthode Iterator ou lorsqu'une instruction `yield break` est atteinte.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant comprend une instruction `yield return` située dans une boucle `for`. Chaque itération du corps d'instruction `foreach` dans `Process` crée un appel à la fonction d'itérateur `Power`. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `yield return`, qui se produit pendant l'itération suivante de la boucle `for`.  
  
 Le type de retour de la méthode Iterator est <xref:System.Collections.IEnumerable>, qui est un type interface itérateur. Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre un accesseur `get` qui est un itérateur. Dans cet exemple, chaque instruction `yield return` retourne une instance d'une classe définie par l'utilisateur.  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Itérateurs](../../iterators.md)
