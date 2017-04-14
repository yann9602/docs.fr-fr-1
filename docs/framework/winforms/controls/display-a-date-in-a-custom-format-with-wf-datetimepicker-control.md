---
title: "Comment&#160;: afficher une date dans un format personnalis&#233; &#224; l&#39;aide du contr&#244;le DateTimePicker Windows Forms | Microsoft Docs"
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
  - "dates, afficher dans le contrôle DateTimePicker"
  - "DateTimePicker (contrôle Windows Forms), styles d'affichage"
  - "exemples (Windows Forms), DateTimePicker (contrôle)"
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: afficher une date dans un format personnalis&#233; &#224; l&#39;aide du contr&#244;le DateTimePicker Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.DateTimePicker> vous offre une grande souplesse en matière de format d'affichage des dates et des heures.  La propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> vous permet d'opérer une sélection dans la liste de formats prédéfinis fournie par <xref:System.Windows.Forms.DateTimePickerFormat>.  Si aucun de ces formats ne vous convient, vous pouvez créer le vôtre à l'aide des caractères de format proposés par <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### Pour afficher un format personnalisé  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur `DateTimePickerFormat.Custom`.  
  
2.  Définissez la propriété <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> en lui attribuant comme valeur une chaîne de format.  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### Pour ajouter le texte à la valeur mise en forme  
  
1.  Utilisez des guillemets simples autour de tout caractère qui ne constitue pas un caractère de mise en forme tel que "M" ou un délimiteur tel que ":".  Par exemple, la chaîne de format ci\-dessous affiche la date en cours dans le format "Today is: 05:30:31 Friday March 02, 2012" dans la culture anglais \(États\-Unis\).  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     En fonction du paramètre de culture, les caractères ne figurant pas entre guillemets simples risquent d'être modifiés.  Par exemple, la chaîne de format ci\-dessus affiche la date en cours dans le format "Today is: 05:30:31 Friday March 02, 2012" dans la culture anglais \(États\-Unis\).  Notez que le premier deux\-points figure entre guillemets simples, car il n'est pas supposé être un caractère de délimitation comme dans "hh:mm:ss".  Dans une autre, cette chaîne pourrait être : "Today is: 05.30.31 Friday March 02, 2012".  
  
## Voir aussi  
 [DateTimePicker, contrôle](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)   
 [Comment : définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)