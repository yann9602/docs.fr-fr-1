---
title: "Date Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Date"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Date data type"
  - "dates, Visual Basic data types"
  - "times, Date data type"
  - "Date literals"
  - "data values"
  - "times, Visual Basic data types"
  - "dates, Date data type"
  - "data types [Visual Basic], assigning"
  - "literals, Date"
  - "# specifier for Date literals"
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Date Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Contient des valeurs sous la forme IEEE 64 bits \(8 octets\) qui représentent des dates comprises entre le 1er janvier de l'année 0001 et le 31 décembre de l'année 9999 et des heures comprises entre de 0:00:00 \(minuit\) et 23:59:59,9999999.  Chaque incrément représente 100 nanosecondes de durée calendaire depuis le début du 1er janvier de l'année 1 du calendrier grégorien.  La valeur maximale représente 100 nanosecondes avant le début du 1er janvier de l'année 10 000.  
  
## Notes  
 Utilisez le type de données `Date` comme conteneur de valeurs de date, de valeurs d'heure ou de valeurs de date et d'heure.  
  
 La valeur par défaut de `Date` est 0:00:00 \(minuit\) le 1er janvier 0001.  
  
 Vous pouvez obtenir les date et heure actuelles à partir de la classe <xref:Microsoft.VisualBasic.DateAndTime>.  
  
## Exigences relatives au format  
 Vous devez placer un littéral `Date` entre des signes dièse \(`# #`\).  Vous devez spécifier la valeur de date au format M\/j\/aaaa, par exemple `#5/31/1993#`, ou aaaa\-MM\-jj, par exemple `#1993-5-31#`.  Vous pouvez utiliser des barres obliques quand vous spécifiez l'année en premier.  Cette exigence est indépendante de vos paramètres régionaux et des paramètres de format de date et d'heure de votre ordinateur.  
  
 Cette restriction tient au fait que la signification de votre code ne doit jamais changer en fonction des paramètres régionaux dans lesquels votre application s'exécute.  Supposez que vous codez en dur un littéral `Date` égal à `#3/4/1998#` et qu'il doit correspondre au 4 mars 1998.  Dans des paramètres régionaux qui utilisent le format mm\/jj\/aaaa, la date 3\/4\/1998 est compilée comme vous le souhaitez.  Supposons toutefois que vous déployiez votre application dans de nombreux pays.  Dans des paramètres régionaux qui utilisent le format jj\/mm\/aaaa, votre littéral codé en dur sera compilé en tant que 3 avril 1998.  Dans des paramètres régionaux qui utilisent le format aaaa\/mm\/jj, le littéral sera non valide \(avril 1998, 0003\) et provoquera une erreur du compilateur.  
  
## Solutions  
 Pour convertir un littéral `Date` dans le format de vos paramètres régionaux ou dans un format personnalisé, fournissez le littéral à la fonction <xref:Microsoft.VisualBasic.Strings.Format%2A>, en spécifiant un format de date prédéfini ou défini par l'utilisateur.  Cela est illustré par l'exemple suivant.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Vous pouvez également utiliser un des constructeurs surchargés de la structure <xref:System.DateTime> pour assembler une valeur de date et d'heure.  L'exemple suivant crée une valeur pour représenter le 31 mai 1993 à 12h14.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)   
```  
  
## Format d'heure  
 Vous pouvez spécifier la valeur d'heure dans un format de 12 heures ou de 24 heures, par exemple `#1:15:30 PM#` ou `#13:15:30#`.  Toutefois, si vous ne spécifiez pas les minutes ou les secondes, vous devez spécifier AM ou PM.  
  
## Valeurs par défaut de date et d'heure  
 Si vous n'incluez pas de date dans un littéral de date\/heure, Visual Basic définit la partie date de la valeur sur le 1er janvier 0001.  Si vous n'incluez pas d'heure dans un littéral de date\/heure, Visual Basic définit la partie heure de la valeur sur le début de la journée, c'est\-à\-dire minuit \(0:00:00\).  
  
## Conversions de type  
 Si vous convertissez une valeur `Date` vers le type `String`, Visual Basic restitue la date en fonction du format de date courte spécifié par les paramètres régionaux d'exécution, et restitue l'heure en fonction du format d'heure \(12 heures ou 24 heures\) spécifié par les paramètres régionaux d'exécution.  
  
## Conseils de programmation  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, tels que des objets Automation ou COM, n'oubliez pas que les types de date et d'heure utilisés dans les autres environnements ne sont pas compatibles avec le type `Date` de Visual Basic.  Si vous transmettez un argument de date et d'heure à un tel composant, déclarez\-le en tant que `Double` et non `Date` dans votre nouveau code Visual Basic, et utilisez les méthodes de conversion <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> et <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>.  
  
-   **Caractères de type.** `Date` n'a aucun caractère de type littéral ni caractère de type identificateur.  Toutefois, le compilateur traite les littéraux compris entre des signes dièse \(`# #`\) en tant que `Date`.  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.DateTime?displayProperty=fullName>.  
  
## Exemple  
 Une variable ou une constante du type de données `Date` contient à la fois la date et l'heure.  L'exemple suivant illustre ce comportement.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## Voir aussi  
 <xref:System.DateTime?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Chaînes de format de date et d'heure standard](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)   
 [Chaînes de format de date et d'heure personnalisées](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)