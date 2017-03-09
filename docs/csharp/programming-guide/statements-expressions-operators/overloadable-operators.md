---
title: "Op&#233;rateurs surchargeables (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, surcharge d'opérateur"
  - "surcharge d'opérateur (C#)"
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# Op&#233;rateurs surchargeables (Guide de programmation&#160;C#)
C\# permet aux types définis par l'utilisateur de surcharger des opérateurs en définissant des fonctions de membre statique à l'aide du mot clé [operator](../../../csharp/language-reference/keywords/operator.md).  Toutefois, tous les opérateurs ne peuvent pas être surchargés et d'autres présentent des restrictions, comme indiqué dans ce tableau :  
  
|Opérateurs|Possibilité de surcharge|  
|----------------|------------------------------|  
|[\+](../../../csharp/language-reference/operators/addition-operator.md), [\-](../../../csharp/language-reference/operators/subtraction-operator.md), [\!](../../../csharp/language-reference/operators/logical-negation-operator.md), [~](../../../csharp/language-reference/operators/bitwise-complement-operator.md), [\+\+](../../../csharp/language-reference/operators/increment-operator.md), [\-\-](../../../csharp/language-reference/operators/decrement-operator.md), [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md)|Ces opérateurs unaires peuvent être surchargés.|  
|[\+](../../../csharp/language-reference/operators/addition-operator.md), [\-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [\/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md),                               [&#124;](../../../csharp/language-reference/operators/or-operator.md) , [^](../../../csharp/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [\>\>](../../../csharp/language-reference/operators/right-shift-operator.md)|Ces opérateurs binaires peuvent être surchargés.|  
|[\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md), [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../../../csharp/language-reference/operators/less-than-operator.md), [\>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [\>\=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)|Les opérateurs de comparaison peuvent être surchargés \(mais consultez la remarque qui suit ce tableau\).|  
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|Les opérateurs logiques conditionnels ne peuvent pas être surchargés, mais ils sont évalués à l'aide de `&` et                               `&#124;` , qui peuvent être surchargés.|  
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|L'opérateur d'indexation de tableau ne peut pas être surchargé, mais vous pouvez définir des indexeurs.|  
|[\(T\)x](../../../csharp/language-reference/operators/invocation-operator.md)|L'opérateur de cast ne peut pas être surchargé, mais vous pouvez définir de nouveaux opérateurs de conversion \(consultez [explicit](../../../csharp/language-reference/keywords/explicit.md) et [implicit](../../../csharp/language-reference/keywords/implicit.md)\).|  
|[\+\=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [\-\=](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md), [\*\=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [\/\=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [%\=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&\=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;\=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^\=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<\=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [\>\>\=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|Les opérateurs d'assignation ne peuvent pas être surchargés, mais `+=`, par exemple, est évalué à l'aide de `+`, qui peut être surchargé.|  
|[\=](../../../csharp/language-reference/operators/assignment-operator.md), [.](../../../csharp/language-reference/operators/member-access-operator.md), [?:](../../../csharp/language-reference/operators/conditional-operator.md), [??](../../../csharp/language-reference/operators/null-conditional-operator.md), [\-\>](../../../csharp/language-reference/operators/dereference-operator.md), [\=\>](../../../csharp/language-reference/operators/lambda-operator.md), [f\(x\)](../../../csharp/language-reference/operators/invocation-operator.md), [as](../../../csharp/language-reference/keywords/as.md), [checked](../../../csharp/language-reference/keywords/checked.md), [unchecked](../../../csharp/language-reference/keywords/unchecked.md), [default](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md), [delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../../csharp/language-reference/keywords/is.md), [new](../../../csharp/language-reference/keywords/new.md), [sizeof](../../../csharp/language-reference/keywords/sizeof.md), [typeof](../../../csharp/language-reference/keywords/typeof.md)|Ces opérateurs ne peuvent pas être surchargés.|  
  
> [!NOTE]
>  Les opérateurs de comparaison, s'ils sont surchargés, doivent l'être par paires ; autrement dit, si `==` est surchargé, `!=` doit également l'être.  L'inverse est également vrai, et similaire pour `<` et `>`, et pour `<=` et `>=`.  
  
 La surcharge d'un opérateur sur une classe personnalisée requiert la création d'une méthode sur la classe avec la signature correcte.  La méthode doit être nommée « opérateur X » où X est le nom ou le symbole de l'opérateur surchargé.  Les opérateurs unaires ont un seul paramètre et les opérateurs binaires en ont deux.  Dans chaque cas, un seul paramètre doit être du même type que la classe ou le struct qui déclarent l'opérateur.  
  
```c#  
public static Complex operator +(Complex c1, Complex c2)  
    {  
        Return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);  
    }  
  
```  
  
 Il est courant d'avoir des définitions qui retournent tout simplement immédiatement le résultat d'une expression.  Il existe un raccourci de syntaxe qui utilise `=>` pour ces situations.  
  
```c#  
public static Complex operator +(Complex c1, Complex c2) =>  
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);  
  
    // Override ToString() to display a complex number   
    // in the traditional format:  
    public override string ToString() => $"{this.real} + {this.imaginary}";  
  
```  
  
 Pour plus d'informations, consultez [Comment : utiliser la surcharge d'opérateur pour créer une classe de nombres complexes](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Instructions, expressions et opérateurs](../../../csharp/programming-guide/statements-expressions-operators/index.md)   
 [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [Pourquoi les opérateurs surchargés sont\-ils toujours statiques en C\# ?](http://go.microsoft.com/fwlink/?LinkId=112383)