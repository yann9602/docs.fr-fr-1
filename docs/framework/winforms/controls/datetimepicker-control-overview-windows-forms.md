---
title: "Vue d'ensemble du contrôle DateTimePicker (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0db5e532a2688d7f213fd42772234b9600192390
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datetimepicker-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DateTimePicker (Windows Forms)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> contrôle permet à l’utilisateur à sélectionner un seul élément dans une liste de dates ou d’heures. Lorsqu’il est utilisé pour représenter une date, il s’affiche en deux parties : une liste déroulante contenant une date sous forme de texte et une grille qui s’affiche lorsque vous cliquez sur la flèche bas en regard de la liste. La grille ressemble à la <xref:System.Windows.Forms.MonthCalendar> contrôle, qui peut être utilisé pour sélectionner plusieurs dates. Pour plus d’informations sur la <xref:System.Windows.Forms.MonthCalendar> du contrôle, consultez [vue d’ensemble du contrôle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md).  
  
## <a name="key-properties"></a>Propriétés de clé  
 Si vous le souhaitez la <xref:System.Windows.Forms.DateTimePicker> apparaisse comme un contrôle permettant de choisir ou de modifier des heures au lieu de dates, définissez la <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> propriété `true` et <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriété <xref:System.Windows.Forms.DateTimePickerFormat.Time>. Pour plus d’informations, consultez [Comment : afficher l’heure avec le contrôle DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
 Lorsque le <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> est définie sur `true`, une case à cocher s’affiche en regard de la date sélectionnée dans le contrôle. Quand la case à cocher est activée, la valeur de date-heure sélectionnée peut être mis à jour. Lorsque la case à cocher est vide, la valeur apparaît comme indisponible.  
  
 Du contrôle <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> et <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> propriétés déterminent la plage de dates et heures. Le <xref:System.Windows.Forms.DateTimePicker.Value%2A> propriété contient la date et heure actuelles du contrôle est défini sur. Pour plus d’informations, consultez [Comment : ensemble et retourner des Dates avec le contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md). Les valeurs peuvent être affichées dans les quatre formats définis par le <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriété : <xref:System.Windows.Forms.DateTimePickerFormat.Long>, <xref:System.Windows.Forms.DateTimePickerFormat.Short>, <xref:System.Windows.Forms.DateTimePickerFormat.Time>, ou <xref:System.Windows.Forms.DateTimePickerFormat.Custom>. Si un format personnalisé est sélectionné, vous devez définir le <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriété à une chaîne appropriée. Pour plus d’informations, consultez [Comment : afficher une Date dans un Format personnalisé avec le contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [Guide pratique pour définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
