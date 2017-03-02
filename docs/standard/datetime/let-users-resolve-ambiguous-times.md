---
title: "Guide pratique : permettre aux utilisateurs de résoudre des heures ambiguës"
description: "Guide pratique pour permettre aux utilisateurs de résoudre des heures ambiguës"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6858a5c-02ab-4367-9e08-fa22c051c38d
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ede8d021a4f524cf37f7ad00b6aed89d1b1729f8
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a>Guide pratique : permettre aux utilisateurs de résoudre des heures ambiguës

Une heure ambiguë est une heure qui correspond à plusieurs heures UTC. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :

* Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.

* Proposez une méthode de mappage à l’heure UTC. Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.

Cet article montre comment permettre à un utilisateur de résoudre une heure ambiguë.

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Pour permettre à un utilisateur de résoudre une heure ambiguë

1. Obtenez la date et l’heure entrées par l’utilisateur.

2. Appelez la méthode [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) pour déterminer si l’heure est ambiguë.

3. Laissez l’utilisateur sélectionner le décalage souhaité.

4. Obtenez la date et l’heure UTC en soustrayant de l’heure locale le décalage sélectionné par l’utilisateur.

5. Appelez la méthode `static` (`Shared` en Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) pour affecter la valeur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) à la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure UTC.

## <a name="example"></a>Exemple

L’exemple suivant invite l’utilisateur à entrer une date et une heure et, si cette dernière est ambiguë, permet à l’utilisateur de sélectionner l’heure UTC à laquelle l’heure ambiguë correspond. L’exemple utilise un objet [DateTime](xref:System.DateTime) ; vous pouvez lui substituer un objet [DateTimeOffset](xref:System.DateTimeOffset) si vous le souhaitez.

```csharp
private void GetUserDateInput()
{
   // Get date and time from user
   DateTime inputDate = GetUserDateTime();
   DateTime utcDate;

   // Exit if date has no significant value
   if (inputDate == DateTime.MinValue) return;

   if (TimeZoneInfo.Local.IsAmbiguousTime(inputDate))
   {
      Console.WriteLine("The date you've entered is ambiguous.");
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:");
      TimeSpan[] offsets = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate);
      for (int ctr = 0; ctr < offsets.Length; ctr++)
      {
         Console.WriteLine("{0}.) {1} hours, {2} minutes", ctr, offsets[ctr].Hours, offsets[ctr].Minutes);
      }
      Console.Write("> ");
      int selection = Convert.ToInt32(Console.ReadLine());

      // Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = DateTime.SpecifyKind(inputDate - offsets[selection], DateTimeKind.Utc);

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());
   }
   else
   {
      utcDate = inputDate.ToUniversalTime();
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());    
   }
}

private DateTime GetUserDateTime() 
{
   bool exitFlag = false;             // flag to exit loop if date is valid
   string dateString;  
   DateTime inputDate = DateTime.MinValue;

   Console.Write("Enter a local date and time: ");
   while (! exitFlag)
   {
      dateString = Console.ReadLine();
      if (dateString.ToUpper() == "E")
         exitFlag = true;

      if (DateTime.TryParse(dateString, out inputDate))
         exitFlag = true;
      else
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ");
   }

   return inputDate;        
}
```

```vb
Private Sub GetUserDateInput()
   ' Get date and time from user
   Dim inputDate As Date = GetUserDateTime()
   Dim utcDate As Date

   ' Exit if date has no significant value
   If inputDate = Date.MinValue Then Exit Sub

   If TimeZoneInfo.Local.IsAmbiguousTime(inputDate) Then
      Console.WriteLine("The date you've entered is ambiguous.")
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:")
      Dim offsets() As TimeSpan = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate)
      For ctr As Integer = 0 to offsets.Length - 1
         Dim zoneDescription As String
         If offsets(ctr).Equals(TimeZoneInfo.Local.BaseUtcOffset) Then 
            zoneDescription = TimeZoneInfo.Local.StandardName
         Else
            zoneDescription = TimeZoneInfo.Local.DaylightName
         End If
         Console.WriteLine("{0}.) {1} hours, {2} minutes ({3})", _
                           ctr, offsets(ctr).Hours, offsets(ctr).Minutes, zoneDescription)
      Next         
      Console.Write("> ")
      Dim selection As Integer = CInt(Console.ReadLine())

      ' Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = Date.SpecifyKind(inputDate - offsets(selection), DateTimeKind.Utc)

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())
   Else
      utcDate = inputDate.ToUniversalTime()
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())    
   End If
End Sub

Private Function GetUserDateTime() As Date
   Dim exitFlag As Boolean = False            ' flag to exit loop if date is valid
   Dim dateString As String 
   Dim inputDate As Date = Date.MinValue

   Console.Write("Enter a local date and time: ")
   Do While Not exitFlag
      dateString = Console.ReadLine()
      If dateString.ToUpper = "E" Then exitFlag = True
      If Date.TryParse(dateString, inputDate) Then
         exitFlag = true
      Else   
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ")
      End If
   Loop

   Return inputDate        
End Function
```

La partie principale de cet exemple de code utilise un tableau d’objets [TimeSpan](xref:System.TimeSpan) pour indiquer les décalages possibles de l’heure ambiguë par rapport à l’heure UTC. Toutefois, ces décalages ne seront probablement pas significatifs pour l’utilisateur. Pour clarifier leur signification, le code note également si un décalage représente l’heure d’hiver du fuseau horaire local ou son heure d’été. Le code détermine l’heure d’hiver et l’heure d’été en comparant le décalage avec la valeur de la propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset). Cette propriété indique la différence entre l’heure UTC et l’heure d’hiver du fuseau horaire.

Dans cet exemple, toutes les références au fuseau horaire local sont faites via la propriété [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) ; le fuseau horaire local n’est jamais assigné à une variable objet. Il est recommandé d’utiliser cette méthode, car un autre appel peut effacer les données mises en cache et invalider les objets auxquels le fuseau horaire local est assigné.

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Guide pratique pour résoudre des heures ambiguës](resolve-ambiguous-times.md)


