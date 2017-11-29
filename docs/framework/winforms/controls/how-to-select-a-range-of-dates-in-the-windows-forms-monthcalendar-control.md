---
title: "Comment : sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms"
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
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d6a8d156e6e9a8c5331bd3db1c8e584be5ac154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="97c90-102">Comment : sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97c90-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="97c90-103">Une fonctionnalité importante des Windows Forms <xref:System.Windows.Forms.MonthCalendar> contrôle est que l’utilisateur peut sélectionner une plage de dates.</span><span class="sxs-lookup"><span data-stu-id="97c90-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="97c90-104">Cette fonctionnalité est une amélioration de la fonctionnalité de sélection de date le <xref:System.Windows.Forms.DateTimePicker> contrôle, qui permet uniquement à l’utilisateur de sélectionner une valeur de date/heure unique.</span><span class="sxs-lookup"><span data-stu-id="97c90-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="97c90-105">Vous pouvez définir une plage de dates ou obtenir une plage de sélection définie par l’utilisateur à l’aide des propriétés de la <xref:System.Windows.Forms.MonthCalendar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="97c90-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="97c90-106">L’exemple de code suivant montre comment définir une plage de sélection.</span><span class="sxs-lookup"><span data-stu-id="97c90-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="97c90-107">Pour sélectionner une plage de dates</span><span class="sxs-lookup"><span data-stu-id="97c90-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="97c90-108">Créer <xref:System.DateTime> objets qui représentent les première et dernière dates dans une plage.</span><span class="sxs-lookup"><span data-stu-id="97c90-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  <span data-ttu-id="97c90-109">Définissez la propriété <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>.</span><span class="sxs-lookup"><span data-stu-id="97c90-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     <span data-ttu-id="97c90-110">– ou –</span><span class="sxs-lookup"><span data-stu-id="97c90-110">–or–</span></span>  
  
     <span data-ttu-id="97c90-111">Définissez les propriétés <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> et <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A>.</span><span class="sxs-lookup"><span data-stu-id="97c90-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97c90-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97c90-112">See Also</span></span>  
 [<span data-ttu-id="97c90-113">MonthCalendar, contrôle</span><span class="sxs-lookup"><span data-stu-id="97c90-113">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="97c90-114">Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97c90-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="97c90-115">Guide pratique pour afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97c90-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="97c90-116">Guide pratique pour afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97c90-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
