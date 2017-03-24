---
title: "Types &#233;num&#233;ration (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "bits indicateurs (C#)"
  - "Langage C#, enums"
  - "énumérations (C#)"
  - "enums (C#)"
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Types &#233;num&#233;ration (Guide de programmation&#160;C#)
Un type énumération \(également nommé une énumération ou un enum\) offre un moyen efficace pour définir un jeu de constantes intégrales nommées qui peuvent être assignées à une variable.  Par exemple, supposons que vous devez définir une variable dont la valeur représente un jour de la semaine.  Cette variable ne stockera jamais plus de sept valeurs précises.  Pour définir ces valeurs, vous pouvez utiliser un type énumération, déclaré en utilisant le mot clé [enum](../../csharp/language-reference/keywords/enum.md).  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]  
  
 Par défaut, le type sous\-jacent de chaque élément de l'enum est [int](../../csharp/language-reference/keywords/int.md).  Vous pouvez spécifier un autre type numérique intégral en utilisant un deux\-points, comme l'illustre l'exemple précédent.  Pour obtenir la liste complète des types possibles, consultez [enum \(Référence C\#\)](../../csharp/language-reference/keywords/enum.md).  
  
 Vous pouvez vérifier les valeurs numériques sous\-jacentes par le cast en type sous\-jacent, comme indiqué dans l'exemple suivant.  
  
```c#  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 Voici les avantages que représente l'utilisation d'un enum au lieu d'un type numérique :  
  
-   Vous spécifiez clairement pour le code client les valeurs qui sont valides pour la variable.  
  
-   Dans [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)], IntelliSense répertorie les valeurs définies.  
  
 Lorsque vous ne spécifiez pas de valeurs pour les éléments de la liste d'énumérateurs, les valeurs sont incrémentées automatiquement d'une unité.  Dans l'exemple précédent, `Days.Sunday` a la valeur 0, `Days.Monday` a la valeur 1, etc.  Lorsque vous créez un objet `Days`, il aura une valeur par défaut de `Days.Sunday` \(0\) si vous ne lui assignez pas de valeur explicitement.  Lorsque vous créez un enum, sélectionnez la valeur par défaut la plus logique et donnez\-lui la valeur zéro.  Tous les enums auront alors cette valeur par défaut si aucune valeur ne leur est explicitement assignée lorsqu'ils sont créés.  
  
 Si la variable `meetingDay` est de type `Days`, vous pouvez uniquement \(sans un cast explicite\) lui assigner l'une des valeurs définies par `Days`.  Et si le jour de la réunion change, vous pouvez assigner une nouvelle valeur de `Days` à `meetingDay` :  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  Il est possible d'assigner n'importe quelle valeur entière arbitraire à `meetingDay`.  Par exemple, cette ligne de code ne produit pas d'erreur : `meetingDay = (Days) 42`.  Toutefois, vous ne devez pas procéder ainsi car le système s'attend implicitement à ce qu'une variable enum contienne seulement l'une des valeurs définies par l'enum.  Assigner une valeur arbitraire à une variable de type énumération présente un risque élevé d'erreurs.  
  
 Vous pouvez assigner n'importe quelle valeur aux éléments de la liste d'énumérateurs d'un type énumération et vous pouvez également utiliser des valeurs calculées :  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]  
  
## Types énumération comme bits indicateurs  
 Vous pouvez utiliser un type énumération pour définir des bits indicateurs, ce qui permet à une instance du type énumération de stocker n'importe quelle combinaison des valeurs définies dans la liste des énumérateurs.  \(Bien sûr, certaines combinaisons peuvent ne pas être significatives ou autorisées dans votre code de programme.\)  
  
 Vous créez un enum de bits indicateurs en appliquant l'attribut <xref:System.FlagsAttribute?displayProperty=fullName> et en définissant les valeurs de manière appropriée afin que les opérations au niveau du bit `AND`, `OR`, `NOT` et `XOR` puissent leur être appliquées.  Dans l'enum de bits indicateurs, incluez une constante nommée dont la valeur zéro signifie « aucun indicateur n'est défini ». N'attribuez pas de valeur zéro à un indicateur si elle ne signifie pas « aucun indicateur n'est défini ».  
  
 Dans l'exemple suivant, une autre version de l'enum `Days`, nommée `Days2`, est définie.  `Days2` a l'attribut `Flags` et la puissance de 2 supérieure suivante est assignée à chaque valeur.  Cela vous permet de créer une variable `Days2` dont la valeur est `Days2.Tuesday` et `Days2.Thursday`.  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]  
  
 Pour définir un indicateur sur un enum, utilisez l'opérateur `OR` au niveau du bit, comme indiqué dans l'exemple suivant :  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]  
  
 Pour déterminer si un indicateur spécifique est défini, utilisez une opération `AND` au niveau du bit, comme indiqué dans l'exemple suivant :  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]  
  
 Pour plus d'informations sur les éléments à prendre en compte lorsque vous définissez des types énumération avec l'attribut <xref:System.FlagsAttribute?displayProperty=fullName>, consultez <xref:System.Enum?displayProperty=fullName>.  
  
## Utilisation des méthodes System.Enum pour découvrir et manipuler des valeurs enum  
 Tous les enums sont des instances du type <xref:System.Enum?displayProperty=fullName>.  Vous ne pouvez pas dériver de nouvelles classes de <xref:System.Enum?displayProperty=fullName>, mais vous pouvez utiliser ses méthodes pour obtenir des informations sur les valeurs d'une instance enum et manipuler ces dernières.  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]  
  
 Pour plus d'informations, consultez <xref:System.Enum?displayProperty=fullName>.  
  
 Vous pouvez également créer une méthode pour un enum en utilisant une méthode d'extension.  Pour plus d'informations, consultez [Comment : créer une méthode pour une énumération](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).  
  
## Chapitre proposé  
 [Plus sur les variables](http://go.microsoft.com/fwlink/?LinkId=221230) dans [Démarrage Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Voir aussi  
 <xref:System.Enum?displayProperty=fullName>   
 [Guide de programmation C\#](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)