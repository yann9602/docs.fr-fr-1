---
title: "params (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "params_CSharpKeyword"
  - "params"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "paramètres [C#], params"
  - "params (mot clé C#)"
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# params (r&#233;f&#233;rence C#)
En utilisant le mot clé `params` vous pouvez spécifier un [paramètre de méthode](../../../csharp/language-reference/keywords/method-parameters.md) qui prend un nombre variable d'arguments.  
  
 Vous pouvez envoyer une liste d'arguments du type spécifié séparés par des virgules dans la déclaration de paramètre ou un tableau d'arguments du type spécifié.  Vous pouvez également ne pas envoyer d'arguments.  Si vous n'envoyez aucun argument, la longueur de la liste `params` est zéro.  
  
 Aucun paramètre supplémentaire n'est autorisé après le mot clé `params` dans une déclaration de méthode et un seul mot clé `params` est autorisé dans une telle déclaration.  
  
## Exemple  
 L'exemple suivant montre différents moyens d'envoyer des arguments à un paramètre `params`.  
  
 [!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)