---
title: "DatePicker | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles (WPF), DatePicker"
  - "DatePicker (contrôle WPF)"
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# DatePicker
Le contrôle <xref:System.Windows.Controls.DatePicker> permet à l'utilisateur de sélectionner une date en la tapant dans un champ de texte ou en utilisant un contrôle <xref:System.Windows.Controls.Calendar> déroulant.  
  
 L'illustration suivante montre un <xref:System.Windows.Controls.DatePicker>.  
  
 ![Contrôle DatePicker](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP\_DatePicker")  
Contrôle de DatePicker  
  
 Une grande partie des propriétés d'un contrôle <xref:System.Windows.Controls.DatePicker> concernent la gestion de son <xref:System.Windows.Controls.Calendar> intégré et fonctionnent de manière identique à la propriété équivalente dans <xref:System.Windows.Controls.Calendar>.  En particulier, les propriétés <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=fullName>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=fullName>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=fullName>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=fullName>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=fullName>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=fullName> et <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=fullName> fonctionnent de manière identique à leurs équivalents <xref:System.Windows.Controls.Calendar>.  Pour plus d'informations, consultez <xref:System.Windows.Controls.Calendar>.  
  
 Les utilisateurs peuvent taper une date directement dans un champ de texte, ce qui définit la propriété <xref:System.Windows.Controls.DatePicker.Text%2A>.  Si le <xref:System.Windows.Controls.DatePicker> ne peut pas convertir la chaîne entrée en date valide, l'événement <xref:System.Windows.Controls.DatePicker.DateValidationError> est déclenché.  Par défaut, cela provoque une exception, mais un gestionnaire d'événements pour <xref:System.Windows.Controls.DatePicker.DateValidationError> peut affecter la valeur `false` à la propriété <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> et empêcher la levée d'une exception.  
  
## Voir aussi  
 [Contrôles](../../../../docs/framework/wpf/controls/index.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)