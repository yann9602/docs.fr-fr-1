---
title: "Utilisation d&#39;un contr&#244;le ComboBox Windows Forms &#224; la place d&#39;un contr&#244;le ListBox | Microsoft Docs"
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
  - "contrôles dépendants, zones de liste déroulante"
  - "zones de liste déroulante, comparées aux zones de liste"
  - "ComboBox (contrôle Windows Forms), comparé à ListBox"
  - "ListBox (contrôle Windows Forms), accéder aux éléments"
  - "ListBox (contrôle Windows Forms), ajouter et enlever des éléments"
  - "ListBox (contrôle Windows Forms), et contrôle ComboBox"
  - "ListCount (propriété)"
  - "ListIndex (propriété)"
  - "contrôles Windows Forms, liaison de données"
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Utilisation d&#39;un contr&#244;le ComboBox Windows Forms &#224; la place d&#39;un contr&#244;le ListBox
Les contrôles <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> ont des comportements similaires et sont dans certains cas interchangeables.  Toutefois, dans certaines situations, l'un ou l'autre contrôle sera plus approprié à une tâche.  
  
 En général, une zone de liste déroulante est mieux adaptée à une liste de choix proposés, tandis qu'une zone de liste convient mieux lorsque le choix doit être limité aux éléments de la liste.  Une zone de liste déroulante contient un champ de zone de texte permettant de taper les éléments qui n'apparaissent pas dans la liste.  L'exception se produit lorsque la propriété <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> a la valeur <xref:System.Windows.Forms.ComboBoxStyle>.  Dans ce cas, le contrôle sélectionnera un élément si vous tapez sa première lettre.  
  
 En outre, les zones de liste déroulante économisent de la place dans un formulaire.  En effet, comme la liste n'est pas entièrement affichée tant que l'utilisateur ne clique pas sur la flèche vers le bas, la zone de liste déroulante peut aisément tenir dans un espace restreint qui ne serait pas suffisant pour une zone de liste.  Toutefois, cette règle ne se vérifie pas lorsque la propriété <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> a la valeur <xref:System.Windows.Forms.ComboBoxStyle> : dans ce cas, la liste complète est affichée et la zone de liste déroulante occupe alors plus de place que ne le ferait une zone de liste.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 [Comment : ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)