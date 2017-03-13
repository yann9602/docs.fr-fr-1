---
title: "Comment&#160;: rechercher des cha&#238;nes &#224; l&#39;aide d&#39;expressions r&#233;guli&#232;res (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "rechercher des chaînes (C#)"
  - "chaînes [C#], rechercher à l’aide de RegEx"
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# Comment&#160;: rechercher des cha&#238;nes &#224; l&#39;aide d&#39;expressions r&#233;guli&#232;res (Guide de programmation C#)
La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> peut être utilisée pour rechercher des chaînes.  Ces recherches peuvent avoir un niveau de complexité allant de très simple à une utilisation complète d'expressions régulières.  Les éléments suivants sont deux exemples de recherche de chaînes à l'aide de la classe <xref:System.Text.RegularExpressions.Regex>.  Pour plus d'informations, consultez [Expressions régulières du .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md).  
  
## Exemple  
 Le code suivant est une application console qui exécute une recherche simple de chaînes dans un tableau, sans respect de la casse.  La méthode statique <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> exécute la recherche en fonction de la chaîne à rechercher et une chaîne qui contient le modèle de recherche.  Dans ce cas, un troisième argument est utilisé pour indiquer que la casse doit être ignorée.  Pour plus d'informations, consultez <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## Exemple  
 Le code suivant est une application console qui utilise des expressions régulières pour valider le format de chaque chaîne dans un tableau.  La validation requiert que chaque chaîne prenne la forme d'un numéro de téléphone dans lequel trois groupes de chiffres sont séparés par des tirets, les deux premiers groupes contenant trois chiffres, et le troisième groupe avec quatre chiffres.  Cette opération s'effectue à l'aide de l'expression régulière `^\\d{3}-\\d{3}-\\d{4}$`.  Pour plus d'informations, consultez [Langage des expressions régulières \- Aide\-mémoire](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md).  
  
 [!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## Voir aussi  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [Expressions régulières du .NET Framework](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [Langage des expressions régulières \- Aide\-mémoire](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md)