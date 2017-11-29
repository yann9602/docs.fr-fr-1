---
title: "Comment : afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18a199592a8bfbef2e4a15b056e37af6d885f5f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="3b3ef-102">Comment : afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ef-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="3b3ef-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> contrôle peut afficher les jours en gras, en tant que dates au singulier ou répétitive.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="3b3ef-104">Vous pouvez procéder pour attirer l’attention sur des dates spéciaux, tels que les week-ends et jours fériés.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="3b3ef-105">Trois propriétés de contrôler cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-105">Three properties control this feature.</span></span> <span data-ttu-id="3b3ef-106">Le <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> propriété contient des dates uniques.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="3b3ef-107">Le <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> propriété contient des dates qui apparaissent en gras chaque année.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="3b3ef-108">Le <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> propriété contient des dates qui apparaissent en gras chaque mois.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="3b3ef-109">Chacune de ces propriétés contient un tableau de <xref:System.DateTime> objets.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="3b3ef-110">Pour ajouter ou supprimer une date à partir d’une de ces listes, vous devez ajouter ou supprimer un <xref:System.DateTime> objet.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="3b3ef-111">Pour afficher une date en gras</span><span class="sxs-lookup"><span data-stu-id="3b3ef-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="3b3ef-112">Créer le <xref:System.DateTime> objets.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-112">Create the <xref:System.DateTime> objects.</span></span>  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2.  <span data-ttu-id="3b3ef-113">Afficher une seule date en gras en appelant le <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, ou <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> méthode de la <xref:System.Windows.Forms.MonthCalendar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     <span data-ttu-id="3b3ef-114">– ou –</span><span class="sxs-lookup"><span data-stu-id="3b3ef-114">–or–</span></span>  
  
     <span data-ttu-id="3b3ef-115">Afficher un ensemble de dates en gras à la fois en créant un tableau de <xref:System.DateTime> objets et assignez-le à l’une des propriétés.</span><span class="sxs-lookup"><span data-stu-id="3b3ef-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="3b3ef-116">Pour afficher une date dans la police normale</span><span class="sxs-lookup"><span data-stu-id="3b3ef-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="3b3ef-117">Afficher une date dans la police normale en appelant le <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, ou <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3b3ef-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     <span data-ttu-id="3b3ef-118">– ou –</span><span class="sxs-lookup"><span data-stu-id="3b3ef-118">–or–</span></span>  
  
     <span data-ttu-id="3b3ef-119">Supprimer toutes les dates en gras de l’une des trois listes en appelant le <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, ou <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3b3ef-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="3b3ef-120">Mettre à jour l’apparence de la police en appelant le <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3b3ef-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3b3ef-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b3ef-121">See Also</span></span>  
 [<span data-ttu-id="3b3ef-122">MonthCalendar, contrôle</span><span class="sxs-lookup"><span data-stu-id="3b3ef-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="3b3ef-123">Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ef-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="3b3ef-124">Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ef-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="3b3ef-125">Guide pratique pour afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b3ef-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
