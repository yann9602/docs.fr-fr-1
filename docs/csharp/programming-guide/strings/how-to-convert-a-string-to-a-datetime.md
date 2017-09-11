---
title: "Comment : convertir une chaîne en DateTime (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 15ef1ec4debf242cdabc42f26add890bd4b61507
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a><span data-ttu-id="013d8-102">Comment : convertir une chaîne en DateTime (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="013d8-102">How to: Convert a String to a DateTime (C# Programming Guide)</span></span>
<span data-ttu-id="013d8-103">Les programmes permettent couramment aux utilisateurs d’entrer des dates sous forme de valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="013d8-103">It is common for programs to enable users to enter dates as string values.</span></span> <span data-ttu-id="013d8-104">Pour convertir une date basée sur une chaîne en objet <xref:System.DateTime?displayProperty=fullName> , vous pouvez utiliser la méthode <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> ou la méthode statique <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> , comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="013d8-104">To convert a string-based date to a <xref:System.DateTime?displayProperty=fullName> object, you can use the <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> method or the <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> static method, as shown in the following example.</span></span>  
  
 <span data-ttu-id="013d8-105">**Culture**.</span><span class="sxs-lookup"><span data-stu-id="013d8-105">**Culture**.</span></span>  <span data-ttu-id="013d8-106">Le format d’écriture des chaînes de date varie selon la culture.</span><span class="sxs-lookup"><span data-stu-id="013d8-106">Different cultures in the world write date strings in different ways.</span></span>  <span data-ttu-id="013d8-107">Par exemple, aux États-Unis, le 20 janvier 2008 s’écrit 01/20/2008.</span><span class="sxs-lookup"><span data-stu-id="013d8-107">For example, in the US 01/20/2008 is January 20th, 2008.</span></span>  <span data-ttu-id="013d8-108">En France, cette date lève l’exception InvalidFormatException.</span><span class="sxs-lookup"><span data-stu-id="013d8-108">In France this will throw an InvalidFormatException.</span></span> <span data-ttu-id="013d8-109">Cela vient du fait que la France utilise le format de date jour/mois/année, alors que les États-Unis utilisent mois/jour/année.</span><span class="sxs-lookup"><span data-stu-id="013d8-109">This is because France reads date-times as Day/Month/Year, and in the US it is Month/Day/Year.</span></span>  
  
 <span data-ttu-id="013d8-110">Une chaîne telle que 20/01/2008 correspond donc bien au 20 janvier 2008 en France, mais elle lève l’exception InvalidFormatException aux États-Unis</span><span class="sxs-lookup"><span data-stu-id="013d8-110">Consequently, a string like 20/01/2008 will parse to January 20th, 2008 in France, and then throw an InvalidFormatException in the US.</span></span>  
  
 <span data-ttu-id="013d8-111">Pour déterminer vos paramètres de culture actuels, vous pouvez utiliser System.Globalization.CultureInfo.CurrentCulture.</span><span class="sxs-lookup"><span data-stu-id="013d8-111">To determine your current culture settings, you can use System.Globalization.CultureInfo.CurrentCulture.</span></span>  
  
 <span data-ttu-id="013d8-112">Un exemple simple de conversion d’une chaîne en dateTime est présenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="013d8-112">See the example below for a simple example of converting a string to dateTime.</span></span>  
  
 <span data-ttu-id="013d8-113">Pour obtenir d’autres exemples de chaînes de date, consultez <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="013d8-113">For more examples of date strings, see <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.</span></span>  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a><span data-ttu-id="013d8-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="013d8-114">Example</span></span>  
 <span data-ttu-id="013d8-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="013d8-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013d8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="013d8-116">See Also</span></span>  
 [<span data-ttu-id="013d8-117">Chaînes</span><span class="sxs-lookup"><span data-stu-id="013d8-117">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

