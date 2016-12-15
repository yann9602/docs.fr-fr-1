---
title: "for (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "for"
  - "for_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "for (mot clé C#)"
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# for (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

À l'aide d'une boucle d' `for` , vous pouvez exécuter une instruction ou un bloc d'instructions à plusieurs reprises jusqu'à ce qu'une expression spécifiée prend la `false`.  Ce genre de boucle est utile pour itérer au sein de les tableaux et d'autres applications dans lesquelles vous connaissez à l'avance la fréquence à laquelle vous souhaitez que la boucle pour itérer.  
  
## Exemple  
 Dans l'exemple suivant, la valeur d' `i` est écrite dans la console et incrémenté par 1 pendant chaque itération de la boucle.  
  
 [!code-cs[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 l'instruction d' `for` dans l'exemple précédent exécute les actions suivantes.  
  
1.  D'abord, la valeur initiale d' `i` variable est générée.  Cette étape se produit uniquement une fois, indépendamment du nombre de fois la boucle se répète.  Vous pouvez considérer cette initialisation en tant qu'événement en dehors de le processus de boucle.  
  
2.  Pour évaluer la condition \(`i <= 5`\), la valeur d' `i` est comparée à 5.  
  
    -   Si `i` est inférieure ou égale à 5, la condition a la `true`, et les actions suivantes se produisent.  
  
        1.  L'instruction d' `Console.WriteLine` dans le corps de la boucle affiche la valeur d' `i`.  
  
        2.  La valeur d' `i` est incrémentée par 1.  
  
        3.  La boucle retourne au début de l'étape 2 pour évaluer la condition de nouveau.  
  
    -   Si `i` est supérieur à 5, la condition a la `false`, et vous quittez la boucle.  
  
 Notez que, si la valeur initiale d' `i` est supérieure à 5, le corps de la boucle ne s'exécute pas même une fois.  
  
 Chaque instruction d' `for` définit l'initialiseur, la condition, les sections et itérateur.  Ces sections déterminent généralement le nombre de fois la boucle itère.  
  
```c#  
for (initializer; condition; iterator)  
    body  
```  
  
 Les sections répondent aux objectifs suivants.  
  
-   La section d'initialiseur définit les conditions initiales.  Les instructions de cette section s'exécutent qu'une seule fois, avant d'écrire la boucle.  La section peut contenir un des deux options suivantes.  
  
    -   La déclaration et l'initialisation d'une variable de boucle locale, comme premier exemple montre`int i = 1`\(\).  La variable est locale à la boucle et ne peut pas accessible en dehors de la boucle.  
  
    -   Expressons zéro ou plus de l'instruction de la liste suivante, séparés par des virgules.  
  
        -   Instruction d'[assignation](../../../csharp/language-reference/operators/assignment-operator.md)  
  
        -   appel d'une méthode  
  
        -   suffixez préfixe ou l'expression d'index, telle qu' `++i` ou `i++`  
  
        -   suffixez préfixe ou l'expression de [décrément](../../../csharp/language-reference/operators/decrement-operator.md) , telle qu' `--i` ou `i--`  
  
        -   création d'un objet à l'aide de [nouveau](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   expression d'[attendez](../../../csharp/language-reference/keywords/await.md)  
  
-   La section de condition contient une expression booléenne qui est évaluée pour déterminer si la boucle doit quitter ou exécuter de nouveau.  
  
-   La section des itérateurs définit ce qui se produit après chaque itération du corps de la boucle.  La section des itérateurs contient zéro ou plusieurs expressions suivantes de l'instruction, séparés par des virgules :  
  
    -   Instruction d'[assignation](../../../csharp/language-reference/operators/assignment-operator.md)  
  
    -   appel d'une méthode  
  
    -   suffixez préfixe ou l'expression d'index, telle qu' `++i` ou `i++`  
  
    -   suffixez préfixe ou l'expression de [décrément](../../../csharp/language-reference/operators/decrement-operator.md) , telle qu' `--i` ou `i--`  
  
    -   création d'un objet à l'aide de [nouveau](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   expression d'[attendez](../../../csharp/language-reference/keywords/await.md)  
  
-   Le corps de la boucle se compose d'une instruction, une instruction vide, ou un bloc d'instructions, que vous créez en plaçant zéro ou plusieurs instructions accolades.  
  
     Vous pouvez de quitter une boucle d' `for` à l'aide de le mot clé de [break](../../../csharp/language-reference/keywords/break.md) , ou vous pouvez passer à l'itération suivante à l'aide de le mot clé de [continuez](../../../csharp/language-reference/keywords/continue.md) .  Vous pouvez également quitter une boucle à l'aide de [goto](../../../csharp/language-reference/keywords/goto.md), de [retour](../../../csharp/language-reference/keywords/return.md), ou de l'instruction de [throw](../../../csharp/language-reference/keywords/throw.md) .  
  
 Le premier exemple de cette rubrique indique le type le plus courant de boucle d' `for` , qui effectue les choix suivants pour les sections.  
  
-   L'initialiseur déclare et initialise une variable de boucle locale, `i`, qui met à jour un nombre d'itérations de la boucle.  
  
-   Les contrôles de spécification la valeur de la variable de boucle sur une valeur finale., 5.  
  
-   La section des itérateurs utilise une instruction de post\-incrémentation, `i++`, pour compter chaque itération de la boucle.  
  
 L'exemple suivant montre plusieurs choix moins courants : l'assignation d'une valeur à une variable de boucle externe dans la section d'initialiseur, en appelant la méthode d' `Console.WriteLine` dans l'initialiseur les sections et des itérateurs, et modifier les valeurs de deux variables dans la section des itérateurs.  
  
 [!code-cs[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 Toutes les expressions qui définissent une instruction d' `for` sont facultatives.  Par exemple, l'instruction suivante crée une boucle infinie.  
  
 [!code-cs[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [for, instruction \(C\+\+\)](/visual-cpp/cpp/for-statement-cpp)   
 [Instructions d'itération](../../../csharp/language-reference/keywords/iteration-statements.md)