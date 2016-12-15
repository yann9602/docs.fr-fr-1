---
title: "switch (R&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "switch_CSharpKeyword"
  - "switch"
  - "case"
  - "case_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "switch (instruction C#)"
  - "switch (mot clé C#)"
  - "Case (instruction C#)"
  - "default (mot clé C#)"
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
caps.handback.revision: 47
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# switch (R&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'instruction `switch` est une séquence de contrôle qui sélectionne une *section switch* à exécuter dans une liste de candidats.  
  
 Une instruction `switch` inclut une ou plusieurs sections de commutation.  Chaque section switch contient un ou plusieurs *noms de cas* suivis d'une ou de plusieurs instructions.  L'exemple suivant montre une instruction `switch` simple qui a trois sections switch.  Chaque section switch a un nom de cas, tel que `case 1` et une liste de deux instructions.  
  
 [!code-cs[csrefKeywordsSelection#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_1.cs)]  
  
## Notes  
 Chaque nom de cas spécifie une valeur de constante.  L'instruction switch transfère le contrôle à la section switch dont l'étiquette case correspond à la valeur de l'*expression switch* \(`caseSwitch` dans l'exemple\).  Si aucun nom de cas ne contient de valeur correspondante, le contrôle est transféré vers la section `default`, s'il y en a une.  S'il n'y a aucune section `default`, aucune action n'est effectuée et le contrôle est transféré à l'extérieur de l'instruction `switch`.  Dans l'exemple précédent, les instructions dans la première section commutateur sont exécutées car `case 1` correspond à la valeur `caseSwitch`.  
  
 Une instruction `switch` peut inclure plusieurs sections commutateur, et chaque section peut contenir une ou plusieurs étiquettes case \(comme indiqué dans l'exemple d'étiquettes case de chaîne ci\-dessous\).  Toutefois, aucun nom avec deux cas ne peut contenir la même valeur de constante.  
  
 L'exécution de la liste d'instructions dans la section switch sélectionnée commence par la première instruction et continue par la liste d'instructions, en général jusqu'à ce qu'une instruction de saut soit atteinte, comme `break`, `goto case`, `return` ou `throw`.  À ce stade, le contrôle est transféré hors de l'instruction `switch` ou vers un autre nom de cas.  
  
 À la différence de C\+\+, C\# ne permet pas à l'exécution de passer d'une section switch à la suivante.  Le code suivant génère une erreur.  
  
```c#  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
  
 C\# requiert que la fin des sections commutateur, y compris la dernière, soit inaccessible.  Autrement dit, contrairement à d'autres langages, votre code ne peut pas passer dans la section switch suivante.  Bien que cette obligation soit généralement remplie à l'aide d'une instruction `break`, le cas suivant est également valide, car il assure que la fin de la liste d'instruction ne peut pas être atteinte.  
  
```c#  
case 4:  
    while (true)  
        Console.WriteLine("Endless looping. . . .");  
```  
  
## Exemple  
 L'exemple suivant illustre les exigences et les fonctionnalités d'une instruction `switch`.  
  
 [!code-cs[csrefKeywordsSelection#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_2.cs)]  
  
## Exemple  
 Dans l'exemple final, la variable chaîne, `str` et les étiquettes case de chaîne contrôlent le flux d'exécution.  
  
 [!code-cs[csrefKeywordsSelection#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/switch_3.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [switch, instruction \(C\+\+\)](/visual-cpp/cpp/switch-statement-cpp)   
 [if\-else](../../../csharp/language-reference/keywords/if-else.md)