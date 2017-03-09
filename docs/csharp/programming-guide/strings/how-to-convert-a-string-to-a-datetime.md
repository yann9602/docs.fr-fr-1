---
title: "Comment&#160;: convertir une cha&#238;ne en DateTime (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "chaînes (C#), convertir en DateTime"
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# Comment&#160;: convertir une cha&#238;ne en DateTime (Guide de programmation&#160;C#)
Les programmes permettent couramment aux utilisateurs d’entrer des dates sous forme de valeurs de chaîne. Pour convertir une date basée sur une chaîne en objet <xref:System.DateTime?displayProperty=fullName>, vous pouvez utiliser la méthode <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> ou la méthode statique <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName>, comme le montre l’exemple suivant.  
  
 **Culture**.  Le format d’écriture des chaînes de date varie selon la culture.  Par exemple, aux États\-Unis, le 20 janvier 2008 s’écrit 01\/20\/2008.  En France, cette date lève l’exception InvalidFormatException. Cela vient du fait que la France utilise le format de date jour\/mois\/année, alors que les États\-Unis utilisent mois\/jour\/année.  
  
 Une chaîne telle que 20\/01\/2008 correspond donc bien au 20 janvier 2008 en France, mais elle lève l’exception InvalidFormatException aux États\-Unis  
  
 Pour déterminer vos paramètres de culture actuels, vous pouvez utiliser System.Globalization.CultureInfo.CurrentCulture.  
  
 Un exemple simple de conversion d’une chaîne en dateTime est présenté ci\-dessous.  
  
 Pour obtenir d’autres exemples de chaînes de date, consultez <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.  
  
```vb  
string dateTime = "01/08/2008 14:50:50.42"; DateTime dt = Convert.ToDateTime(dateTime); Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}", dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond); // Specify exactly how to interpret the string. IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true); // Alternate choice: If the string has been input by an end user, you might // want to format it according to the current culture: // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture; DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal); Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}", dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond /* Output (assuming first culture is en-US and second is fr-FR): Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420 Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420 Press any key to continue . . . */  
```  
  
## Exemple  
 [!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#13)]  
  
## Voir aussi  
 [Chaînes](../../../csharp/programming-guide/strings/index.md)