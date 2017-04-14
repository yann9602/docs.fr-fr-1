---
title: "Vue d&#39;ensemble du contr&#244;le DateTimePicker (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DateTimePicker"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles Date Time Picker"
  - "DateTimePicker (contrôle Windows Forms), à propos de"
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Vue d&#39;ensemble du contr&#244;le DateTimePicker (Windows Forms)
Le contrôle <xref:System.Windows.Forms.DateTimePicker> Windows Forms permet à l'utilisateur de sélectionner un élément dans une liste de dates ou d'heures.  Lorsqu'il est utilisé pour représenter une date, il se compose de deux parties : une liste déroulante contenant une date sous forme de texte et une grille qui apparaît lorsque vous cliquez sur la flèche bas affichée en regard de la liste.  La grille ressemble à celle du contrôle <xref:System.Windows.Forms.MonthCalendar>, qui permet de sélectionner plusieurs dates.  Pour plus d'informations sur le contrôle <xref:System.Windows.Forms.MonthCalendar>, consultez [Vue d'ensemble du contrôle MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md).  
  
## Propriétés de clé  
 Si vous souhaitez que <xref:System.Windows.Forms.DateTimePicker> apparaisse comme un contrôle permettant de choisir ou de modifier des heures en remplacement des dates, affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> la valeur `true` et à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur <xref:System.Windows.Forms.DateTimePickerFormat>.  Pour plus d'informations, consultez [Comment : afficher l'heure avec le contrôle DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
 Lorsque la propriété <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> a la valeur `true`, une case à cocher s'affiche en regard de la date sélectionnée dans le contrôle.  Lorsque cette case est cochée, la valeur date\-heure sélectionnée peut être mise à jour.  Dans le cas contraire, la valeur apparaît comme indisponible.  
  
 Les propriétés <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> et <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> du contrôle déterminent la plage de dates et d'heures.  La propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> contient la valeur date\-heure actuelle du contrôle.  Pour plus d'informations, consultez [Comment : définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md).  Les valeurs peuvent être affichées dans les quatre formats définis par la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> : <xref:System.Windows.Forms.DateTimePickerFormat>, <xref:System.Windows.Forms.DateTimePickerFormat>, <xref:System.Windows.Forms.DateTimePickerFormat> ou <xref:System.Windows.Forms.DateTimePickerFormat>.  Si un format personnalisé est sélectionné, vous devez définir une chaîne appropriée pour la propriété <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  Pour plus d'informations, consultez [Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md).  
  
## Voir aussi  
 [Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)   
 [Comment : définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)