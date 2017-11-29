---
title: "for (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a>for (référence C#)
En utilisant une boucle `for`, vous pouvez exécuter une instruction ou un bloc d’instructions de manière répétée jusqu'à ce qu’une expression spécifiée corresponde à `false`. Ce type de boucle est utile pour itérer des tableaux et d’autres applications pour lesquelles vous savez à l’avance combien de fois vous souhaitez effectuer une itération.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la valeur de `i` est écrite dans la console et incrémentée de 1 à chaque itération de la boucle.  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 L’instruction `for` de l’exemple précédent effectue les actions suivantes :  
  
1.  Tout d’abord, la valeur initiale de la variable `i` est établie. Cette étape se produit une seule fois, quel que soit le nombre d’itérations de la boucle. Vous pouvez considérer cette initialisation comme survenant en dehors du processus de boucle.  
  
2.  Pour évaluer la condition (`i <= 5`), la valeur de `i` est comparée à 5.  
  
    -   Si `i` est inférieur ou égal à 5, la condition prend la valeur `true`, et les actions suivantes se produisent.  
  
        1.  L’instruction `Console.WriteLine` dans le corps de la boucle affiche la valeur de `i`.  
  
        2.  La valeur de `i` incrémentée de 1.  
  
        3.  La boucle retourne au début de l’étape 2 pour évaluer de nouveau la condition.  
  
    -   Si `i` est supérieur à 5, la condition prend la valeur `false`, et vous quittez la boucle.  
  
 Notez que, si la valeur initiale de `i` est supérieure à 5, le corps de la boucle n’est jamais exécuté.  
  
 Chaque instruction `for` définit les sections Initialiseur, Condition et Itérateur. Ces sections déterminent généralement le nombre d’itérations de la boucle.  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 Ces sections répondent aux objectifs suivants :  
  
-   La section Initialiseur définit les conditions initiales. Les instructions de cette section ne sont exécutées qu’une seule fois, avant l’entrée dans la boucle. La section peut contenir uniquement l’une des deux options suivantes.  
  
    -   La déclaration et l’initialisation d’une variable de boucle locale, comme le montre le premier exemple (`int i = 1`). La variable se trouve dans la boucle et n’est pas accessible en dehors de celle-ci.  
  
    -   Zéro ou plusieurs expressions d’instruction de la liste suivante, séparées par des virgules.  
  
        -   Instruction d’[assignation](../../../csharp/language-reference/operators/assignment-operator.md)  
  
        -   Appel d’une méthode  
  
        -   Expression d’[incrémentation](../../../csharp/language-reference/operators/increment-operator.md) préfixée ou suffixée, telle que `++i` ou `i++`  
  
        -   Expression de [décrémentation](../../../csharp/language-reference/operators/decrement-operator.md) préfixée ou suffixée, telle que `--i` ou `i--`  
  
        -   Création d’un objet à l’aide de [new](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   Expression [await](../../../csharp/language-reference/keywords/await.md)  
  
-   La section Condition contient une expression booléenne qui est évaluée pour déterminer si la boucle doit s’arrêter ou s’exécuter de nouveau.  
  
-   La section Itérateur définit ce qui se produit après chaque itération du corps de la boucle. La section Itérateur contient zéro ou plusieurs des expressions d’instruction suivantes, séparées par des virgules :  
  
    -   Instruction d’[assignation](../../../csharp/language-reference/operators/assignment-operator.md)  
  
    -   Appel d’une méthode  
  
    -   Expression d’[incrémentation](../../../csharp/language-reference/operators/increment-operator.md) préfixée ou suffixée, telle que `++i` ou `i++`  
  
    -   Expression de [décrémentation](../../../csharp/language-reference/operators/decrement-operator.md) préfixée ou suffixée, telle que `--i` ou `i--`  
  
    -   Création d’un objet à l’aide de [new](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   Expression [await](../../../csharp/language-reference/keywords/await.md)  
  
-   Le corps de la boucle se compose d’une instruction, d’une instruction vide ou d’un bloc d’instructions que vous créez en plaçant zéro ou plusieurs instructions entre accolades.  
  
     Vous pouvez quitter une boucle `for` à l’aide du mot clé [break](../../../csharp/language-reference/keywords/break.md), ou passer à l’itération suivante de la boucle à l’aide du mot clé [continue](../../../csharp/language-reference/keywords/continue.md). Vous pouvez quitter une boucle en utilisant une instruction [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
 Le premier exemple de cette rubrique montre le type de boucle `for` le plus courant, qui fait les choix suivants au niveau des sections :  
  
-   L’initialiseur déclare et initialise une variable de boucle locale, `i`, qui compte le nombre d’itérations de la boucle.  
  
-   La condition compare la valeur de la variable de boucle par rapport à la valeur finale connue de 5.  
  
-   La section Itérateur utilise une instruction d’incrémentation suffixée, `i++`, pour calculer chaque itération de la boucle.  
  
 L’exemple suivant montre plusieurs choix moins courants : l’attribution d’une valeur à une variable de boucle externe dans la section Initialiseur, l’appel de la méthode `Console.WriteLine` dans les sections Initialiseur et Itérateur, et la modification des valeurs de deux variables dans la section Itérateur.  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 Toutes les expressions qui définissent une instruction `for` sont facultatives. Par exemple, l’instruction suivante crée une boucle infinie.  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [for, instruction (C++)](/cpp/cpp/for-statement-cpp)  
 [Instructions d’itération](../../../csharp/language-reference/keywords/iteration-statements.md)
