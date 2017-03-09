---
title: "Comment&#160;: effectuer sans risque un cast du type bool? en bool (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "caster (C#), types Nullable"
  - "types Nullable (C#), caster bool? en bool"
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# Comment&#160;: effectuer sans risque un cast du type bool? en bool (Guide de programmation&#160;C#)
Le type Nullable `bool?` peut contenir trois valeurs différentes : `true`, `false` et `null`.  Par conséquent, le type `bool?` ne peut pas être utilisé dans des conditionnels comme `if`, `for` ou `while`.  Par exemple, le code suivant crée une erreur de compilation.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 Cela n'est pas autorisé parce que la signification de `null` n'est pas claire dans le contexte d'un conditionnel.  Pour utiliser un type `bool?` dans une instruction conditionnelle, commencez par vérifier sa propriété <xref:System.Nullable%601.HasValue%2A> pour vous assurer que sa valeur n'est pas `null`, puis convertissez\-le en un `bool`.  Pour plus d'informations, consultez [bool](../../../csharp/language-reference/keywords/bool.md).  Si vous effectuez le cast sur un type `bool?` avec une valeur `null`, une <xref:System.InvalidOperationException> sera levée dans le test conditionnel.  L'exemple suivant illustre comment convertir sans risque un type `bool?` en `bool` :  
  
## Exemple  
  
```c#  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés littéraux](../../../csharp/language-reference/keywords/literal-keywords.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [?? Opérateur](../../../csharp/language-reference/operators/null-conditional-operator.md)