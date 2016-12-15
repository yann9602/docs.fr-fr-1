---
title: "unchecked (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "unchecked_CSharpKeyword"
  - "unchecked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "unchecked (mot clé C#)"
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# unchecked (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `unchecked` sert à supprimer le contrôle de dépassement pour les opérations arithmétiques de type entier et les conversions.  
  
 Dans un contexte non vérifié \(unchecked\), si une expression produit une valeur qui est hors de la plage du type de destination, le résultat n'est pas marqué d'un indicateur.  Le calcul de l'exemple suivant étant exécuté dans un bloc ou une expression `unchecked`, le fait que le résultat est trop volumineux pour un entier est ignoré, et la valeur \-2,147,483,639 est assignée à `int1`.  
  
 [!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Si l'environnement `unchecked` est supprimé, une erreur de compilation se produit.  Le dépassement de capacité peut être détecté au moment de la compilation parce que tous les termes de l'expression sont des constantes.  
  
 Les expressions qui contiennent des termes non constants sont non vérifiées par défaut au moment de la compilation et de l'exécution.  Consultez [checked](../../../csharp/language-reference/keywords/checked.md) pour plus d'informations sur l'activation d'un environnement vérifié.  
  
 Parce que la vérification du dépassement de capacité prend du temps, l'utilisation de code non vérifié dans les situations où il n'y a aucun danger de dépassement peut améliorer la performance.  Toutefois, si le dépassement de capacité est susceptible de se produire, un environnement vérifié doit être utilisé.  
  
## Exemple  
 Cet exemple indique comment utiliser le mot clé `unchecked`.  
  
 [!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [checked](../../../csharp/language-reference/keywords/checked.md)