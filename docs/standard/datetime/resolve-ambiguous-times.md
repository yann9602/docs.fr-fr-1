---
title: "Guide pratique : résoudre des heures ambiguës"
description: "Guide pratique pour résoudre des heures ambiguës"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: b31ea18cd7a7e32863f384cb279dc715fd62b3df

---

# <a name="how-to-resolve-ambiguous-times"></a>Guide pratique : résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

* Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.

* Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

Cet article indique comment résoudre une heure ambiguë en supposant qu’elle correspond à l’heure d’hiver du fuseau horaire.

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire

1. Appelez la méthode [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) pour déterminer si l’heure est ambiguë.

2. Si l’heure est ambiguë, soustrayez l’heure de l’objet [TimeSpan](xref:System.TimeSpan) retourné par la propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) du fuseau horaire.

3. Appelez la méthode `static` (`Shared` en Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) pour affecter la valeur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) à la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure UTC.

## <a name="example"></a>Exemple

L’exemple suivant illustre comment convertir une heure [DateTime](xref:System.DateTime) ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local. 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

Cet exemple comprend une méthode nommée `ResolveAmbiguousTime`, qui détermine si la valeur [DateTime](xref:System.DateTime) qui lui est transmise est ambiguë ou non. Si la valeur est ambiguë, la méthode retourne une valeur [DateTime](xref:System.DateTime) qui représente l’heure UTC correspondante. La méthode gère cette conversion en soustrayant de l’heure locale la valeur de la propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) du fuseau horaire local. 

En règle générale, il est possible de gérer une heure ambiguë en appelant la méthode [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) pour récupérer un tableau des objets [TimeSpan](xref:System.TimeSpan) qui contiennent les décalages possibles de l’heure ambiguë par rapport à l’heure UTC. Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire. La propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Guide pratique pour permettre aux utilisateurs de résoudre des heures ambiguës](let-users-resolve-ambiguous-times.md)




<!--HONumber=Nov16_HO3-->


