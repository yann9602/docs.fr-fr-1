---
title: "Exécution d’opérations arithmétiques avec des dates et heures"
description: "Exécution d’opérations arithmétiques avec des dates et heures"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 64fbb3b25d5959ac1dd781d2076775560d926e1a

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Exécution d’opérations arithmétiques avec des dates et heures

Même si les structures [System.DateTime](xref:System.DateTime) et [System.DateTimeOffset](xref:System.DateTimeOffset) fournissent des membres qui exécutent des opérations arithmétiques sur leurs valeurs, les résultats des opérations arithmétiques sont très différents. Cet article examine ces différences, les met en rapport avec les degrés de prise en charge des fuseaux horaires dans les données de date et d’heure, et explique comment exécuter des opérations prenant pleinement en charge les fuseaux horaires à l’aide de données de date et d’heure.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparaisons et opérations arithmétiques avec des valeurs DateTime

Les valeurs [System.DateTime](xref:System.DateTime) possèdent un degré limité de prise en charge des fuseaux horaires. La propriété [DateTime.Kind](xref:System.DateTime.Kind) permet d’assigner une valeur [System.DateTimeKind](xref:System.DateTimeKind) à la date et à l’heure pour indiquer si elle représente l’heure locale, le temps universel coordonné (UTC) ou l’heure dans un fuseau horaire non spécifié. Toutefois, ces informations limitées de fuseau horaire sont ignorées lors de la comparaison ou de l’exécution d’opérations arithmétiques avec des dates et des heures sur des valeurs [DateTime](xref:System.DateTime). Ceci est illustré dans l’exemple suivant, qui compare l’heure locale actuelle à l’heure UTC actuelle.

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

La méthode [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) signale que l’heure locale est antérieure (ou inférieure) à l’heure UTC, et l’opération de soustraction indique que la différence entre l’heure UTC et l’heure locale pour un système dans le fuseau horaire du Pacifique est de sept heures. Toutefois, comme ces deux valeurs donnent des représentations différentes d’un même point dans le temps, il apparaît clairement dans ce cas que cet intervalle de temps est totalement attribuable au décalage du fuseau horaire local par rapport à l’heure UTC. 

En règle générale, la propriété [DateTimeKind](xref:System.DateTimeKind) n’affecte pas les résultats retournés par les méthodes de comparaison et d’arithmétique [DateTime](xref:System.DateTime) (comme la comparaison de deux points identiques dans le temps l’indique), mais elle peut affecter l’interprétation de ces résultats. Exemple :

* Le résultat de toute opération arithmétique exécutée sur deux valeurs de date et d’heure dont les propriétés [DateTimeKind](xref:System.DateTimeKind) sont égales à [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) reflète l’intervalle de temps effectif entre ces deux valeurs. De même, la comparaison de deux valeurs de date et d’heure de ce type indique précisément la relation entre les heures.

* Le résultat de toute opération arithmétique ou de comparaison exécutée sur deux valeurs de date et d’heure dont les propriétés [DateTimeKind](xref:System.DateTimeKind) sont égales à [DateTimeKind.Local](xref:System.DateTimeKind.Local) ou sur deux valeurs de date et d’heure dont les propriétés [DateTimeKind](xref:System.DateTimeKind) ont des valeurs différentes reflète la différence de temps horloge entre ces deux valeurs. 

* Les opérations arithmétiques ou de comparaison sur des valeurs de date et d’heure locales ne prennent pas en compte le fait qu’une valeur particulière soit ambiguë ou non valide, ni l’incidence de règles d’ajustement quelconques résultant du passage du fuseau horaire local à l’heure d’été ou à l’heure d’hiver.

* Toute opération qui compare ou calcule la différence entre l’heure UTC et une heure locale inclut dans le résultat un intervalle de temps égal au décalage du fuseau horaire local par rapport à l’heure UTC. 

* Toute opération qui compare ou calcule la différence entre une heure non spécifiée et l’heure UTC ou l’heure locale reflète le temps horloge simple. Les décalages entre les fuseaux horaires ne sont pas pris en compte et le résultat ne reflète pas l’application des règles d’ajustement des fuseaux horaires. 

* Toute opération qui compare ou calcule la différence entre deux heures non spécifiées peut inclure un intervalle inconnu qui reflète la différence d’heure entre deux fuseaux horaires différents.

Il existe de nombreux scénarios dans lesquels les différences entre les fuseaux horaires n’affectent pas les calculs des dates et des heures ou dans lesquels le contexte des données de date et d’heure définit la signification des opérations arithmétiques ou de comparaison. Pour une présentation de certains d’entre eux, consultez [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md).

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparaisons et opérations arithmétiques avec des valeurs DateTimeOffset

Une valeur [System.DateTimeOffset](xref:System.DateTimeOffset) inclut non seulement une date et une heure, mais également un décalage qui définit clairement cette date et cette heure par rapport à l’heure UTC. Cela permet de définir une égalité d’une manière quelque peu différente de celle des valeurs [System.DateTime](xref:System.DateTime). Les valeurs [DateTime](xref:System.DateTime) sont égales lorsqu’elles ont la même valeur de date et d’heure, alors que les valeurs [DateTimeOffset](xref:System.DateTimeOffset) sont égales lorsqu’elles font toutes les deux référence au même point dans le temps. Une valeur [DateTimeOffset](xref:System.DateTimeOffset) est de ce fait plus précise et nécessite une interprétation moindre lorsqu’elle est utilisée dans des comparaisons ou dans la plupart des opérations arithmétiques qui déterminent l’intervalle entre deux dates et heures. Cette différence de comportement est illustrée dans l’exemple suivant, qui est l’équivalent [DateTimeOffset](xref:System.DateTimeOffset) de l’exemple précédent, qui comparait des valeurs DateTime d’heure locale et d’heure UTC.

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

Dans cet exemple, la méthode [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) indique que l’heure locale actuelle et l’heure UTC actuelle sont égales, et la soustraction des valeurs [DateTimeOffset](xref:System.DateTimeOffset) indique que la différence entre les deux heures est [TimeSpan.Zero](xref:System.TimeSpan.Zero). 

L’utilisation de valeurs [DateTimeOffset](xref:System.DateTimeOffset) dans des opérations arithmétiques de date et d’heure présente une limitation majeure : les valeurs [DateTimeOffset](xref:System.DateTimeOffset) prennent partiellement en charge les fuseaux horaires, et non pas pleinement. Même si le décalage de la valeur [DateTimeOffset](xref:System.DateTimeOffset) reflète le décalage d’un fuseau horaire par rapport à l’heure UTC lorsqu’une valeur est assignée initialement à une variable [DateTimeOffset](xref:System.DateTimeOffset), il se dissocie par la suite du fuseau horaire. Comme il n’est plus directement associé à une heure identifiable, l’addition et la soustraction d’intervalles de dates et d’heures ne prennent pas en compte les règles d’ajustement des fuseaux horaires. 

Pour illustrer cela, la passage à l’heure d’été dans le fuseau horaire du Centre (États-Unis) se produit à 2:00, le 9 mars 2008. Cela signifie que l’ajout d’un intervalle de deux heures trente à l’heure de 1:30 dans le fuseau horaire du Centre des États-Unis, le 9 mars 2008, doit avoir pour résultat 5:00, le 9 mars 2008. Toutefois, comme le montre l’exemple suivant, le résultat de l’addition est 4:00, le 9 mars 2008. Notez que le résultat de cette opération représente l’heure correcte, même s’il ne s’agit pas de l’heure dans le fuseau horaire qui nous intéresse (autrement dit, elle n’a pas le décalage horaire attendu).

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Opérations arithmétiques avec des heures dans des fuseaux horaires

La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) ne fournit aucune méthode appliquant automatiquement des règles d’ajustement lorsque vous effectuez des opérations arithmétiques de date et d’heure. Toutefois, vous pouvez convertir l’heure d’un fuseau horaire en heure UTC, effectuer l’opération arithmétique, puis reconvertir l’heure UTC dans l’heure du fuseau horaire. Pour plus d’informations, consultez [Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md).

Par exemple, le code suivant est semblable au code précédent qui ajoutait deux heures trente à 2:00, le 9 mars 2008. Toutefois, comme il convertit l’heure du Centre des États-Unis en heure UTC avant d’effectuer les opérations arithmétiques de date et d’heure, puis reconvertit le résultat UTC en heure du Centre, l’heure résultante reflète le passage du fuseau horaire du Centre des États-Unis à l’heure d’été.

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md)





<!--HONumber=Nov16_HO1-->


