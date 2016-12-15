---
title: "Espace de noms (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "namespace_CSharpKeyword"
  - "namespace"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "namespace (mot clé C#)"
  - "portée (C#)"
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Espace de noms (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé d' `namespace` est utilisé pour déclarer une portée qui contient un ensemble d'objets connexes.  Vous pouvez utiliser un espace de noms pour organiser des éléments de code et créer globalement de types uniques.  
  
 [!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## Notes  
 Au sein d'un espace de noms, vous pouvez déclarer un ou plusieurs des types suivants :  
  
-   un autre espace de noms  
  
-   [classe](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [délégué](../../../csharp/language-reference/keywords/delegate.md)  
  
 Que vous déclariez ou pas explicitement un espace de noms dans un fichier source C\#, le compilateur ajoute un espace de noms par défaut.  Cet espace de noms sans nom, parfois appelé espace de noms global, est présent dans chaque fichier.  Tout identificateur dans l'espace de noms global est disponible pour être utilisé dans un espace de noms nommé.  
  
 Les espaces de noms disposent implicitement d'un accès public et cela ne peut pas être changé.  Consultez [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour en savoir plus sur les modificateurs d'accès que vous pouvez assigner à des éléments dans un espace de noms.  
  
 Il est possible de définir un espace de noms dans deux déclarations ou plus.  Par exemple, le code suivant définit deux classes comme appartenant à l'espace de noms `MyCompany` :  
  
 [!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## Exemple  
 L'exemple suivant montre comment appeler une méthode statique dans un espace de noms imbriqué.  
  
 [!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## Pour plus d'informations  
 Pour plus d'informations sur l'utilisation des espaces de noms, consultez les rubriques suivantes :  
  
-   [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Utilisation d'espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Comment : utiliser l'alias d'espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d'espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [using](../../../csharp/language-reference/keywords/using.md)