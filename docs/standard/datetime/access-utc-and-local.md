---
title: "Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis"
description: "Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: ab419cf365b61399ea41e99c15e276584ad0db31

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Guide pratique : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis

La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) fournit deux propriétés, `Utc` et `Local`, qui permettent à votre code d’accéder à des objets de fuseau horaire prédéfinis. Cette rubrique explique comment accéder aux objets `TimeZoneInfo` retournés par ces propriétés.

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)

1. Utilisez la propriété **static** (**Shared** en Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) pour accéder au temps universel coordonné.

2. Au lieu d’affecter l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) retourné par la propriété à une variable d’objet, continuez à accéder au temps universel coordonné via la propriété [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc).


## <a name="to-access-the-local-time-zone"></a>Pour accéder au fuseau horaire local

1. Utilisez la propriété **static** (**Shared** en Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) pour accéder au fuseau horaire local du système.

2. Au lieu d’affecter l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) retourné par la propriété à une variable d’objet, continuez à accéder au fuseau horaire local via la propriété [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).

## <a name="example"></a>Exemple

Le code suivant utilise les propriétés [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) et [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) pour convertir une heure du fuseau horaire Est (États-Unis et Canada), ainsi que pour afficher le nom du fuseau horaire sur la console.

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

Vous devez toujours accéder au fuseau horaire local via la propriété [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) plutôt qu’en affectant le fuseau horaire local à une variable d’objet [TimeZoneInfo](xref:System.TimeZoneInfo). De même, vous devez toujours accéder au temps universel coordonné via la propriété [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) plutôt qu’en affectant le fuseau horaire UTC à une variable d’objet [TimeZoneInfo](xref:System.TimeZoneInfo). Cela empêche la variable d’objet [TimeZoneInfo](xref:System.TimeZoneInfo) d’être invalidée par une méthode externe.


## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md)



<!--HONumber=Nov16_HO3-->


