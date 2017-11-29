---
title: "Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e43a23d632b397889721373471a8fa165052d7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms
Contrôles Windows Forms ne triez pas lorsqu’ils sont liés aux données. Pour afficher les données triées, utilisez une source de données qui prend en charge le tri et devez ensuite trier la source de données. Les sources de données qui prennent en charge le tri sont les vues de données, les gestionnaires de vues de données et les tableaux triés.  
  
 Si le contrôle n’est pas lié aux données, vous pouvez les trier.  
  
### <a name="to-sort-the-list"></a>Pour trier la liste  
  
1.  Affectez à la propriété `Sorted` la valeur `true`.  
  
     Ce paramètre repositionne tous les éléments de liste existants dans un ordre trié.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
