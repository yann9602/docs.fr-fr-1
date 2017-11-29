---
title: "Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms"
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
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cf236f93fa3352e536c71000f6bb110abf02fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="b1026-102">Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1026-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="b1026-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> contrôle peut afficher jusqu'à 12 mois à la fois.</span><span class="sxs-lookup"><span data-stu-id="b1026-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="b1026-104">Par défaut, le contrôle affiche uniquement un mois, mais vous pouvez spécifier le nombre de mois est affiché, et comment ils sont réorganisés dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b1026-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="b1026-105">Lorsque vous modifiez la taille du calendrier, le contrôle est redimensionné, veillez donc à que l’espace est suffisant sur le formulaire pour les nouvelles dimensions.</span><span class="sxs-lookup"><span data-stu-id="b1026-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="b1026-106">Pour afficher plusieurs mois</span><span class="sxs-lookup"><span data-stu-id="b1026-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="b1026-107">Définir le <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> propriété au nombre de mois à afficher horizontalement et verticalement.</span><span class="sxs-lookup"><span data-stu-id="b1026-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b1026-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1026-108">See Also</span></span>  
 [<span data-ttu-id="b1026-109">MonthCalendar, contrôle</span><span class="sxs-lookup"><span data-stu-id="b1026-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="b1026-110">Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1026-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="b1026-111">Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1026-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
