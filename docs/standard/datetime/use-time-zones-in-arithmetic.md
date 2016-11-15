---
title: "Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure"
description: "Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 26870cdc-1709-4978-831b-ff2a2f24856f
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 735ae2f1d11ddf6b88b40c7b89083a45d1f07523

---

# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Guide pratique : utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure

En règle générale, lorsque vous effectuez des opérations arithmétiques de date et d’heure à l’aide de valeurs [System.DateTimeOffset](xref:System.DateTimeOffset), le résultat ne reflète pas les règles d’ajustement d’un fuseau horaire. Cela est vrai même lorsque le fuseau horaire de la valeur de date et d’heure est clairement identifiable. Cet article montre comment effectuer des opérations arithmétiques sur des valeurs de date et d’heure qui appartiennent à un fuseau horaire particulier. Les résultats de ces opérations arithmétiques reflètent les règles d’ajustement du fuseau horaire.

## <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Pour appliquer des règles d’ajustement dans les opérations arithmétiques de date et d’heure

1. Implémentez une méthode de couplage étroit d’une valeur de date et d’heure avec le fuseau horaire auquel elle appartient. Par exemple, déclarez une structure qui inclut à la fois la valeur de date et d’heure et son fuseau horaire. L’exemple suivant utilise cette approche pour lier une valeur [DateTimeOffset](xref:System.DateTimeOffset) et son fuseau horaire.

    ```csharp
    // Define a structure for DateTime values for internal use only
    internal struct TimeWithTimeZone
    {
    TimeZoneInfo TimeZone;
    DateTimeOffset Time;
    }
    ```

    ```vb
    ' Define a structure for DateTime values for internal use only
    Friend Structure TimeWithTimeZone
       Dim TimeZone As TimeZoneInfo
       Dim Time As Date
    End Structure
    ```
    
2. Convertissez une heure en temps universel coordonné (UTC) en appelant la méthode [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)).

3. Effectuez l’opération arithmétique sur l’heure UTC.

4. Convertissez l’heure UTC dans le fuseau horaire associé à l’heure d’origine en appelant la méthode [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)). 

## <a name="example"></a>Exemple

L’exemple suivant ajoute deux heures et trente minutes à 9 mars 2008, à 1:30 A.M., heure du Centre des États-Unis. Le passage du fuseau horaire à l’heure d’été se produit trente minutes plus tard, à 2:00, le 9 mars 2008. Étant donné que cet exemple suit les quatre étapes répertoriées à la section précédente, il signale correctement l’heure obtenue, soit 5:00, le 9 mars 2008. 

```csharp
using System;

public struct TimeZoneTime
{
   public TimeZoneInfo TimeZone;
   public DateTimeOffset Time;

   public TimeZoneTime(TimeZoneInfo tz, DateTimeOffset time)
   {
      if (tz == null) 
         throw new ArgumentNullException("The time zone cannot be a null reference.");

      this.TimeZone = tz;
      this.Time = time;   
   }

   public TimeZoneTime AddTime(TimeSpan interval)
   {
      // Convert time to UTC
      DateTimeOffset utcTime = TimeZoneInfo.ConvertTime(this.Time, TimeZoneInfo.Utc);      
      // Add time interval to time
      utcTime = utcTime.Add(interval);
      // Convert time back to time in time zone
      return new TimeZoneTime(this.TimeZone, TimeZoneInfo.ConvertTime(utcTime, this.TimeZone));
   }
}

public class TimeArithmetic
{
   public const string tzName = "Central Standard Time";

   public static void Main()
   {
      try
      {
         TimeZoneTime cstTime1, cstTime2;

         TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
         DateTime time1 = new DateTime(2008, 3, 9, 1, 30, 0);          
         TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

         cstTime1 = new TimeZoneTime(cst, 
                        new DateTimeOffset(time1, cst.GetUtcOffset(time1)));
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours);
         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, 
                                                    twoAndAHalfHours.ToString(),  
                                                    cstTime2.Time);
      }
      catch
      {
         Console.WriteLine("Unable to find {0}.", tzName);
      }
   }
}
```

```vb
Public Structure TimeZoneTime
   Public TimeZone As TimeZoneInfo
   Public Time As Date

   Public Sub New(tz As TimeZoneInfo, time As Date)
      If tz Is Nothing Then _
         Throw New ArgumentNullException("The time zone cannot be a null reference.")

      Me.TimeZone = tz
      Me.Time = time
   End Sub

   Public Function AddTime(interval As TimeSpan) As TimeZoneTime
      ' Convert time to UTC
      Dim utcTime As DateTime = TimeZoneInfo.ConvertTimeToUtc(Me.Time, _
                                                              Me.TimeZone)      
      ' Add time interval to time
      utcTime = utcTime.Add(interval)
      ' Convert time back to time in time zone
      Return New TimeZoneTime(Me.TimeZone, TimeZoneInfo.ConvertTime(utcTime, _
                              TimeZoneInfo.Utc, Me.TimeZone))
   End Function
End Structure

Module TimeArithmetic
   Public Const tzName As String = "Central Standard Time"

   Public Sub Main()
      Try
         Dim cstTime1, cstTime2 As TimeZoneTime

         Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName)
         Dim time1 As Date = #03/09/2008 1:30AM#
         Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

         cstTime1 = New TimeZoneTime(cst, time1)
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours)

         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, _
                                                    twoAndAHalfHours.ToString(), _ 
                                                    cstTime2.Time)  
      Catch
         Console.WriteLine("Unable to find {0}.", tzName)
      End Try   
   End Sub   
End Module
```

Notez que si cet ajout est effectué simplement sur la valeur [DateTimeOffset](xref:System.DateTimeOffset) sans conversion préalable de cette valeur en heure UTC, le résultat indique le point correct dans le temps, mais son décalage ne reflète pas celui du fuseau horaire désigné pour cette heure. 

Les valeurs [DateTimeOffset](xref:System.DateTimeOffset) sont dissociées de tout fuseau horaire auquel elles peuvent appartenir. Pour effectuer des opérations arithmétiques de date et d’heure d’une manière qui applique automatiquement les règles d’ajustement d’un fuseau horaire, le fuseau horaire auquel toute valeur de date et d’heure appartient doit être identifiable immédiatement. Cela signifie qu’une date et une heure et leur fuseau horaire associé doivent être étroitement couplés. Il existe plusieurs manières de procéder, dont les suivantes :

* Supposez que toutes les heures utilisées dans une application appartiennent à un fuseau horaire particulier. Bien qu’appropriée dans certains cas, cette approche présente une souplesse limitée et une portabilité éventuellement limitée.

* Définissez un type qui couple étroitement une valeur de date et d’heure avec son fuseau horaire associé en incluant les deux comme champs. Cette approche est utilisée dans l’exemple de code qui définit une structure pour stocker la date et l’heure, et le fuseau horaire, dans deux champs membres.

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Exécution d’opérations arithmétiques avec des dates et heures](performing-arithmetic-operations.md)



<!--HONumber=Nov16_HO1-->


