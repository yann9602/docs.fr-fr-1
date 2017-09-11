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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: ede8d021a4f524cf37f7ad00b6aed89d1b1729f8
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="02547-104">Guide pratique : permettre aux utilisateurs de résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="02547-104">How to: let users resolve ambiguous times</span></span>

<span data-ttu-id="02547-105">Une heure ambiguë est une heure qui correspond à plusieurs heures UTC.</span><span class="sxs-lookup"><span data-stu-id="02547-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="02547-106">Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="02547-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="02547-107">Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="02547-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="02547-108">Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="02547-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="02547-109">Proposez une méthode de mappage à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="02547-109">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="02547-110">Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="02547-110">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="02547-111">Cet article montre comment permettre à un utilisateur de résoudre une heure ambiguë.</span><span class="sxs-lookup"><span data-stu-id="02547-111">This article shows how to let a user resolve an ambiguous time.</span></span>

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="02547-112">Pour permettre à un utilisateur de résoudre une heure ambiguë</span><span class="sxs-lookup"><span data-stu-id="02547-112">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="02547-113">Obtenez la date et l’heure entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="02547-113">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="02547-114">Appelez la méthode [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) ou [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) pour déterminer si l’heure est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="02547-114">Call the [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="02547-115">Laissez l’utilisateur sélectionner le décalage souhaité.</span><span class="sxs-lookup"><span data-stu-id="02547-115">Let the user select the desired offset.</span></span>

4. <span data-ttu-id="02547-116">Obtenez la date et l’heure UTC en soustrayant de l’heure locale le décalage sélectionné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="02547-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

5. <span data-ttu-id="02547-117">Appelez la méthode `static` (`Shared` en Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) pour affecter la valeur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) à la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="02547-117">Call the `static` (`Shared` in Visual Basic ) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="02547-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="02547-118">Example</span></span>

<span data-ttu-id="02547-119">L’exemple suivant invite l’utilisateur à entrer une date et une heure et, si cette dernière est ambiguë, permet à l’utilisateur de sélectionner l’heure UTC à laquelle l’heure ambiguë correspond.</span><span class="sxs-lookup"><span data-stu-id="02547-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span> <span data-ttu-id="02547-120">L’exemple utilise un objet [DateTime](xref:System.DateTime) ; vous pouvez lui substituer un objet [DateTimeOffset](xref:System.DateTimeOffset) si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="02547-120">The example uses a [DateTime](xref:System.DateTime) object; you can substitute a [DateTimeOffset](xref:System.DateTimeOffset) object if desired.</span></span>

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

<span data-ttu-id="02547-121">La partie principale de cet exemple de code utilise un tableau d’objets [TimeSpan](xref:System.TimeSpan) pour indiquer les décalages possibles de l’heure ambiguë par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="02547-121">The core of the example code uses an array of [TimeSpan](xref:System.TimeSpan) objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="02547-122">Toutefois, ces décalages ne seront probablement pas significatifs pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="02547-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="02547-123">Pour clarifier leur signification, le code note également si un décalage représente l’heure d’hiver du fuseau horaire local ou son heure d’été.</span><span class="sxs-lookup"><span data-stu-id="02547-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="02547-124">Le code détermine l’heure d’hiver et l’heure d’été en comparant le décalage avec la valeur de la propriété [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset).</span><span class="sxs-lookup"><span data-stu-id="02547-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span> <span data-ttu-id="02547-125">Cette propriété indique la différence entre l’heure UTC et l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="02547-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="02547-126">Dans cet exemple, toutes les références au fuseau horaire local sont faites via la propriété [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) ; le fuseau horaire local n’est jamais assigné à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="02547-126">In this example, all references to the local time zone are made through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="02547-127">Il est recommandé d’utiliser cette méthode, car un autre appel peut effacer les données mises en cache et invalider les objets auxquels le fuseau horaire local est assigné.</span><span class="sxs-lookup"><span data-stu-id="02547-127">This is a recommended practice because another call could clear the cached data and invalidate any objects that the local time zone is assigned to.</span></span>

## <a name="see-also"></a><span data-ttu-id="02547-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02547-128">See Also</span></span>

[<span data-ttu-id="02547-129">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="02547-129">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="02547-130">Guide pratique pour résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="02547-130">How to: resolve ambiguous times</span></span>](resolve-ambiguous-times.md)


