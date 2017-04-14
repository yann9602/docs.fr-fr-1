---
title: "Comment&#160;: trier le contenu d&#39;un contr&#244;le ComboBox, CheckedListBox ou ListBox Windows Forms | Microsoft Docs"
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
  - "CheckedListBox (contrôle Windows Forms), trier"
  - "zones de liste déroulante, trier le contenu"
  - "ComboBox (contrôle Windows Forms), trier le contenu"
  - "zones de liste, trier le contenu"
  - "ListBox (contrôle Windows Forms), trier le contenu"
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: trier le contenu d&#39;un contr&#244;le ComboBox, CheckedListBox ou ListBox Windows Forms
Les contrôles Windows Forms ne trient pas leurs contenus quand ils sont liés à des données.  Pour afficher les données triées, utilisez une source de données prenant en charge cette fonction et demandez le tri.  Les sources de données qui prennent en charge le tri sont les vues de données, les gestionnaires de vue de données et les tableaux triés.  
  
 Si le contrôle n'est pas lié aux données, vous pouvez le trier.  
  
### Pour trier la liste  
  
1.  Affectez à la propriété  `Sorted`  la valeur `true`.  
  
     Ce paramètre repositionne tous les éléments de liste existants dans l'ordre de tri.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Comment : ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)