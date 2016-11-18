---
title: "Chaînes de format TimeSpan standard"
description: "Chaînes de format TimeSpan standard"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 4e0f02f1-4abd-47b5-8995-5c3ff45b0ce1
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: bb209c7bac71960fa0a679e546bedae486b412b8

---

# <a name="standard-timespan-format-strings"></a>Chaînes de format TimeSpan standard

Une chaîne de format [TimeSpan](xref:System.TimeSpan) standard utilise un spécificateur de format unique pour définir la représentation textuelle d’une valeur [TimeSpan](xref:System.TimeSpan) qui résulte d’une opération de mise en forme. Toute chaîne de format contenant plusieurs caractères, espace blanc compris, est interprétée comme une chaîne de format [TimeSpan](xref:System.TimeSpan) personnalisée. Pour plus d’informations, consultez [Chaînes de format numériques personnalisées](custom-timespan.md).

Les représentations sous forme de chaîne de valeurs [TimeSpan](xref:System.TimeSpan) sont produites par des appels aux surcharges de la méthode [TimeSpan.ToString](xref:System.TimeSpan.ToString), ainsi que par les méthodes qui prennent en charge la mise en forme composite, telles que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Pour plus d’informations, consultez [Mise en forme des types](formatting-types.md) et [Mise en forme composite](composite-format.md). L’exemple suivant illustre l’utilisation de chaînes de format standard dans des opérations de mise en forme.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan duration = new TimeSpan(1, 12, 23, 62);
      string output = "Time of Travel: " + duration.ToString("c");
      Console.WriteLine(output);

      Console.WriteLine("Time of Travel: {0:c}", duration); 
   }
}
// The example displays the following output:
//       Time of Travel: 1.12:24:02
//       Time of Travel: 1.12:24:02
```

```vb
Module Example
   Public Sub Main()
      Dim duration As New TimeSpan(1, 12, 23, 62)
      Dim output As String = "Time of Travel: " + duration.ToString("c")
      Console.WriteLine(output)

      Console.WriteLine("Time of Travel: {0:c}", duration) 
   End Sub
End Module
' The example displays the following output:
'       Time of Travel: 1.12:24:02
'       Time of Travel: 1.12:24:02
```

Les chaînes de format [TimeSpan](xref:System.TimeSpan) standard sont également utilisées par les méthodes [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) et [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)) pour définir le format requis des chaînes d’entrée pour les opérations d’analyse. (L'analyse convertit la représentation sous forme de chaîne d'une valeur en cette valeur.) L'exemple suivant illustre l'utilisation de chaînes de format standard dans des opérations d'analyse.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value = "1.03:14:56.1667";
      TimeSpan interval;
      try {
         interval = TimeSpan.ParseExact(value, "c", null);
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      }   
      catch (FormatException) {
         Console.WriteLine("{0}: Bad Format", value);
      }   
      catch (OverflowException) {
         Console.WriteLine("{0}: Out of Range", value);
      }

      if (TimeSpan.TryParseExact(value, "c", null, out interval))
         Console.WriteLine("Converted '{0}' to {1}", value, interval);
      else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value);
   }
}
// The example displays the following output:
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
//       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

```vb
Module Example
   Public Sub Main()
      Dim value As String = "1.03:14:56.1667"
      Dim interval As TimeSpan
      Try
         interval = TimeSpan.ParseExact(value, "c", Nothing)
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Catch e As FormatException
         Console.WriteLine("{0}: Bad Format", value)
      Catch e As OverflowException
         Console.WriteLine("{0}: Out of Range", value)
      End Try

      If TimeSpan.TryParseExact(value, "c", Nothing, interval) Then
         Console.WriteLine("Converted '{0}' to {1}", value, interval)
      Else
         Console.WriteLine("Unable to convert {0} to a time interval.", 
                           value)
      End If                
   End Sub
End Module
' The example displays the following output:
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
'       Converted '1.03:14:56.1667' to 1.03:14:56.1667000
```

Le tableau suivant répertorie les spécificateurs de format d'intervalle de temps standard.

Spécificateur de format | Nom | Description | Exemples
---------------- | ---- | ----------- | --------
"c" | Format constant (invariant) | Ce spécificateur ne dépend pas de la culture. Il prend la forme [-][d’.’]hh’:’mm’:’ss[‘.’fffffff]. (les chaînes de format "t" et "T" produisent les mêmes résultats) | `TimeSpan.Zero -> 00:00:00`; `New TimeSpan(0, 0, 30, 0) -> 00:30:00`; `New TimeSpan(3, 17, 25, 30, 500) -> 3.17:25:30.5000000`
"g" | Format court général | Ce spécificateur retourne uniquement ce qui est nécessaire. Il dépend de la culture et prend la forme [-][d’:’]h’:’mm’:’ss[.FFFFFFF]. | `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50.5 (en-US)`; `New TimeSpan(1, 3, 16, 50, 500) -> 1:3:16:50,5 (fr-FR)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50.599 (en-US)`; `New TimeSpan(1, 3, 16, 50, 599) -> 1:3:16:50,599 (fr-FR)`
"G" | Format long général | Ce spécificateur retourne toujours les jours et sept chiffres fractionnaires. Il dépend de la culture et prend la forme [-]d’:’hh’:’mm’:’ss.fffffff. | `New TimeSpan(18, 30, 0) -> 0:18:30:00.0000000 (en-US)`; `New TimeSpan(18, 30, 0) -> 0:18:30:00,0000000 (fr-FR)` 

## <a name="the-constant-c-format-specifier"></a>Spécificateur de format constant ("c")

Le spécificateur de format « c » retourne la représentation sous forme de chaîne d’une valeur [TimeSpan](xref:System.TimeSpan) au format suivant :

[-][_d_.]_hh_:_mm_:_ss_[._fffffff_]

Les éléments entre crochets ([ et ]) sont facultatifs. Le point (.) et les deux-points (:) sont des symboles littéraux. Le tableau suivant décrit les éléments restants. 

Élément | Description
------- | -----------
- | Signe négatif facultatif, qui indique un intervalle de temps négatif.
*d* | Nombre facultatif de jours, sans zéros non significatifs.
*hh* | Nombre d'heures, allant de "00" à "23".
*mm* | Nombre de minutes, allant de "00" à "59".
*ss* | Nombre de secondes, allant de "0" à "59".
*fffffff* | Partie fractionnaire facultative d'une seconde. Sa valeur peut varier de « 0000001 » (une graduation ou un dix-millionième de seconde) à « 9999999 » (9 999 999 dix-millionièmes de seconde ou une seconde moins une graduation). 

Contrairement aux spécificateurs de format "g" et "G", le spécificateur de format "c" ne dépend pas de la culture. Il produit la représentation sous forme de chaîne d’une valeur [TimeSpan](xref:System.TimeSpan) qui est invariante et commune à toutes les versions du .NET Framework antérieures au .NET Framework 4. « c » est la chaîne de format [TimeSpan](xref:System.TimeSpan) par défaut. La méthode [TimeSpan.ToString](xref:System.TimeSpan.ToString) met en forme une valeur d’intervalle de temps à l’aide de la chaîne de format « c ».

> [!NOTE]
> [TimeSpan](xref:System.TimeSpan) prend également en charge les chaînes de format standard « t » et « T », dont le comportement est identique à celui de la chaîne de format standard « c ».

L’exemple suivant instancie deux objets [TimeSpan](xref:System.TimeSpan), les utilise pour effectuer des opérations arithmétiques, puis affiche le résultat. Dans chaque cas, il utilise la mise en forme composite pour afficher la valeur [TimeSpan](xref:System.TimeSpan) à l’aide du spécificateur de format « c ».

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);

      interval1 = new TimeSpan(0, 0, 1, 14, 365);
      interval2 = TimeSpan.FromTicks(2143756);  
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       07:45:16 - 18:12:38 = -10:27:22
//       07:45:16 + 18:12:38 = 1.01:57:54
//       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

```vb
Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:c} - {1:c} = {2:c}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)

      interval1 = New TimeSpan(0, 0, 1, 14, 365)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:c} + {1:c} = {2:c}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       07:45:16 - 18:12:38 = -10:27:22
'       07:45:16 + 18:12:38 = 1.01:57:54
'       00:01:14.3650000 + 00:00:00.2143756 = 00:01:14.5793756
```

## <a name="the-general-short-g-format-specifier"></a>Spécificateur de format court général ("g")

Le spécificateur de format [TimeSpan](xref:System.TimeSpan) « g » retourne la représentation sous forme de chaîne d’une valeur [TimeSpan](xref:System.TimeSpan) dans un format compact, en incluant uniquement les éléments qui sont nécessaires. Son format est le suivant :

[-][_d_:]_h_:_mm_:_ss_[._FFFFFFF_]

Les éléments entre crochets ([ et ]) sont facultatifs. Le signe deux-points (:) est un symbole littéral. Le tableau suivant décrit les éléments restants.

Élément | Description
------- | -----------
- | Signe négatif facultatif, qui indique un intervalle de temps négatif.
*d* | Nombre facultatif de jours, sans zéros non significatifs.
*hh* | Nombre d'heures, allant de "0" à "23", sans zéros non significatifs. 
*mm* | Nombre de minutes, allant de "00" à "59".
*ss* | Nombre de secondes, allant de "0" à "59".
. | Séparateur des fractions de seconde.
*FFFFFFF* | Fractions de seconde. Le moins de chiffres possible sont affichés.

Tout comme le spécificateur de format "G", le spécificateur de format "g" est localisé. Son séparateur de fractions de seconde est basé sur la culture actuelle.

L’exemple suivant instancie deux objets [TimeSpan](xref:System.TimeSpan), les utilise pour effectuer des opérations arithmétiques, puis affiche le résultat. Dans chaque cas, il utilise la mise en forme composite pour afficher la valeur [TimeSpan](xref:System.TimeSpan) à l’aide du spécificateur de format « g ». De plus, il met en forme la valeur [TimeSpan](xref:System.TimeSpan) à l’aide des conventions de format de la culture système actuelle (dans le cas présent, Anglais - États-Unis ou en-US) et de la culture Français - France (fr-FR).

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       7:45:16 - 18:12:38 = -10:27:22
//       7:45:16 + 18:12:38 = 1:1:57:54
//       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:g} - {1:g} = {2:g}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:g} + {1:g} = {2:g}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       7:45:16 - 18:12:38 = -10:27:22
'       7:45:16 + 18:12:38 = 1:1:57:54
'       0:01:14.036 + 0:00:00.2143756 = 0:01:14.2503756
```

## <a name="the-general-long-g-format-specifier"></a>Spécificateur de format long général ("G")

Le spécificateur de format [TimeSpan](xref:System.TimeSpan) « G » retourne la représentation sous forme de chaîne d’une valeur [TimeSpan](xref:System.TimeSpan) sous une forme longue comprenant toujours les jours et les fractions de secondes. La chaîne qui résulte du spécificateur de format standard "G" est au format suivant :

[-]*d*:*hh*:*mm*:*ss*.*fffffff*

Les éléments entre crochets ([ et ]) sont facultatifs. Le signe deux-points (:) est un symbole littéral. Le tableau suivant décrit les éléments restants.

Élément | Description
------- | -----------
- | Signe négatif facultatif, qui indique un intervalle de temps négatif.
*d* | Nombre facultatif de jours, sans zéros non significatifs.
*hh* | Nombre d’heures, allant de 0 à 23. 
*mm* | Nombre de minutes, allant de "00" à "59".
*ss* | Nombre de secondes, allant de "0" à "59".
. | Séparateur des fractions de seconde.
*fffffff* | Fractions de seconde.

Tout comme le spécificateur de format "G", le spécificateur de format "g" est localisé. Son séparateur de fractions de seconde est basé sur la culture actuelle.

L’exemple suivant instancie deux objets [TimeSpan](xref:System.TimeSpan), les utilise pour effectuer des opérations arithmétiques, puis affiche le résultat. Dans chaque cas, il utilise la mise en forme composite pour afficher la valeur [TimeSpan](xref:System.TimeSpan) à l’aide du spécificateur de format « G ». De plus, il met en forme la valeur [TimeSpan](xref:System.TimeSpan) à l’aide des conventions de format de la culture système actuelle (dans le cas présent, Anglais - États-Unis ou en-US) et de la culture Français - France (fr-FR). 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      TimeSpan interval1, interval2;
      interval1 = new TimeSpan(7, 45, 16);
      interval2 = new TimeSpan(18, 12, 38);

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2));

      interval1 = new TimeSpan(0, 0, 1, 14, 36);
      interval2 = TimeSpan.FromTicks(2143756);      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2);
   }
}
// The example displays the following output:
//       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
//       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
//       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim interval1, interval2 As TimeSpan
      interval1 = New TimeSpan(7, 45, 16)
      interval2 = New TimeSpan(18, 12, 38)

      Console.WriteLine("{0:G} - {1:G} = {2:G}", interval1, 
                        interval2, interval1 - interval2)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), 
                        "{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2))

      interval1 = New TimeSpan(0, 0, 1, 14, 36)
      interval2 = TimeSpan.FromTicks(2143756)      
      Console.WriteLine("{0:G} + {1:G} = {2:G}", interval1, 
                        interval2, interval1 + interval2)
   End Sub
End Module
' The example displays the following output:
'       0:07:45:16.0000000 - 0:18:12:38.0000000 = -0:10:27:22.0000000
'       0:07:45:16,0000000 + 0:18:12:38,0000000 = 1:01:57:54,0000000
'       0:00:01:14.0360000 + 0:00:00:00.2143756 = 0:00:01:14.2503756
```

## <a name="see-also"></a>Voir aussi

[Mise en forme des types](formatting-types.md)

[Mise en forme composite](composite-format.md)

[Analyse de chaînes](parsing-strings.md)




<!--HONumber=Nov16_HO3-->


