---
title: "Chaînes de format TimeSpan personnalisées"
description: "Chaînes de format TimeSpan personnalisées"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e79745eb-6ebd-4e62-85c4-4f2830c27285
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bec60437d4345decaf38f2bbb9434922ac889683
ms.lasthandoff: 03/03/2017

---

# <a name="custom-timespan-format-strings"></a>Chaînes de format TimeSpan personnalisées

Une chaîne de format [TimeSpan](xref:System.TimeSpan) définit la représentation sous forme de chaîne d’une valeur [TimeSpan](xref:System.TimeSpan) qui résulte d’une opération de mise en forme. Une chaîne de format personnalisée se compose d’un ou plusieurs spécificateurs de format [TimeSpan](xref:System.TimeSpan) personnalisé et d’un nombre quelconque de caractères littéraux. Toute chaîne autre qu’une chaîne de format [TimeSpan standard](standard-timespan.md) est interprétée comme chaîne de format [TimeSpan](xref:System.TimeSpan) personnalisée.

> [!IMPORTANT]
> Les spécificateurs de format [TimeSpan](xref:System.TimeSpan) personnalisé n’incluent pas de symboles de séparateur d’espace réservé, tels que les symboles qui séparent les jours des heures, les heures des minutes ou les secondes des fractions de seconde. Au lieu de cela, ces symboles doivent figurer dans la chaîne de format personnalisée comme littéraux de chaîne. Par exemple, `"dd\.hh\:mm"` définit un point (.) comme séparateur entre les jours et les heures et un signe deux-points (:) comme séparateur entre les heures et les minutes. 

> En outre, les spécificateurs de format [TimeSpan](xref:System.TimeSpan) personnalisé n’incluent pas un symbole de signe permettant de faire la distinction entre les intervalles de temps positifs et négatifs. Pour inclure un symbole de signe, vous devez construire une chaîne de format à l’aide d’une logique conditionnelle. La section [Autres caractères](#other-characters) présente un exemple. 

Les représentations sous forme de chaîne de valeurs [TimeSpan](xref:System.TimeSpan) sont produites par des appels aux surcharges de la méthode [TimeSpan](xref:System.TimeSpan) `ToString`, ainsi que par les méthodes qui prennent en charge la mise en forme composite, telles que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Pour plus d’informations, consultez [Mise en forme des types](formatting-types.md) et [Mise en forme composite](composite-format.md). L'exemple suivant illustre l'utilisation de chaînes de format standard dans des opérations de mise en forme.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan duration = new TimeSpan(1, 12, 23, 62);

      string output = null;
      output = "Time of Travel: " + duration.ToString("%d") + " days";
      Console.WriteLine(output);
      output = "Time of Travel: " + duration.ToString(xref:"dd\.hh\:mm\:ss"); 
      Console.WriteLine(output);

      Console.WriteLine("Time of Travel: {0:%d} day(s)", duration);
      Console.WriteLine("Time of Travel: {0:dd\\.hh\\:mm\\:ss} days", duration);
   }
}
// The example displays the following output:
//       Time of Travel: 1 days
//       Time of Travel: 01.12:24:02
//       Time of Travel: 1 day(s)
//       Time of Travel: 01.12:24:02 days
```

```vb
Module Example
   Public Sub Main()
      Dim duration As New TimeSpan(1, 12, 23, 62)

      Dim output As String = Nothing
      output = "Time of Travel: " + duration.ToString("%d") + " days"
      Console.WriteLine(output)
      output = "Time of Travel: " + duration.ToString("dd\.hh\:mm\:ss") 
      Console.WriteLine(output)

      Console.WriteLine("Time of Travel: {0:%d} day(s)", duration)
      Console.WriteLine("Time of Travel: {0:dd\.hh\:mm\:ss} days", duration)
   End Sub
End Module
' The example displays the following output:
'       Time of Travel: 1 days
'       Time of Travel: 01.12:24:02
'       Time of Travel: 1 day(s)
'       Time of Travel: 01.12:24:02 days
```

Les chaînes de format [TimeSpan](xref:System.TimeSpan) personnalisées sont également utilisées par les méthodes [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) et [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)) pour définir le format requis des chaînes d’entrée pour les opérations d’analyse. (L'analyse convertit la représentation sous forme de chaîne d'une valeur en cette valeur.) L'exemple suivant illustre l'utilisation de chaînes de format standard dans des opérations d'analyse.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value = null;
      TimeSpan interval;

      value = "6";
      if (TimeSpan.TryParseExact(value, "%d", null, out interval))
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"));
      else
         Console.WriteLine("Unable to parse '{0}'", value);

      value = "16:32.05";
      if (TimeSpan.TryParseExact(value, @"mm\:ss\.ff", null, out interval))
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"));
      else
         Console.WriteLine("Unable to parse '{0}'", value);

      value= "12.035";
      if (TimeSpan.TryParseExact(value, "ss\\.fff", null, out interval))
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"));
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       6 --> 6.00:00:00
//       16:32.05 --> 00:16:32.0500000
//       12.035 --> 00:00:12.0350000
```

```vb
Module Example
   Public Sub Main()
      Dim value As String = Nothing
      Dim interval As TimeSpan

      value = "6"
      If TimeSpan.TryParseExact(value, "%d", Nothing, interval) Then
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"))
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If

      value = "16:32.05"
      If TimeSpan.TryParseExact(value, "mm\:ss\.ff", Nothing, interval) Then
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"))
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If

      value= "12.035"
      If TimeSpan.TryParseExact(value, "ss\.fff", Nothing, interval) Then
         Console.WriteLine("{0} --> {1}", value, interval.ToString("c"))
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       6 --> 6.00:00:00
'       16:32.05 --> 00:16:32.0500000
'       12.035 --> 00:00:12.0350000
```

Le tableau suivant décrit les spécificateurs de format de date et d'heure personnalisés.

Spécificateur de format | Description | Exemples
---------------- | ----------- | --------
"d", "%d" | Nombre de jours entiers dans l’intervalle de temps. | `new TimeSpan(6, 14, 32, 17, 685):` `%d --> "6"`;  `d\.hh\:mm --> "6.14:32"`
"dd", "dddddddd" | Nombre de jours entiers dans l’intervalle de temps, complété avec des zéros non significatifs en fonction des besoins. | `new TimeSpan(6, 14, 32, 17, 685):` `ddd --> "006"`; `dd\.hh\:mm --> "06.14:32"`
"h", "%h" | Nombre d’heures entières dans l’intervalle de temps qui ne sont pas comptabilisées dans des jours. Les heures à un chiffre n’ont pas de zéro non significatif. | `new TimeSpan(6, 14, 32, 17, 685):` `%h --> "14"`; `hh\:mm --> "14:32"`
"hh" | Nombre d’heures entières dans l’intervalle de temps qui ne sont pas comptabilisées dans des jours. Les heures à un chiffre ont un zéro non significatif. | `new TimeSpan(6, 14, 32, 17, 685):` `hh --> "14"`  `new TimeSpan(6, 8, 32, 17, 685):` `hh --> 08`
"m", "%m" | Nombre de minutes entières dans l’intervalle de temps qui ne sont pas incluses dans des jours ou des heures. Les minutes à un chiffre n’ont pas de zéro non significatif. | `new TimeSpan(6, 14, 8, 17, 685):` `%m --> "8"`; `h\:m --> "14:8"`
"mm" | Nombre de minutes entières dans l’intervalle de temps qui ne sont pas incluses dans des jours ou des heures. Les minutes à un chiffre ont un zéro non significatif. | `new TimeSpan(6, 14, 8, 17, 685):` `mm --> "08"` `new TimeSpan(6, 8, 5, 17, 685):` `d\.hh\:mm\:ss --> 6.08:05:17`
"s", "%s" | Nombre de secondes entières dans l’intervalle de temps qui ne sont pas incluses dans des jours, heures ou minutes. Les secondes à un chiffre n’ont pas de zéro non significatif. | `TimeSpan.FromSeconds(12.965):` `%s --> 12`; `s\.fff --> 12.965`
"ss" | Nombre de secondes entières dans l’intervalle de temps qui ne sont pas incluses dans des jours, heures ou minutes. Les secondes à un chiffre ont un zéro non significatif. | `TimeSpan.FromSeconds(6.965):` `ss --> 06`; `ss\.fff --> 06.965`
"f", "%f" | Dixièmes de seconde dans un intervalle de temps. | `TimeSpan.FromSeconds(6.895):` `f --> 8`; `ss\.f --> 06.8`
"ff" | Centièmes de seconde dans un intervalle de temps. | `TimeSpan.FromSeconds(6.895):` `ff --> 89`; `ss\.ff --> 06.89`
"fff" | Millisecondes dans un intervalle de temps. | `TimeSpan.FromSeconds(6.895):` `fff --> 895`; `ss\.fff --> 06.895`
"ffff" | Dix millièmes de seconde dans un intervalle de temps. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 8954`; `ss\.ffff --> 06.8954`
"fffff" | Cent millièmes de seconde dans un intervalle de temps. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 89543`; `ss\.ffff --> 06.89543`
"ffffff" | Millionièmes de seconde dans un intervalle de temps. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 895432`; `ss\.ffff --> 06.895432`
"fffffff" | Dix millionièmes de seconde (ou nombre fractionnaire de graduations) dans un intervalle de temps. | `TimeSpan.Parse("0:0:6.8954321"):` `ffff --> 8954321`; `ss\.ffff --> 06.8954321`
"F", "%F" | Dixièmes de seconde dans un intervalle de temps. Rien ne s'affiche si le chiffre est zéro. | `TimeSpan.Parse("00:00:06.32"):` `%F: 3`  `TimeSpan.Parse("0:0:3.091"):` `ss\.F: 03.`
"FF" | Centièmes de seconde dans un intervalle de temps. Tous les zéros de fin fractionnaires ou deux chiffres zéro ne sont pas affichés. |  `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 32`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFF" | Millisecondes dans un intervalle de temps. Tous les zéros de fin fractionnaires ne sont pas affichés. |  `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 329`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFF" | Dix millièmes de seconde dans un intervalle de temps. Tous les zéros de fin fractionnaires ne sont pas affichés. |  `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 3291`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFFF" | Cent millièmes de seconde dans un intervalle de temps. Tous les zéros de fin fractionnaires ne sont pas affichés. | `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 32917`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFFFF" | Millionièmes de seconde dans un intervalle de temps. Tous les zéros de fin fractionnaires ne sont pas affichés. | `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 329179`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.1`
"FFFFFFF" | Dix millionièmes de seconde dans un intervalle de temps. Tous les zéros de fin fractionnaires ou sept zéros ne sont pas affichés. | `TimeSpan.Parse("00:00:06.3291791"):` `FFFFFF: 3291791`  `TimeSpan.Parse("0:0:3.1900000"):` `ss\.FFFFFF: 03.19`
'chaîne' | Délimiteur de chaîne littérale | `new TimeSpan(14, 32, 17):` `hh':'mm':'ss --> "14:32:17"`
\ | Caractère d'échappement. | `new TimeSpan(14, 32, 17):` `hh\:mm\:ss --> "14:32:17"`
N'importe quel autre caractère | Tout autre caractère sans séquence d’échappement est interprété comme un spécificateur de format personnalisé. | `new TimeSpan(14, 32, 17):` `hh\:mm\:ss --> "14:32:17"`

## <a name="the-d-custom-format-specifier"></a>Spécificateur de format personnalisé "d"

Le spécificateur de format personnalisé "d" affiche la valeur de la propriété [TimeSpan.Days](xref:System.TimeSpan.Days), qui représente le nombre de jours entiers dans l’intervalle de temps. Il affiche le nombre total de jours dans une valeur [TimeSpan](xref:System.TimeSpan), même si la valeur a plusieurs chiffres. Si la valeur de la propriété [TimeSpan.Days](xref:System.TimeSpan.Days) est zéro, le spécificateur retourne « 0 ».

Si le spécificateur de format personnalisé "d" est utilisé seul, spécifiez "%d" afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

```csharp
TimeSpan ts1 = new TimeSpan(16, 4, 3, 17, 250);
Console.WriteLine(ts1.ToString("%d"));
// Displays 16
```

```vb
Dim ts As New TimeSpan(16, 4, 3, 17, 250)
Console.WriteLine(ts.ToString("%d"))
' Displays 16 
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "d".

```csharp
TimeSpan ts2 = new TimeSpan(4, 3, 17);
Console.WriteLine(ts2.ToString(xref:"d\.hh\:mm\:ss"));

TimeSpan ts3 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine(ts3.ToString(xref:"d\.hh\:mm\:ss"));
// The example displays the following output:
//       0.04:03:17
//       3.04:03:17
```

```vb
Dim ts2 As New TimeSpan(4, 3, 17)
Console.WriteLine(ts2.ToString("d\.hh\:mm\:ss"))

Dim ts3 As New TimeSpan(3, 4, 3, 17)
Console.WriteLine(ts3.ToString("d\.hh\:mm\:ss"))
' The example displays the following output:
'       0.04:03:17
'       3.04:03:17
```

## <a name="the-dd-dddddddd-custom-format-specifiers"></a>Spécificateurs de format personnalisé "dd" à "dddddddd"

Les spécificateurs de format personnalisé "dd", "ddd", "dddd", "ddddd", "dddddd", "ddddddd" et "dddddddd" affichent la valeur de la propriété [TimeSpan.Days](xref:System.TimeSpan.Days), qui représente le nombre de jours entiers dans l’intervalle de temps. 

La chaîne de sortie inclut un nombre minimal de chiffres spécifié par le nombre de caractères « d » dans le spécificateur de format, et elle est remplie avec des zéros non significatifs en fonction des besoins. Si les chiffres dans le nombre de jours dépassent le nombre de caractères « d » dans le spécificateur de format, le nombre total de jours est affiché dans la chaîne de résultat.

L’exemple suivant utilise ces spécificateurs de format pour afficher la représentation sous forme de chaîne de deux valeurs [TimeSpan](xref:System.TimeSpan). La valeur du composant « jours » du premier intervalle de temps est zéro ; la valeur du composant « jours » du deuxième est 365.

```csharp
TimeSpan ts1 = new TimeSpan(0, 23, 17, 47);
TimeSpan ts2 = new TimeSpan(365, 21, 19, 45);

for (int ctr = 2; ctr <= 8; ctr++)
{
   string fmt = new String('d', ctr) + @"\.hh\:mm\:ss";
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts1);  
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts2);
   Console.WriteLine();
}  
// The example displays the following output:
//       dd\.hh\:mm\:ss --> 00.23:17:47
//       dd\.hh\:mm\:ss --> 365.21:19:45
//       
//       ddd\.hh\:mm\:ss --> 000.23:17:47
//       ddd\.hh\:mm\:ss --> 365.21:19:45
//       
//       dddd\.hh\:mm\:ss --> 0000.23:17:47
//       dddd\.hh\:mm\:ss --> 0365.21:19:45
//       
//       ddddd\.hh\:mm\:ss --> 00000.23:17:47
//       ddddd\.hh\:mm\:ss --> 00365.21:19:45
//       
//       dddddd\.hh\:mm\:ss --> 000000.23:17:47
//       dddddd\.hh\:mm\:ss --> 000365.21:19:45
//       
//       ddddddd\.hh\:mm\:ss --> 0000000.23:17:47
//       ddddddd\.hh\:mm\:ss --> 0000365.21:19:45
//       
//       dddddddd\.hh\:mm\:ss --> 00000000.23:17:47
//       dddddddd\.hh\:mm\:ss --> 00000365.21:19:45
```

```vb
Dim ts1 As New TimeSpan(0, 23, 17, 47)
Dim ts2 As New TimeSpan(365, 21, 19, 45)

For ctr As Integer = 2 To 8
   Dim fmt As String = New String("d"c, ctr) + "\.hh\:mm\:ss"
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts1) 
   Console.WriteLine("{0} --> {1:" + fmt + "}", fmt, ts2)
   Console.WriteLine()
Next  
' The example displays the following output:
'       dd\.hh\:mm\:ss --> 00.23:17:47
'       dd\.hh\:mm\:ss --> 365.21:19:45
'       
'       ddd\.hh\:mm\:ss --> 000.23:17:47
'       ddd\.hh\:mm\:ss --> 365.21:19:45
'       
'       dddd\.hh\:mm\:ss --> 0000.23:17:47
'       dddd\.hh\:mm\:ss --> 0365.21:19:45
'       
'       ddddd\.hh\:mm\:ss --> 00000.23:17:47
'       ddddd\.hh\:mm\:ss --> 00365.21:19:45
'       
'       dddddd\.hh\:mm\:ss --> 000000.23:17:47
'       dddddd\.hh\:mm\:ss --> 000365.21:19:45
'       
'       ddddddd\.hh\:mm\:ss --> 0000000.23:17:47
'       ddddddd\.hh\:mm\:ss --> 0000365.21:19:45
'       
'       dddddddd\.hh\:mm\:ss --> 00000000.23:17:47
'       dddddddd\.hh\:mm\:ss --> 00000365.21:19:45
```

## <a name="the-h-custom-format-specifier"></a>Spécificateur de format personnalisé "h"

Le spécificateur de format personnalisé "h" affiche la valeur de la propriété [TimeSpan.Hours](xref:System.TimeSpan.Hours), qui représente le nombre d’heures entières dans l’intervalle de temps non comptabilisées dans le composant « jour ». Il retourne une valeur de chaîne à un chiffre si la valeur de la propriété [TimeSpan.Hours](xref:System.TimeSpan.Hours) est comprise entre 0 et 9, ou une valeur de chaîne à deux chiffres si la valeur de la propriété [TimeSpan.Hours](xref:System.TimeSpan.Hours) est comprise entre 10 et 23.

Si le spécificateur de format personnalisé "h" est utilisé seul, spécifiez "%h" afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

```csharp
TimeSpan ts = new TimeSpan(3, 42, 0);
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts);
// The example displays the following output:
//       3 hours 42 minutes
```

```vb
Dim ts As New TimeSpan(3, 42, 0)
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts)
' The example displays the following output:
'       3 hours 42 minutes
```

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "%h" à la place pour interpréter la chaîne numérique comme nombre d’heures. L'exemple suivant illustre cette situation.

```csharp
string value = "8";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "%h", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       08:00:00
```

```vb
Dim value As String = "8"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "%h", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       08:00:00
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "h".

```csharp
TimeSpan ts1 = new TimeSpan(14, 3, 17);
Console.WriteLine(ts1.ToString(xref:"d\.h\:mm\:ss"));

TimeSpan ts2 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine(ts2.ToString(xref:"d\.h\:mm\:ss"));
// The example displays the following output:
//       0.14:03:17
//       3.4:03:17
```

```vb
Dim ts1 As New TimeSpan(14, 3, 17)
Console.WriteLine(ts1.ToString("d\.h\:mm\:ss"))

Dim ts2 As New TimeSpan(3, 4, 3, 17)
Console.WriteLine(ts2.ToString("d\.h\:mm\:ss"))
' The example displays the following output:
'       0.14:03:17
'       3.4:03:17
```

## <a name="the-hh-custom-format-specifier"></a>Spécificateur de format personnalisé "hh"

Le spécificateur de format personnalisé "hh" affiche la valeur de la propriété [TimeSpan.Hours](xref:System.TimeSpan.Hours), qui représente le nombre d’heures entières dans l’intervalle de temps non comptabilisées dans le composant « jour ». Pour les valeurs 0 à 9, la chaîne de sortie inclut un zéro non significatif. 

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "hh" à la place pour interpréter la chaîne numérique comme nombre d’heures. L'exemple suivant illustre cette situation.

```csharp
string value = "08";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "hh", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       08:00:00 
```

```vb
Dim value As String = "08"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "hh", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       08:00:00
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "hh".

```csharp
TimeSpan ts1 = new TimeSpan(14, 3, 17);
Console.WriteLine(ts1.ToString(xref:"d\.hh\:mm\:ss"));

TimeSpan ts2 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine(ts2.ToString(xref:"d\.hh\:mm\:ss"));
// The example displays the following output:
//       0.14:03:17
//       3.04:03:17
```

```vb
Dim ts1 As New TimeSpan(14, 3, 17)
Console.WriteLine(ts1.ToString("d\.hh\:mm\:ss"))

Dim ts2 As New TimeSpan(3, 4, 3, 17)
Console.WriteLine(ts2.ToString("d\.hh\:mm\:ss"))
' The example displays the following output:
'       0.14:03:17
'       3.04:03:17
```

## <a name="the-m-custom-format-specifier"></a>Spécificateur de format personnalisé "m"

Le spécificateur de format personnalisé "m" affiche la valeur de la propriété [TimeSpan.Minutes](xref:System.TimeSpan.Minutes), qui représente le nombre de minutes entières dans l’intervalle de temps non comptabilisées dans le composant « jour ». Il retourne une valeur de chaîne à un chiffre si la valeur de la propriété [TimeSpan.Minutes](xref:System.TimeSpan.Minutes) est comprise entre 0 et 9, ou une valeur de chaîne à deux chiffres si la valeur de la propriété [TimeSpan.Minutes](xref:System.TimeSpan.Minutes) est comprise entre 10 et 59.

Si le spécificateur de format personnalisé "m" est utilisé seul, spécifiez "%m" afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

```csharp
TimeSpan ts = new TimeSpan(3, 42, 0);
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts);
// The example displays the following output:
//       3 hours 42 minutes
```

```vb
Dim ts As New TimeSpan(3, 42, 0)
Console.WriteLine("{0:%h} hours {0:%m} minutes", ts)
' The example displays the following output:
'       3 hours 42 minutes
```

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "%m" à la place pour interpréter la chaîne numérique comme nombre de minutes. L'exemple suivant illustre cette situation.

```csharp
string value = "3";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "%m", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       00:03:00
```

```vb
Dim value As String = "3"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "%m", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       00:03:00                              
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "m".

```csharp
TimeSpan ts1 = new TimeSpan(0, 6, 32);
Console.WriteLine("{0:m\\:ss} minutes", ts1);

TimeSpan ts2 = new TimeSpan(3, 4, 3, 17);
Console.WriteLine("Elapsed time: {0:m\\:ss}", ts2);
// The example displays the following output:
//       6:32 minutes
//       Elapsed time: 18:44
```

```vb
Dim ts1 As New TimeSpan(0, 6, 32)
Console.WriteLine("{0:m\:ss} minutes", ts1)

Dim ts2 As New TimeSpan(0, 18, 44)
Console.WriteLine("Elapsed time: {0:m\:ss}", ts2)
' The example displays the following output:
'       6:32 minutes
'       Elapsed time: 18:44
```

## <a name="the-mm-custom-format-specifier"></a>Spécificateur de format personnalisé "mm"

Le spécificateur de format personnalisé "mm" affiche la valeur de la propriété [TimeSpan.Minutes](xref:System.TimeSpan.Minutes), qui représente le nombre de minutes entières dans l’intervalle de temps non incluses dans les composants « jours » ou « heures ». Pour les valeurs 0 à 9, la chaîne de sortie inclut un zéro non significatif. 

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "mm" à la place pour interpréter la chaîne numérique comme nombre de minutes. L'exemple suivant illustre cette situation.

```csharp
string value = "07";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "mm", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       00:07:00
```

```vb
Dim value As String = "05"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "mm", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       00:05:00
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "mm".

```csharp
TimeSpan departTime = new TimeSpan(11, 12, 00);
TimeSpan arriveTime = new TimeSpan(16, 28, 00);
Console.WriteLine("Travel time: {0:hh\\:mm}", 
                  arriveTime - departTime);
// The example displays the following output:
//       Travel time: 05:16
```

```vb
Dim departTime As New TimeSpan(11, 12, 00)
Dim arriveTime As New TimeSpan(16, 28, 00)
Console.WriteLine("Travel time: {0:hh\:mm}", 
                  arriveTime - departTime)
' The example displays the following output:
'       Travel time: 05:16
```

## <a name="the-s-custom-format-specifier"></a>Spécificateur de format personnalisé "s"

Le spécificateur de format personnalisé "s" affiche la valeur de la propriété [TimeSpan.Seconds](xref:System.TimeSpan.Seconds), qui représente le nombre de secondes entières dans l’intervalle de temps non incluses dans les composants « jours », « heures » ou « minutes ». Il retourne une valeur de chaîne à un chiffre si la valeur de la propriété [TimeSpan.Seconds](xref:System.TimeSpan.Seconds) est comprise entre 0 et 9, ou une valeur de chaîne à deux chiffres si la valeur de la propriété [TimeSpan.Seconds](xref:System.TimeSpan.Seconds) est comprise entre 10 et 59. 

Si le spécificateur de format personnalisé "s" est utilisé seul, spécifiez "%s" afin qu’il ne soit pas interprété à tort comme une chaîne de format standard. L'exemple suivant illustre cette situation.

```csharp
TimeSpan ts = TimeSpan.FromSeconds(12.465);
Console.WriteLine(ts.ToString("%s"));
// The example displays the following output:
//       12
```

```vb
Dim ts As TimeSpan = TimeSpan.FromSeconds(12.465)
Console.WriteLine(ts.ToString("%s"))
' The example displays the following output:
'       12
```

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "%s" à la place pour interpréter la chaîne numérique comme nombre de secondes. L'exemple suivant illustre cette situation.

```csharp
string value = "9";
TimeSpan interval;
if (TimeSpan.TryParseExact(value, "%s", null, out interval))
   Console.WriteLine(interval.ToString("c"));
else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value);   
// The example displays the following output:
//       00:00:09
```

```vb
Dim value As String = "9"
Dim interval As TimeSpan
If TimeSpan.TryParseExact(value, "%s", Nothing, interval) Then
   Console.WriteLine(interval.ToString("c"))
Else
   Console.WriteLine("Unable to convert '{0}' to a time interval", 
                     value)   
End If   
' The example displays the following output:
'       00:00:09
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "s".

```csharp
TimeSpan startTime = new TimeSpan(0, 12, 30, 15, 0);
TimeSpan endTime = new TimeSpan(0, 12, 30, 21, 3);
Console.WriteLine(xref:"Elapsed Time: {0:s\:fff} seconds", 
                  endTime - startTime);
// The example displays the following output:
//       Elapsed Time: 6:003 seconds      
```

```vb
Dim startTime As New TimeSpan(0, 12, 30, 15, 0)
Dim endTime As New TimeSpan(0, 12, 30, 21, 3)
Console.WriteLine("Elapsed Time: {0:s\:fff} seconds", 
                  endTime - startTime)
' The example displays the following output:
'       Elapsed Time: 6:003 seconds
```

## <a name="the-ss-custom-format-specifier"></a>Spécificateur de format personnalisé "ss"

Le spécificateur de format personnalisé "ss" affiche la valeur de la propriété [TimeSpan.Seconds](xref:System.TimeSpan.Seconds), qui représente le nombre de secondes entières dans l’intervalle de temps non incluses dans les composants « jours », « heures » ou « minutes ». Pour les valeurs 0 à 9, la chaîne de sortie inclut un zéro non significatif. 

En règle générale, dans une opération d’analyse, une chaîne d’entrée qui ne contient qu’un seul nombre est interprétée comme le nombre de jours. Vous pouvez utiliser le spécificateur de format personnalisé "ss" à la place pour interpréter la chaîne numérique comme nombre de secondes. L'exemple suivant illustre cette situation.

```csharp
string[] values = { "49", "9", "06" };
TimeSpan interval;
foreach (string value in values)
{
   if (TimeSpan.TryParseExact(value, "ss", null, out interval))
      Console.WriteLine(interval.ToString("c"));
   else
      Console.WriteLine("Unable to convert '{0}' to a time interval", 
                        value);   
}
// The example displays the following output:
//       00:00:49
//       Unable to convert '9' to a time interval
//       00:00:06
```

```vb
Dim values() As String = { "49", "9", "06" }
Dim interval As TimeSpan
For Each value As String In values
   If TimeSpan.TryParseExact(value, "ss", Nothing, interval) Then
      Console.WriteLine(interval.ToString("c"))
   Else
      Console.WriteLine("Unable to convert '{0}' to a time interval", 
                        value)   
   End If   
Next   
' The example displays the following output:
'       00:00:49
'       Unable to convert '9' to a time interval
'       00:00:06
```

L’exemple suivant illustre l’utilisation du spécificateur de format personnalisé "ss".

```csharp
TimeSpan interval1 = TimeSpan.FromSeconds(12.60);
Console.WriteLine(interval1.ToString(xref:"ss\.fff"));

TimeSpan interval2 = TimeSpan.FromSeconds(6.485);
Console.WriteLine(interval2.ToString(xref:"ss\.fff"));
// The example displays the following output:
//       12.600
//       06.485
```

```vb
Dim interval1 As TimeSpan = TimeSpan.FromSeconds(12.60)
Console.WriteLine(interval1.ToString("ss\.fff"))
Dim interval2 As TimeSpan = TimeSpan.FromSeconds(6.485)
Console.WriteLine(interval2.ToString("ss\.fff"))
' The example displays the following output:
'       12.600
'       06.485
```

## <a name="the-f-custom-format-specifier"></a>Spécificateur de format personnalisé "f"

Le spécificateur de format personnalisé "f" affiche les dixièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement un chiffre fractionnaire. 

Si le spécificateur de format personnalisé "f" est utilisé seul, spécifiez "%f" afin qu’il ne soit pas interprété à tort comme une chaîne de format standard.

L’exemple suivant utilise le spécificateur de format personnalisé "f" pour afficher les dixièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). "f" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-ff-custom-format-specifier"></a>Spécificateur de format personnalisé "ff"

Le spécificateur de format personnalisé "ff" affiche les centièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement deux chiffres fractionnaires. 

L’exemple suivant utilise le spécificateur de format personnalisé "ff" pour afficher les centièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). "ff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-fff-custom-format-specifier"></a>Spécificateur de format personnalisé "fff"

Le spécificateur de format personnalisé "fff" (trois caractères « f ») affiche les millisecondes dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement trois chiffres fractionnaires. 

L’exemple suivant utilise le spécificateur de format personnalisé "fff" pour afficher les millisecondes dans une valeur [TimeSpan](xref:System.TimeSpan). "fff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-ffff-custom-format-specifier"></a>Spécificateur de format personnalisé "ffff"
Le spécificateur de format personnalisé "ffff" (quatre caractères « f ») affiche les dix millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement quatre chiffres fractionnaires. 

L’exemple suivant utilise le spécificateur de format personnalisé "ffff" pour afficher les dix millièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). "ffff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-fffff-custom-format-specifier"></a>Spécificateur de format personnalisé "fffff"
Le spécificateur de format personnalisé "fffff" (cinq caractères « f ») affiche les cent millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement cinq chiffres fractionnaires. 

L’exemple suivant utilise le spécificateur de format personnalisé "fffff" pour afficher les cent millièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). "fffff" est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432 
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-ffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "ffffff"

Le spécificateur de format personnalisé "ffffff" (six caractères « f ») affiche les millionièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement six chiffres fractionnaires. 

L’exemple suivant utilise le spécificateur de format personnalisé "ffffff" pour afficher les millionièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432 
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-fffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "fffffff"

Le spécificateur de format personnalisé "fffffff" (sept caractères « f ») affiche les dix millionièmes de seconde (ou le nombre fractionnaire de graduations) dans un intervalle de temps. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la chaîne d’entrée doit contenir exactement sept chiffres fractionnaires. 

L’exemple suivant utilise le spécificateur de format personnalisé "fffffff" pour afficher le nombre fractionnaire de graduations dans une valeur [TimeSpan](xref:System.TimeSpan). Il est d’abord utilisé seul comme spécificateur de format, puis est combiné avec le spécificateur "s" dans une chaîne de format personnalisée.

```csharp
TimeSpan ts = new TimeSpan(1003498765432);
string fmt;
Console.WriteLine(ts.ToString("c"));
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   if (fmt.Length == 1) fmt = "%" + fmt;
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts);
} 
Console.WriteLine();

for (int ctr = 1; ctr <= 7; ctr++) {
   fmt = new String('f', ctr);
   Console.WriteLine("{0,10}: {1:s\\." + fmt + "}", "s\\." + fmt, ts);
}
// The example displays the following output:
//               %f: 8
//               ff: 87
//              fff: 876
//             ffff: 8765
//            fffff: 87654
//           ffffff: 876543
//          fffffff: 8765432
//       
//              s\.f: 29.8
//             s\.ff: 29.87
//            s\.fff: 29.876
//           s\.ffff: 29.8765
//          s\.fffff: 29.87654
//         s\.ffffff: 29.876543
//        s\.fffffff: 29.8765432 
```

```vb
Dim ts As New TimeSpan(1003498765432)
Dim fmt As String
Console.WriteLine(ts.ToString("c"))
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   If fmt.Length = 1 Then fmt = "%" + fmt
   Console.WriteLine("{0,10}: {1:" + fmt + "}", fmt, ts)
Next 
Console.WriteLine()

For ctr = 1 To 7
   fmt = New String("f"c, ctr)
   Console.WriteLine("{0,10}: {1:s\." + fmt + "}", "s\." + fmt, ts)
Next
' The example displays the following output:
'            %f: 8
'            ff: 87
'           fff: 876
'          ffff: 8765
'         fffff: 87654
'        ffffff: 876543
'       fffffff: 8765432
'    
'           s\.f: 29.8
'          s\.ff: 29.87
'         s\.fff: 29.876
'        s\.ffff: 29.8765
'       s\.fffff: 29.87654
'      s\.ffffff: 29.876543
'     s\.fffffff: 29.8765432
```

## <a name="the-f-custom-format-specifier"></a>Spécificateur de format personnalisé "F"

Le spécificateur de format personnalisé "F" affiche les dixièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Si la valeur des dixièmes de seconde de l’intervalle de temps est égale à zéro, elle n’est pas incluse dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence du chiffre des dixièmes de seconde est facultative.

Si le spécificateur de format personnalisé "F" est utilisé seul, spécifiez "%F" afin qu’il ne soit pas interprété à tort comme une chaîne de format standard.

L’exemple suivant utilise le spécificateur de format personnalisé "F" pour afficher les dixièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.669");
Console.WriteLine("{0} ('%F') --> {0:%F}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.091");
Console.WriteLine("{0} ('ss\\.F') --> {0:ss\\.F}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.1", "0:0:03.12" };
string fmt = @"h\:m\:ss\.F";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}                        
// The example displays the following output:
//       Formatting:
//       00:00:03.6690000 ('%F') --> 6
//       00:00:03.0910000 ('ss\.F') --> 03.
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.F') --> 00:00:03
//       0:0:03.1 ('h\:m\:ss\.F') --> 00:00:03.1000000
//       Cannot parse 0:0:03.12 with 'h\:m\:ss\.F'.
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.669")
Console.WriteLine("{0} ('%F') --> {0:%F}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.091")
Console.WriteLine("{0} ('ss\.F') --> {0:ss\.F}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.1", "0:0:03.12" }
Dim fmt As String = "h\:m\:ss\.F"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6690000 ('%F') --> 6
'       00:00:03.0910000 ('ss\.F') --> 03.
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.F') --> 00:00:03
'       0:0:03.1 ('h\:m\:ss\.F') --> 00:00:03.1000000
'       Cannot parse 0:0:03.12 with 'h\:m\:ss\.F'.
```

## <a name="the-ff-custom-format-specifier"></a>Spécificateur de format personnalisé "FF"

Le spécificateur de format personnalisé "FF" affiche les centièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les zéros de fin fractionnaires éventuels ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence du chiffre des dixièmes et des centièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FF" pour afficher les centièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.697");
Console.WriteLine("{0} ('FF') --> {0:FF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.809");
Console.WriteLine("{0} ('ss\\.FF') --> {0:ss\\.FF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.1", "0:0:03.127" };
string fmt = @"h\:m\:ss\.FF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//       Formatting:
//       00:00:03.6970000 ('FF') --> 69
//       00:00:03.8090000 ('ss\.FF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FF') --> 00:00:03
//       0:0:03.1 ('h\:m\:ss\.FF') --> 00:00:03.1000000
//       Cannot parse 0:0:03.127 with 'h\:m\:ss\.FF'. 
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.697")
Console.WriteLine("{0} ('FF') --> {0:FF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.809")
Console.WriteLine("{0} ('ss\.FF') --> {0:ss\.FF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.1", "0:0:03.127" }
Dim fmt As String = "h\:m\:ss\.FF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6970000 ('FF') --> 69
'       00:00:03.8090000 ('ss\.FF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FF') --> 00:00:03
'       0:0:03.1 ('h\:m\:ss\.FF') --> 00:00:03.1000000
'       Cannot parse 0:0:03.127 with 'h\:m\:ss\.FF'.
```

## <a name="the-fff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFF"

Le spécificateur de format personnalisé "FFF" (trois caractères « F ») affiche les millisecondes dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les zéros de fin fractionnaires éventuels ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence du chiffre des dixièmes, des centièmes et des millièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFF" pour afficher les millièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.6974");
Console.WriteLine("{0} ('FFF') --> {0:FFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.8009");
Console.WriteLine("{0} ('ss\\.FFF') --> {0:ss\\.FFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.1279" };
string fmt = @"h\:m\:ss\.FFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//       Formatting:
//       00:00:03.6974000 ('FFF') --> 697
//       00:00:03.8009000 ('ss\.FFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.1279 with 'h\:m\:ss\.FFF'.  
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.6974")
Console.WriteLine("{0} ('FFF') --> {0:FFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.8009")
Console.WriteLine("{0} ('ss\.FFF') --> {0:ss\.FFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.1279" }
Dim fmt As String = "h\:m\:ss\.FFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974000 ('FFF') --> 697
'       00:00:03.8009000 ('ss\.FFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.1279 with 'h\:m\:ss\.FFF'.
```

## <a name="the-ffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFF"

Le spécificateur de format personnalisé "FFFF" (quatre caractères « F ») affiche les dix millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les zéros de fin fractionnaires éventuels ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence du chiffre des dixièmes, des centièmes, des millièmes et des dix millièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFF" pour afficher les dix millièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également le spécificateur de format personnalisé "FFFF" dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.69749");
Console.WriteLine("{0} ('FFFF') --> {0:FFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.80009");
Console.WriteLine("{0} ('ss\\.FFFF') --> {0:ss\\.FFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.12795" };
string fmt = @"h\:m\:ss\.FFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//       Formatting:
//       00:00:03.6974900 ('FFFF') --> 6974
//       00:00:03.8000900 ('ss\.FFFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.12795 with 'h\:m\:ss\.FFFF'.
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.69749")
Console.WriteLine("{0} ('FFFF') --> {0:FFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.80009")
Console.WriteLine("{0} ('ss\.FFFF') --> {0:ss\.FFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.12795" }
Dim fmt As String = "h\:m\:ss\.FFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974900 ('FFFF') --> 6974
'       00:00:03.8000900 ('ss\.FFFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.12795 with 'h\:m\:ss\.FFFF'.
```

## <a name="the-fffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFFF"

Le spécificateur de format personnalisé "FFFFF" (cinq caractères « F ») affiche les cent millièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les zéros de fin fractionnaires éventuels ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence du chiffre des dixièmes, des centièmes, des millièmes, des dix millièmes et des cent millièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFFF" pour afficher les cent millièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également le spécificateur de format personnalisé "FFFFF" dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.697497");
Console.WriteLine("{0} ('FFFFF') --> {0:FFFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.800009");
Console.WriteLine("{0} ('ss\\.FFFFF') --> {0:ss\\.FFFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.127956" };
string fmt = @"h\:m\:ss\.FFFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}                       
// The example displays the following output:
//       Formatting:
//       00:00:03.6974970 ('FFFFF') --> 69749
//       00:00:03.8000090 ('ss\.FFFFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.127956 with 'h\:m\:ss\.FFFF'. 
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.697497")
Console.WriteLine("{0} ('FFFFF') --> {0:FFFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.800009")
Console.WriteLine("{0} ('ss\.FFFFF') --> {0:ss\.FFFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.127956" }
Dim fmt As String = "h\:m\:ss\.FFFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974970 ('FFFFF') --> 69749
'       00:00:03.8000090 ('ss\.FFFFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.127956 with 'h\:m\:ss\.FFFF'.
```

## <a name="the-ffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFFFF"

Le spécificateur de format personnalisé "FFFFFF" (six caractères « F ») affiche les millionièmes de seconde dans un intervalle de temps. Dans une opération de mise en forme, tous les chiffres fractionnaires restants sont tronqués. Les zéros de fin fractionnaires éventuels ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence du chiffre des dixièmes, des centièmes, des millièmes, des dix millièmes, des cent millièmes et des millionièmes de seconde est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFFFF" pour afficher les millionièmes de seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.6974974");
Console.WriteLine("{0} ('FFFFFF') --> {0:FFFFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.8000009");
Console.WriteLine("{0} ('ss\\.FFFFFF') --> {0:ss\\.FFFFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" };
string fmt = @"h\:m\:ss\.FFFFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}                       
// The example displays the following output:
//       Formatting:
//       00:00:03.6974974 ('FFFFFF') --> 697497
//       00:00:03.8000009 ('ss\.FFFFFF') --> 03.8
//       
//       Parsing:
//       0:0:03. ('h\:m\:ss\.FFFFFF') --> 00:00:03
//       0:0:03.12 ('h\:m\:ss\.FFFFFF') --> 00:00:03.1200000
//       Cannot parse 0:0:03.1279569 with 'h\:m\:ss\.FFFFFF'.
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.6974974")
Console.WriteLine("{0} ('FFFFFF') --> {0:FFFFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.8000009")
Console.WriteLine("{0} ('ss\.FFFFFF') --> {0:ss\.FFFFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" }
Dim fmt As String = "h\:m\:ss\.FFFFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'       Formatting:
'       00:00:03.6974974 ('FFFFFF') --> 697497
'       00:00:03.8000009 ('ss\.FFFFFF') --> 03.8
'       
'       Parsing:
'       0:0:03. ('h\:m\:ss\.FFFFFF') --> 00:00:03
'       0:0:03.12 ('h\:m\:ss\.FFFFFF') --> 00:00:03.1200000
'       Cannot parse 0:0:03.1279569 with 'h\:m\:ss\.FFFFFF'
```

## <a name="the-fffffff-custom-format-specifier"></a>Spécificateur de format personnalisé "FFFFFFF"

Le spécificateur de format personnalisé "FFFFFFF" (sept caractères « F ») affiche les dix millionièmes de seconde (ou le nombre fractionnaire de graduations) dans un intervalle de temps. Les zéros de fin fractionnaires éventuels ne sont pas inclus dans la chaîne de résultat. Dans une opération d’analyse qui appelle la méthode [TimeSpan.ParseExact](xref:System.TimeSpan.ParseExact(System.String,System.String,System.IFormatProvider)) ou [TimeSpan.TryParseExact](xref:System.TimeSpan.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.TimeSpanStyles,System.TimeSpan@)), la présence des sept chiffres fractionnaires dans la chaîne d’entrée est facultative.

L’exemple suivant utilise le spécificateur de format personnalisé "FFFFFFF" pour afficher les parties fractionnaires d’une seconde dans une valeur [TimeSpan](xref:System.TimeSpan). Il utilise également ce spécificateur de format personnalisé dans une opération d’analyse.

```csharp
Console.WriteLine("Formatting:");
TimeSpan ts1 = TimeSpan.Parse("0:0:3.6974974");
Console.WriteLine("{0} ('FFFFFFF') --> {0:FFFFFFF}", ts1);

TimeSpan ts2 = TimeSpan.Parse("0:0:3.9500000");
Console.WriteLine("{0} ('ss\\.FFFFFFF') --> {0:ss\\.FFFFFFF}", ts2);
Console.WriteLine();

Console.WriteLine("Parsing:");
string[] inputs = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" };
string fmt = @"h\:m\:ss\.FFFFFFF";
TimeSpan ts3;

foreach (string input in inputs) {
   if (TimeSpan.TryParseExact(input, fmt, null, out ts3))
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3);
   else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt);
}
// The example displays the following output:
//    Formatting:
//    00:00:03.6974974 ('FFFFFFF') --> 6974974
//    00:00:03.9500000 ('ss\.FFFFFFF') --> 03.95
//    
//    Parsing:
//    0:0:03. ('h\:m\:ss\.FFFFFFF') --> 00:00:03
//    0:0:03.12 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1200000
//    0:0:03.1279569 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1279569 
```

```vb
Console.WriteLine("Formatting:")
Dim ts1 As TimeSpan = TimeSpan.Parse("0:0:3.6974974")
Console.WriteLine("{0} ('FFFFFFF') --> {0:FFFFFFF}", ts1)

Dim ts2 As TimeSpan = TimeSpan.Parse("0:0:3.9500000")
Console.WriteLine("{0} ('ss\.FFFFFFF') --> {0:ss\.FFFFFFF}", ts2)
Console.WriteLine()

Console.WriteLine("Parsing:")
Dim inputs() As String = { "0:0:03.", "0:0:03.12", "0:0:03.1279569" }
Dim fmt As String = "h\:m\:ss\.FFFFFFF"
Dim ts3 As TimeSpan

For Each input As String In inputs
   If TimeSpan.TryParseExact(input, fmt, Nothing, ts3)
      Console.WriteLine("{0} ('{1}') --> {2}", input, fmt, ts3)
   Else
      Console.WriteLine("Cannot parse {0} with '{1}'.", 
                        input, fmt)
   End If  
Next
' The example displays the following output:
'    Formatting:
'    00:00:03.6974974 ('FFFFFFF') --> 6974974
'    00:00:03.9500000 ('ss\.FFFFFFF') --> 03.95
'    
'    Parsing:
'    0:0:03. ('h\:m\:ss\.FFFFFFF') --> 00:00:03
'    0:0:03.12 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1200000
'    0:0:03.1279569 ('h\:m\:ss\.FFFFFFF') --> 00:00:03.1279569  
```

## <a name="other-characters"></a>Autres caractères

Tout autre caractère sans séquence d’échappement dans une chaîne de format, y compris un espace blanc, est interprété comme un spécificateur de format personnalisé. Dans la plupart des cas, la présence de tout autre caractère sans séquence d’échappement aboutit à une [FormatException](xref:System.FormatException). 

Vous pouvez inclure un caractère littéral dans une chaîne de format de deux façons :

* Mettez-le entre guillemets simples (délimiteur de chaîne littérale). 

* Faites-le précéder d’une barre oblique inverse ("\"), qui est interprétée comme un caractère d’échappement. Cela signifie que, en C#, soit la chaîne de format doit être @-quoted, puis placée entre guillemets, soit le caractère littéral doit être précédé d’une barre oblique inverse supplémentaire.

  Dans certains cas, vous devrez peut-être utiliser une logique conditionnelle pour inclure un littéral avec séquence d’échappement dans une chaîne de format. L’exemple suivant utilise une logique conditionnelle pour inclure un symbole de signe pour les intervalles de temps négatifs. 
  
```csharp
using System;

public class Example
{
   public static void Main()
   {
      TimeSpan result = new DateTime(2010, 01, 01) - DateTime.Now; 
      String fmt = (result < TimeSpan.Zero ?  "\\-" : "") + "dd\\.hh\\:mm";

      Console.WriteLine(result.ToString(fmt));
      Console.WriteLine("Interval: {0:" + fmt + "}", result);
   }
}
// The example displays output like the following:
//       -1291.10:54
//       Interval: -1291.10:54
```

```vb
Module Example
   Public Sub Main()
      Dim result As TimeSpan = New DateTime(2010, 01, 01) - Date.Now 
      Dim fmt As String = If(result < TimeSpan.Zero, "\-", "") + "dd\.hh\:mm"

      Console.WriteLine(result.ToString(fmt))
      Console.WriteLine("Interval: {0:" + fmt + "}", result)
   End Sub
End Module
' The example displays output like the following:
'       -1291.10:54
'       Interval: -1291.10:54
```
  
.NET ne définit pas de grammaire pour les séparateurs dans les intervalles de temps. Cela signifie que les séparateurs entre les jours et les heures, entre les heures et les minutes, entre les minutes et les secondes et entre les secondes et les fractions de seconde doivent tous être traités comme des littéraux de caractère dans une chaîne de format.

L’exemple suivant utilise le caractère d’échappement et le guillemet simple pour définir une chaîne de format personnalisée qui inclut le mot « minutes » dans la chaîne de sortie. 

```csharp
TimeSpan interval = new TimeSpan(0, 32, 45);
// Escape literal characters in a format string.
string fmt = @"mm\:ss\ \m\i\n\u\t\e\s";
Console.WriteLine(interval.ToString(fmt));
// Delimit literal characters in a format string with the ' symbol.
fmt = "mm':'ss' minutes'";      
Console.WriteLine(interval.ToString(fmt));
// The example displays the following output: 
//       32:45 minutes      
//       32:45 minutes
```

```vb
Dim interval As New TimeSpan(0, 32, 45)
' Escape literal characters in a format string.
Dim fmt As String = "mm\:ss\ \m\i\n\u\t\e\s"
Console.WriteLine(interval.ToString(fmt))
' Delimit literal characters in a format string with the ' symbol.
fmt = "mm':'ss' minutes'"
Console.WriteLine(interval.ToString(fmt))
' The example displays the following output: 
'       32:45 minutes      
'       32:45 minutes
```

## <a name="see-also"></a>Voir aussi

[Mise en forme des types](formatting-types.md)

[Chaînes de format TimeSpan standard](standard-timespan.md)  


