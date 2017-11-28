---
title: "out, modificateur de paramètre (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a>out, modificateur de paramètre (référence C#)
Le mot clé `out` entraîne le passage des arguments par référence. Il est similaire au mot clé [ref](../../../csharp/language-reference/keywords/ref.md), à la différence que `ref` nécessite que la variable soit initialisée avant d’être passée. Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`. Exemple :  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> Le mot clé `out` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est covariant. Pour plus d’informations sur l’utilisation du mot clé `out` dans ce contexte, consultez [out, modificateur générique](../../../csharp/language-reference/keywords/out-generic-modifier.md).
  
 Les variables passées comme arguments `out` n’ont pas à être initialisées avant d’être passées dans un appel de méthode. Toutefois, la méthode appelée doit assigner une valeur avant le retour de la méthode.  
  
 Bien que les mots clés `ref` et `out` entraînent un comportement différent lors de l'exécution, ils ne sont pas considérés comme partie de la signature de la méthode au moment de la compilation. Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l'une d'elles accepte un argument`ref` et l'autre un argument `out`. Le code suivant, par exemple, ne se compilera pas :  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Toutefois, la surcharge est autorisée si une méthode prend un argument `ref` ou `out` et que l’autre méthode n’utilise ni l’un ni l’autre, comme suit :  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.  
  
 Pour plus d’informations sur le passage de tableaux, consultez [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :  
  
-   Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).  
  
-   Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  

## <a name="declaring-out-arguments"></a>Déclaration d’arguments `out`   

 La déclaration d’une méthode avec des arguments `out` est utile lorsque vous souhaitez qu’une méthode retourne plusieurs valeurs. L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode. Notez que le troisième argument reçoit la valeur null. Cela permet aux méthodes de retourner des valeurs le cas échéant.  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 Le [modèle Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) consiste à retourner une valeur `bool` qui indique si une opération a réussi ou échoué et à retourner le résultat de l’opération dans un argument `out`. Un certain nombre de méthodes d’analyse, notamment la méthode [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), utilisent ce modèle.
   
## <a name="calling-a-method-with-an-out-argument"></a>Appel d’une méthode avec un argument `out`

Dans C# 6 et les versions antérieures, vous devez déclarer une variable dans une instruction distincte avant de la passer comme argument `out`. L’exemple suivant déclare une variable nommée `number` avant de la passer à la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), qui tente de convertir une chaîne en nombre.

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

À compter de C# 7, vous pouvez déclarer la variable `out` dans la liste d’arguments de l’appel de méthode au lieu de le faire dans une déclaration de variable distincte. Cette technique rend le code plus simple et plus lisible, et vous empêche également d’assigner par inadvertance une valeur à la variable avant l’appel de méthode. L’exemple suivant est semblable au précédent, sauf qu’il définit la variable `number` dans l’appel de la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
Dans l’exemple précédent, la variable `number` est fortement typée en `int`. Vous pouvez également déclarer une variable locale implicitement typée, comme dans l’exemple suivant.

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)
