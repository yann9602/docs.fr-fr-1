---
title: "Vue d&#39;ensemble du contr&#244;le MonthCalendar (Windows Forms) | Microsoft Docs"
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
  - "MonthCalendar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles calendar, Windows Forms"
  - "calendriers, contrôles Windows Forms"
  - "MonthCalendar (contrôle Windows Forms), définir le premier jour de la semaine"
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du contr&#244;le MonthCalendar (Windows Forms)
Le contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms présente une interface graphique intuitive permettant aux utilisateurs d'afficher et de définir des informations de date.  Il affiche un calendrier qui se présente sous la forme d'une grille contenant les quantièmes du mois en cours, disposés en colonnes sous les jours de la semaine et où la plage de dates sélectionnée est en surbrillance.  Vous pouvez sélectionner un mois différent en cliquant sur les boutons de direction affichés de part et d'autre du nom du mois.  À la différence du contrôle <xref:System.Windows.Forms.DateTimePicker> dont il est pourtant similaire, vous pouvez sélectionner plusieurs dates à l'aide de ce contrôle.  Pour plus d'informations sur le contrôle <xref:System.Windows.Forms.DateTimePicker>, consultez [DateTimePicker, contrôle](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).  
  
## Configuration du contrôle MonthCalendar  
 L'apparence du contrôle <xref:System.Windows.Forms.MonthCalendar> peut être modifiée dans une large mesure.  Par défaut, la date du jour est entourée d'un cercle et apparaît également au bas de la grille.  Vous pouvez modifier cette fonctionnalité en affectant aux propriétés <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> et <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> la valeur `false`.  Vous pouvez également ajouter des numéros de semaine au calendrier en affectant à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`.  En définissant la propriété <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>, vous pouvez afficher plusieurs mois horizontalement et verticalement.  Par défaut, dimanche est le premier jour de la semaine, mais vous pouvez choisir un autre jour à l'aide de la propriété <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>.  
  
 Vous pouvez également définir l'affichage en gras de certaines dates sur une base occasionnelle, annuelle ou mensuelle, en ajoutant des objets <xref:System.DateTime> aux propriétés <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> et <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>.  Pour plus d'informations, consultez [Comment : afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).  
  
 La principale propriété du contrôle <xref:System.Windows.Forms.MonthCalendar> est <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, qui correspond à la plage de dates sélectionnée dans le contrôle.  La valeur <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> ne peut pas dépasser le nombre maximal de jours pouvant être sélectionnés, ce nombre étant défini dans la propriété <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>.  Les premières et dernières dates que l'utilisateur peut sélectionner sont déterminées par les propriétés <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> et <xref:System.Windows.Forms.MonthCalendar.MinDate%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MonthCalendar>   
 [MonthCalendar, contrôle](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)