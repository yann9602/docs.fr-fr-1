---
title: "readonly (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "readonly_CSharpKeyword"
  - "readonly"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "readonly (mot clé C#)"
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# readonly (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `readonly` est un modificateur que vous pouvez utiliser sur des champs.  Lorsqu'une déclaration de champ comprend un modificateur `readonly`, les assignations aux champs introduites par la déclaration sont possibles uniquement dans le cadre de la déclaration ou dans un constructeur de la même classe.  
  
## Exemple  
 Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la méthode `ChangeYear`, bien qu'une valeur lui soit assignée dans le constructeur de la classe :  
  
 [!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Vous pouvez assigner une valeur à un champ `readonly` uniquement dans les contextes suivants :  
  
-   Lorsque la variable est initialisée dans la déclaration. Exemple :  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   Pour un champ d'instance, dans les constructeurs d'instance de la classe qui contient la déclaration de champ ou pour un champ statique, dans le constructeur statique de la classe qui contient la déclaration de champ.  Ce sont les seuls contextes dans lesquels il est valide de passer un champ `readonly` en tant que paramètre [out](../../../csharp/language-reference/keywords/out.md) ou [ref](../../../csharp/language-reference/keywords/ref.md).  
  
> [!NOTE]
>  Le mot clé `readonly` est différent du mot clé [const](../../../csharp/language-reference/keywords/const.md).  Un champ `const` ne peut être initialisé que dans sa déclaration.  Un champ `readonly` peut être initialisé soit dans la déclaration, soit dans un constructeur.  C'est pourquoi les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.  En outre, un champ `const` est une constante de compilation, tandis que le champ `readonly` peut être utilisé pour les constantes d'exécution, comme dans l'exemple suivant :  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## Exemple  
 [!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 Dans l'exemple précédent, si vous utilisez une instruction telle que :  
  
 `p2.y = 66;        // Error`  
  
 vous obtenez le message d'erreur de compilation :  
  
 `The left-hand side of an assignment must be an l-value`  
  
 qui correspond à la même erreur que vous obtenez lorsque vous tentez d'assigner une valeur à une constante.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)