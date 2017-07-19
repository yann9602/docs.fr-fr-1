---
title: "Comment&#160;: s&#233;lectionner une plage de dates dans le contr&#244;le MonthCalendar Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "calendriers, sélectionner une plage de dates"
  - "dates, sélectionner une plage dans les contrôles Calendar"
  - "exemples (Windows Forms), contrôles calendar"
  - "MonthCalendar (contrôle Windows Forms), sélectionner une plage de dates"
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: s&#233;lectionner une plage de dates dans le contr&#244;le MonthCalendar Windows Forms
Une fonctionnalité importante du contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms permet à l'utilisateur de sélectionner une plage de dates.  Cette fonctionnalité est une amélioration de la fonctionnalité de sélection de date du contrôle <xref:System.Windows.Forms.DateTimePicker> qui permet uniquement à l'utilisateur de sélectionner une seule valeur de date\/d'heure.  Vous pouvez définir une plage de dates ou obtenir une plage de sélection définie par l'utilisateur en utilisant des propriétés du contrôle <xref:System.Windows.Forms.MonthCalendar>.  L'exemple de code suivant montre comment définir une plage de sélection.  
  
### Pour sélectionner une plage de dates  
  
1.  Créez des objets <xref:System.DateTime> qui représentent la première et la dernière dates d'une plage.  
  
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
  
2.  Définissez la propriété <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>.  
  
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
  
     \- ou \-  
  
     Définissez les propriétés <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> et <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A>.  
  
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
  
## Voir aussi  
 [MonthCalendar, contrôle](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [Comment : modifier l'apparence du contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)   
 [Comment : afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)   
 [Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)