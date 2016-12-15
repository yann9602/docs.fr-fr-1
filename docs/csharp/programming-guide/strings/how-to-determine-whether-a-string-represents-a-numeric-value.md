---
title: "Comment&#160;: d&#233;terminer si une cha&#238;ne repr&#233;sente une valeur num&#233;rique (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "chaînes numériques (C#)"
  - "chaînes (C#), numériques"
  - "valider des entrées numériques (C#)"
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: d&#233;terminer si une cha&#238;ne repr&#233;sente une valeur num&#233;rique (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Pour déterminer si une chaîne est une représentation valide d'un type numérique spécifié, utilisez la méthode `TryParse` statique implémentée par tous les types numériques primitifs, ainsi que par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>.  L'exemple suivant indique comment déterminer si « 108 » est un [int](../../../csharp/language-reference/keywords/int.md)valide.  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Si la chaîne contient des caractères non numériques ou que la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro au paramètre de sortie.  Sinon, il retourne la valeur true et définit le paramètre de sortie à la valeur numérique de la chaîne.  
  
> [!NOTE]
>  Une chaîne peut contenir des caractères numériques uniquement et n'être toujours pas valide pour le type de la méthode `TryParse` que vous utilisez.  Par exemple, « 256 » n'est pas une valeur valide pour `byte` mais est valide pour `int`. "  98.6 » n'est pas une valeur valide pour `int`, mais est valide pour `decimal`.  
  
## Exemple  
 Les exemples suivants indiquent comment utiliser `TryParse` avec les représentations sous forme de chaîne des valeurs `long`, `byte` et `decimal`.  
  
 [!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## Programmation fiable  
 Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne ne correspond pas à un nombre valide.  La méthode `TryParse` est généralement plus efficace car elle retourne simplement la valeur false si le nombre n'est pas valide.  
  
## Sécurité .NET Framework  
 Utilisez toujours les méthodes `TryParse` ou `Parse` pour valider l'entrée d'utilisateur de contrôles comme les zones de texte et les zones de liste déroulante.  
  
## Voir aussi  
 [Comment : convertir un tableau de byte en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)   
 [Comment : convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)   
 [Comment : effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)   
 [Analyse de chaînes numériques](../Topic/Parsing%20Numeric%20Strings%20in%20the%20.NET%20Framework.md)   
 [Mise en forme des types](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)