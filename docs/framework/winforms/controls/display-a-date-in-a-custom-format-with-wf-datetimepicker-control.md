---
title: "Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms"
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
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b92fec7565aad2a881f714f9232eae10bf7633c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms
Windows Forms <xref:System.Windows.Forms.DateTimePicker> contrôle offre une grande souplesse dans la mise en forme l’affichage des dates et heures dans le contrôle. Le <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriété vous permet de sélectionner à partir des formats prédéfinis répertoriés dans le <xref:System.Windows.Forms.DateTimePickerFormat>. Si aucun de ces éléments est adaptée à vos besoins, vous pouvez créer votre propre style de format à l’aide de caractères de format répertoriés dans <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Pour afficher un format personnalisé  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur `DateTimePickerFormat.Custom`.  
  
2.  Définir le <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriété à une chaîne de format.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Pour ajouter du texte à la valeur mise en forme  
  
1.  Utilisez des guillemets simples pour encadrer tout caractère qui n’est pas un caractère de format comme « M » ou un délimiteur comme « : ». Par exemple, la chaîne de format ci-dessous affiche la date actuelle au format « aujourd'hui est : 05:30:31 vendredi 02 mars 2012 » dans l’anglais (États-Unis) de culture.  
  
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
  
     Selon le paramètre de culture, les caractères ne pas entourés de guillemets simples peuvent être modifiés. Par exemple, la chaîne de format ci-dessus affiche la date actuelle au format « aujourd'hui est : 05:30:31 vendredi 02 mars 2012 » dans l’anglais (États-Unis) de culture. Notez que le premier signe deux-points est placée entre guillemets simples, car elle n’est pas destinée à être un caractère de délimitation comme dans « hh : mm : ». Dans une autre culture, le format peut apparaître en tant que « aujourd'hui est : 05.30.31 vendredi 02 mars 2012 ».  
  
## <a name="see-also"></a>Voir aussi  
 [DateTimePicker, contrôle](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Guide pratique pour définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
