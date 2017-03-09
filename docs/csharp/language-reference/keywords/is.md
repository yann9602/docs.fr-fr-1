---
title: "is (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2017-02-17"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "is_CSharpKeyword"
  - "is"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "is (mot clé C#)"
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# is (r&#233;f&#233;rence C#)
Vérifie si un objet est compatible avec un type donné.  Par exemple, le code suivant permet de déterminer si un objet est une instance du type `MyObject` ou un type dérivé de `MyObject` :  
  
```  
if (obj is MyObject)  
{  
}  
```  
  
 Une expression `is` prend la valeur `true` si l'expression fournie n'est pas null, et que l'objet fourni peut être casté en type fourni sans entraîner la levée d'une exception.  
  
 Le mot clé `is` engendre un avertissement de compilation si l'expression doit toujours être `true` ou `false`, mais en général il évalue la compatibilité de type au moment de l'exécution.  
  
 L'opérateur `is` ne peut pas être surchargé.  
  
 Notez que l'opérateur `is` considère uniquement les conversions de référence, les conversions boxing et les conversions unboxing.  D'autres conversions, comme les conversions définies par l'utilisateur, ne sont pas prises en compte.  
  
 Les méthodes anonymes ne sont pas autorisées à gauche de l'opérateur `is`.  Cette exception inclut les expressions lambda.  
  
## Exemple  
 [!code-cs[csrefKeywordsOperator#4](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#4)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)