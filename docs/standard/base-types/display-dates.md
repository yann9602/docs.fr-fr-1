---
title: "Guide pratique : afficher des dates dans des calendriers non grégoriens"
description: "Guide pratique pour afficher des dates dans des calendriers non grégoriens"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 93f06e1d-544b-4ccc-a0b2-95cd674852cb
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 69a33b3e162c07a1d8a065a150c6db96f04334f6
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Guide pratique : afficher des dates dans des calendriers non grégoriens

Les types [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset) utilisent le calendrier grégorien comme calendrier par défaut. Cela signifie que l’appel de la méthode `ToString` d’une valeur de date et d’heure affiche la représentation sous forme de chaîne de la date et de l’heure dans le calendrier grégorien, même si ces date et heure ont été créées à l’aide d’un autre calendrier. Ceci est illustré dans l’exemple suivant, qui utilise deux méthodes différentes pour créer une valeur de date et d’heure avec le calendrier persan, mais affiche toujours ces valeurs de date et d’heure dans le calendrier grégorien quand il appelle la méthode [ToString](xref:System.DateTime.ToString). Cet exemple reflète deux techniques couramment utilisées, mais incorrectes, pour l’affichage de la date dans un calendrier particulier.

```csharp
PersianCalendar persianCal = new PersianCalendar();

DateTime persianDate = persianCal.ToDateTime(1387, 3, 18, 12, 0, 0, 0);
Console.WriteLine(persianDate.ToString());

persianDate = new DateTime(1387, 3, 18, persianCal);
Console.WriteLine(persianDate.ToString());
// The example displays the following output to the console:
//       6/7/2008 12:00:00 PM
//       6/7/2008 12:00:00 AM
```

```vb
Dim persianCal As New PersianCalendar()

Dim persianDate As Date = persianCal.ToDateTime(1387, 3, 18, _
                                                12, 0, 0, 0)
Console.WriteLine(persianDate.ToString())

persianDate = New DateTime(1387, 3, 18, persianCal)
Console.WriteLine(persianDate.ToString())
' The example displays the following output to the console:
'       6/7/2008 12:00:00 PM
'       6/7/2008 12:00:00 AM
```

Deux techniques différentes peuvent être utilisées pour afficher la date dans un calendrier particulier. La première nécessite que le calendrier soit le calendrier par défaut pour une culture particulière. La seconde est utilisable avec n’importe quel calendrier.

## <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Pour afficher la date pour le calendrier par défaut d’une culture

1. Instanciez un objet de calendrier dérivé de la classe [Calendar](xref:System.Globalization.Calendar) qui représente le calendrier à utiliser.

2. Instanciez un objet [CultureInfo](xref:System.Globalization.CultureInfo) représentant la culture dont la mise en forme doit être utilisée pour afficher la date.

3. Appelez la méthode [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) pour déterminer si l’objet de calendrier est membre du tableau retourné par la propriété [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars). Cela indique que le calendrier peut servir de calendrier par défaut pour l’objet [CultureInfo](xref:System.Globalization.CultureInfo). S’il n’est pas membre du tableau, suivez les instructions de la section « Pour afficher la date dans un calendrier ».

4. Assignez l’objet de calendrier à la propriété [Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) retourné par la propriété [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat).

  > [!NOTE]
  > La classe [CultureInfo](xref:System.Globalization.CultureInfo) comporte également une propriété [Calendar](xref:System.Globalization.CultureInfo.Calendar). Toutefois, elle est en lecture seule et constante ; elle ne change pas pour refléter le nouveau calendrier par défaut attribué à la propriété [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar).
  
5. Appelez la méthode [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) ou [DateTime.ToString(String,IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) et passez-lui l’objet [CultureInfo](xref:System.Globalization.CultureInfo) dont le calendrier par défaut a été modifié à l’étape précédente.

## <a name="to-display-the-date-in-any-calendar"></a>Pour afficher la date dans un calendrier

1. Instanciez un objet de calendrier dérivé de la classe [Calendar](xref:System.Globalization.Calendar) qui représente le calendrier à utiliser.

2. Déterminez les éléments de date et d’heure qui doivent apparaître dans la représentation sous forme de chaîne de la valeur de date et d’heure.

3. Pour chaque élément de date et d’heure que vous souhaitez afficher, appelez la méthode `Get…` de l’objet de calendrier. Les méthodes suivantes sont disponibles :

    * [GetYear](xref:System.Globalization.Calendar.GetYear(System.DateTime)), pour afficher l’année dans le calendrier approprié.
    
    * [GetMonth](xref:System.Globalization.Calendar.GetMonth(System.DateTime)), pour afficher le mois dans le calendrier approprié. 
    
    * [GetDayOfMonth](xref:System.Globalization.Calendar.GetDayOfMonth(System.DateTime)), pour afficher le numéro du jour du mois dans le calendrier approprié.
    
    * [GetHour](xref:System.Globalization.Calendar.GetHour(System.DateTime)), pour afficher l’heure du jour dans le calendrier approprié.
    
    * [GetMinute](xref:System.Globalization.Calendar.GetMinute(System.DateTime)), pour afficher les minutes de l’heure dans le calendrier approprié.
    
    * [GetSecond](xref:System.Globalization.Calendar.GetSecond(System.DateTime)), pour afficher les secondes de la minute dans le calendrier approprié. 
    
    * [GetMilliseconds](xref:System.Globalization.Calendar.GetMilliseconds(System.DateTime)), pour afficher les millisecondes de la seconde dans le calendrier approprié.
    
## <a name="example"></a>Exemple
    
L’exemple affiche une date à l’aide de deux calendriers différents. Il affiche la date après avoir défini le calendrier hégirien comme calendrier par défaut pour la culture ar-JO et affiche la date à l’aide du calendrier persan, qui n’est pas pris en charge comme calendrier facultatif par la culture fa-IR.

```csharp
using System;
using System.Globalization;

public class CalendarDates
{
   public static void Main()
   {
      HijriCalendar hijriCal = new HijriCalendar();
      CalendarUtility hijriUtil = new CalendarUtility(hijriCal);
      DateTime dateValue1 = new DateTime(1429, 6, 29, hijriCal);
      DateTimeOffset dateValue2 = new DateTimeOffset(dateValue1, 
                                  TimeZoneInfo.Local.GetUtcOffset(dateValue1));
      CultureInfo jc = CultureInfo.CreateSpecificCulture("ar-JO");

      // Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", 
                        dateValue1.ToString("d"));
      // Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", 
                        dateValue1.ToString("d", jc));
      // Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:");
      // Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc));
      // Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc));

      Console.WriteLine();

      PersianCalendar persianCal = new PersianCalendar();
      CalendarUtility persianUtil = new CalendarUtility(persianCal);
      CultureInfo ic = CultureInfo.CreateSpecificCulture("fa-IR");

      // Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}",       
                        dateValue1.ToString("d", ic));
      // Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic));
      // Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic));
   }
}

public class CalendarUtility
{
   private Calendar thisCalendar;
   private CultureInfo targetCulture;

   public CalendarUtility(Calendar cal)
   {
      this.thisCalendar = cal;
   }

   private bool CalendarExists(CultureInfo culture)
   {
      this.targetCulture = culture;
      return Array.Exists(this.targetCulture.OptionalCalendars, 
                          this.HasSameName);
   }

   private bool HasSameName(Calendar cal)
   {
      if (cal.ToString() == thisCalendar.ToString())
         return true;
      else
         return false;
   }

   public string DisplayDate(DateTime dateToDisplay, CultureInfo culture)
   {
      DateTimeOffset displayOffsetDate = dateToDisplay;
      return DisplayDate(displayOffsetDate, culture);
   }

   public string DisplayDate(DateTimeOffset dateToDisplay, 
                             CultureInfo culture)
   {
      string specifier = "yyyy/MM/dd";

      if (this.CalendarExists(culture))
      {
         Console.WriteLine("Displaying date in supported {0} calendar...", 
                           this.thisCalendar.GetType().Name);
         culture.DateTimeFormat.Calendar = this.thisCalendar;
         return dateToDisplay.ToString(specifier, culture);
      }
      else
      {
         Console.WriteLine("Displaying date in unsupported {0} calendar...", 
                           thisCalendar.GetType().Name);

         string separator = targetCulture.DateTimeFormat.DateSeparator;

         return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") +
                separator +
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") + 
                separator +
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00"); 
      }
   } 
}
// The example displays the following output to the console:
//       Using the system default culture: 7/3/2008
//       Using the ar-JO culture's original default calendar: 03/07/2008
//       Using the ar-JO culture with Hijri as the default calendar:
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       
//       Using the ir-FA culture's default calendar: 7/3/2008
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
```

```vb
Imports System.Globalization

Public Class CalendarDates
   Public Shared Sub Main()
      Dim hijriCal As New HijriCalendar()
      Dim hijriUtil As New CalendarUtility(hijriCal)
      Dim dateValue1 As Date = New Date(1429, 6, 29, hijriCal)
      Dim dateValue2 As DateTimeOffset = New DateTimeOffset(dateValue1, _
                                         TimeZoneInfo.Local.GetUtcOffset(dateValue1))
      Dim jc As CultureInfo = CultureInfo.CreateSpecificCulture("ar-JO")

      ' Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", _
                        dateValue1.ToString("d"))
      ' Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", _
                        dateValue1.ToString("d", jc))
      ' Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:")
      ' Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc))
      ' Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc))

      Console.WriteLine()

      Dim persianCal As New PersianCalendar()
      Dim persianUtil As New CalendarUtility(persianCal)
      Dim ic As CultureInfo = CultureInfo.CreateSpecificCulture("fa-IR")

      ' Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}", _      
                        dateValue1.ToString("d", ic))
      ' Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic))
      ' Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic))
   End Sub
End Class

Public Class CalendarUtility
   Private thisCalendar As Calendar
   Private targetCulture As CultureInfo

   Public Sub New(cal As Calendar)
      Me.thisCalendar = cal
   End Sub

   Private Function CalendarExists(culture As CultureInfo) As Boolean
      Me.targetCulture = culture
      Return Array.Exists(Me.targetCulture.OptionalCalendars, _
                          AddressOf Me.HasSameName)
   End Function 

   Private Function HasSameName(cal As Calendar) As Boolean
      If cal.ToString() = thisCalendar.ToString() Then
         Return True
      Else
         Return False
      End If
   End Function

   Public Function DisplayDate(dateToDisplay As Date, _
                               culture As CultureInfo) As String
      Dim displayOffsetDate As DateTimeOffset = dateToDisplay
      Return DisplayDate(displayOffsetDate, culture)
   End Function

   Public Function DisplayDate(dateToDisplay As DateTimeOffset, _
                               culture As CultureInfo) As String
      Dim specifier As String = "yyyy/MM/dd"

      If Me.CalendarExists(culture) Then
         Console.WriteLine("Displaying date in supported {0} calendar...", _
                           thisCalendar.GetType().Name)
         culture.DateTimeFormat.Calendar = Me.thisCalendar
         Return dateToDisplay.ToString(specifier, culture)
      Else
         Console.WriteLine("Displaying date in unsupported {0} calendar...", _
                           thisCalendar.GetType().Name)

         Dim separator As String = targetCulture.DateTimeFormat.DateSeparator

         Return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") & separator & _
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") & separator & _
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00") 
      End If             
   End Function
End Class
' The example displays the following output to the console:
'       Using the system default culture: 7/3/2008
'       Using the ar-JO culture's original default calendar: 03/07/2008
'       Using the ar-JO culture with Hijri as the default calendar:
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       
'       Using the ir-FA culture's default calendar: 7/3/2008
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
```

Chaque objet [CultureInfo](xref:System.Globalization.CultureInfo) peut prendre en charge un ou plusieurs calendriers, indiqués par la propriété [OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars). L’un d’eux est désigné comme calendrier par défaut de la culture et est retourné par la propriété [CultureInfo.Calendar](xref:System.Globalization.CultureInfo.Calendar) en lecture seule. Un autre des calendriers facultatifs peut être désigné comme calendrier par défaut en attribuant un objet [Calendar](xref:System.Globalization.Calendar) qui représente ce calendrier pour la propriété [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) retournée par la propriété [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat). Toutefois, certains calendriers, tels que le calendrier persan représenté par la classe [PersianCalendar](xref:System.Globalization.PersianCalendar), ne servent de calendriers facultatifs pour aucune culture.   

L’exemple définit une classe utilitaire de calendrier réutilisable, `CalendarUtility`, pour gérer de nombreux détails de la génération de la représentation sous forme de chaîne d’une date à l’aide d’un calendrier particulier. La classe `CalendarUtility` possède les membres suivants : 

* Un constructeur paramétré dont le paramètre unique est un objet [Calendar](xref:System.Globalization.Calendar) dans lequel la date doit être représentée. Il est assigné à un champ privé de la classe.

* `CalendarExists`, méthode privée qui retourne une valeur booléenne indiquant si le calendrier représenté par l’objet `CalendarUtility` est pris en charge par l’objet [CultureInfo](xref:System.Globalization.CultureInfo) qui est passé à la méthode comme paramètre. La méthode inclut dans un wrapper un appel à la méthode [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})), à laquelle il transmet le tableau [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars).

* `HasSameName`, méthode privée assignée au délégué [Predicate&lt;T&gt;](xref:System.Predicate%601) qui est passé comme paramètre à la méthode [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})). Chaque membre du tableau est passé à la méthode jusqu’à ce qu’elle retourne `true`. La méthode détermine si le nom d’un calendrier facultatif est identique à celui du calendrier représenté par l’objet `CalendarUtility`.

* `DisplayDate`, méthode publique surchargée qui reçoit deux paramètres : une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) à exprimer dans le calendrier représenté par l’objet `CalendarUtility` et la culture dont les règles de mise en forme doivent être utilisées. La façon dont elle retourne la représentation sous forme de chaîne d’une date varie selon que le calendrier cible est pris en charge ou non par la culture dont les règles de mise en forme doivent être utilisées.

Quel que soit le calendrier utilisé pour créer une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) dans cet exemple, la valeur est généralement exprimée sous la forme d’une date du calendrier grégorien. En effet, les types [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset) ne conservent pas les informations de calendrier. En interne, elles sont représentées comme nombre de graduations qui se sont écoulées depuis le 1er janvier 0001 à minuit. L’interprétation de ce nombre dépend du calendrier. Pour la plupart des cultures, le calendrier par défaut est le calendrier grégorien. 

## <a name="see-also"></a>Voir aussi

[Exécution d’opérations de mise en forme](performing-formatting-operations.md)

