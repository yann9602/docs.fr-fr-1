---
title: "Comment&#160;: afficher en gras certains jours &#224; l&#39;aide du contr&#244;le MonthCalendar Windows Forms | Microsoft Docs"
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
  - "calendriers, afficher les dates en gras"
  - "exemples (Windows Forms), contrôles calendar"
  - "GetDayBold (événement)"
  - "MonthCalendar (contrôle Windows Forms), dates affichées en caractères gras"
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: afficher en gras certains jours &#224; l&#39;aide du contr&#244;le MonthCalendar Windows Forms
Le contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms peut afficher les jours en gras, de manière répétitive ou pour des dates isolées.  Vous utiliserez l'affichage en gras, par exemple, pour attirer l'attention du lecteur sur certaines dates, telles que les jours fériés ou les week\-ends.  
  
 Trois propriétés contrôlent cette fonctionnalité.  La propriété <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> contient des dates isolées.  La propriété <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> contient des dates qui apparaissent en gras chaque année.  La propriété <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> contient des dates qui apparaissent en gras chaque mois.  Chacune de ces propriétés contient un tableau d'objets <xref:System.DateTime>.  Pour ajouter ou supprimer une date d'une de ces listes, vous devez ajouter ou supprimer un objet <xref:System.DateTime>.  
  
### Pour faire apparaître une date en gras  
  
1.  Créez les objets <xref:System.DateTime>.  
  
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
  
2.  Pour afficher en gras une date isolée, appelez la méthode <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A> ou <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> du contrôle <xref:System.Windows.Forms.MonthCalendar>.  
  
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
  
     \- ou \-  
  
     Pour afficher simultanément en gras un groupe de dates, créez un tableau d'objets <xref:System.DateTime> et assignez\-le à l'une des propriétés.  
  
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
  
### Pour faire apparaître une date sans mise en forme  
  
1.  Pour afficher sans mise en forme une date qui est en gras, appelez la méthode <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A> ou <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>.  
  
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
  
     \- ou \-  
  
     Pour supprimer toutes les dates en gras de l'une des trois listes, appelez la méthode <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A> ou <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  Mettez à jour l'apparence de la police en appelant la méthode <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## Voir aussi  
 [MonthCalendar, contrôle](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [Comment : sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [Comment : modifier l'apparence du contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)   
 [Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)