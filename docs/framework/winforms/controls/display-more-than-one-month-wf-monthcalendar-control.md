---
title: "Comment&#160;: afficher plusieurs mois dans le contr&#244;le MonthCalendar Windows Forms | Microsoft Docs"
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
  - "calendriers, mettre en forme l'affichage"
  - "calendriers, plusieurs mois"
  - "exemples (Windows Forms), contrôles calendar"
  - "MonthCalendar (contrôle Windows Forms), mettre en forme l'affichage"
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: afficher plusieurs mois dans le contr&#244;le MonthCalendar Windows Forms
Le contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms peut afficher jusqu'à douze mois simultanément.  Par défaut, le contrôle n'affiche qu'un seul mois, mais vous pouvez spécifier le nombre de mois à afficher et leur disposition dans le contrôle.  Lorsque vous modifiez la taille du calendrier, le contrôle est redimensionné ; par conséquent, assurez\-vous que vous disposez de suffisamment d'espace dans le formulaire pour les nouvelles dimensions du calendrier.  
  
### Pour afficher plusieurs mois  
  
-   Attribuez à la propriété <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> le nombre de mois à afficher horizontalement et verticalement.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## Voir aussi  
 [MonthCalendar, contrôle](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [Comment : sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [Comment : modifier l'apparence du contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)