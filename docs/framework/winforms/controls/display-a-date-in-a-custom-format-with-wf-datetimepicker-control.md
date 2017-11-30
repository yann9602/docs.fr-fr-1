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
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="88546-102">Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88546-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="88546-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> contrôle offre une grande souplesse dans la mise en forme l’affichage des dates et heures dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="88546-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="88546-104">Le <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriété vous permet de sélectionner à partir des formats prédéfinis répertoriés dans le <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="88546-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="88546-105">Si aucun de ces éléments est adaptée à vos besoins, vous pouvez créer votre propre style de format à l’aide de caractères de format répertoriés dans <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="88546-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="88546-106">Pour afficher un format personnalisé</span><span class="sxs-lookup"><span data-stu-id="88546-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="88546-107">Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="88546-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="88546-108">Définir le <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriété à une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="88546-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="88546-109">Pour ajouter du texte à la valeur mise en forme</span><span class="sxs-lookup"><span data-stu-id="88546-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="88546-110">Utilisez des guillemets simples pour encadrer tout caractère qui n’est pas un caractère de format comme « M » ou un délimiteur comme « : ».</span><span class="sxs-lookup"><span data-stu-id="88546-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="88546-111">Par exemple, la chaîne de format ci-dessous affiche la date actuelle au format « aujourd'hui est : 05:30:31 vendredi 02 mars 2012 » dans l’anglais (États-Unis) de culture.</span><span class="sxs-lookup"><span data-stu-id="88546-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="88546-112">Selon le paramètre de culture, les caractères ne pas entourés de guillemets simples peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="88546-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="88546-113">Par exemple, la chaîne de format ci-dessus affiche la date actuelle au format « aujourd'hui est : 05:30:31 vendredi 02 mars 2012 » dans l’anglais (États-Unis) de culture.</span><span class="sxs-lookup"><span data-stu-id="88546-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="88546-114">Notez que le premier signe deux-points est placée entre guillemets simples, car elle n’est pas destinée à être un caractère de délimitation comme dans « hh : mm : ».</span><span class="sxs-lookup"><span data-stu-id="88546-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="88546-115">Dans une autre culture, le format peut apparaître en tant que « aujourd'hui est : 05.30.31 vendredi 02 mars 2012 ».</span><span class="sxs-lookup"><span data-stu-id="88546-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88546-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88546-116">See Also</span></span>  
 [<span data-ttu-id="88546-117">DateTimePicker, contrôle</span><span class="sxs-lookup"><span data-stu-id="88546-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="88546-118">Guide pratique pour définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88546-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
