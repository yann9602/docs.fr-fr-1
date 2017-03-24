---
title: "Comment&#160;: analyser des cha&#238;nes &#224; l’aide de String.Split (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fractionner des chaînes (C#)"
  - "Split (méthode C#)"
  - "chaînes (C#), fractionner"
  - "analyser des chaînes"
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Comment&#160;: analyser des cha&#238;nes &#224; l’aide de String.Split (Guide de programmation&#160;C#)
L’exemple de code suivant montre comment analyser une chaîne à l’aide de la méthode <xref:System.String.Split%2A?displayProperty=fullName>.<xref:System.String.Split%2A> accepte comme entrée un tableau qui indique les caractères séparant les sous\-chaînes intéressantes de la chaîne cible.  La fonction retourne un tableau des sous\-chaînes.  
  
 Cet exemple utilise des caractères de séparation \(espaces, virgules, points, deux\-points et onglets\) qui sont tous passés dans un tableau à <xref:System.String.Split%2A>.  Chaque mot dans la phrase de la chaîne cible est affiché séparément du tableau de chaînes résultant.  
  
## Exemple  
 [!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## Exemple  
 Par défaut, String.Split retourne des chaînes vides quand deux caractères de séparation apparaissent de façon contiguë dans la chaîne cible.  Vous pouvez passer un paramètre StringSplitOptions.RemoveEmptyEntries facultatif pour exclure toutes les chaînes vides dans la sortie.  
  
 String.Split peut accepter un tableau de chaînes \(séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible\).  
  
```c#  
class TestStringSplit { static void Main() { char[] separatingChars = { "<<", "..." }; string text = "one<<two......three<four"; System.Console.WriteLine("Original text: '{0}'", text); string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries ); System.Console.WriteLine("{0} substrings in text:", words.Length); foreach (string s in words) { System.Console.WriteLine(s); } // Keep the console window open in debug mode. System.Console.WriteLine("Press any key to exit."); System.Console.ReadKey(); } } /* Output: Original text: 'one<<two......three<four' 3 words in text: one two three<four */  
  
```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [Expressions régulières du .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)