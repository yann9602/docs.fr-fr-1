---
title: "typeof (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "typeof"
  - "typeof_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "typeof (mot clé C#)"
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# typeof (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Sert à obtenir l'objet `System.Type` d'un type.  Une expression `typeof` prend la forme suivante :  
  
```  
System.Type type = typeof(int);  
```  
  
## Notes  
 Pour obtenir le type d'exécution d'une expression, vous pouvez utiliser la méthode <xref:System.Object.GetType%2A> du .NET Framework, comme dans l'exemple suivant :  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 L'opérateur `typeof` ne peut pas être surchargé.  
  
 L'opérateur `typeof` peut également être utilisé sur les types génériques ouverts.  Les types ayant plusieurs paramètres de type doivent présenter le nombre approprié de virgules dans leur spécification.  L'exemple suivant indique comment déterminer si le type de retour d'une méthode est un <xref:System.Collections.Generic.IEnumerable%601> générique.  Supposez que la méthode est une instance de type MethodInfo :  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## Exemple  
 [!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Object.GetType%2A> pour déterminer le type utilisé pour contenir le résultat d'un calcul numérique.  Cela dépend des besoins en mémoire du nombre résultant.  
  
 [!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.Type?displayProperty=fullName>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)