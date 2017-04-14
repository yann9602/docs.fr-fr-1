---
title: "Comment&#160;: r&#233;pertorier les formats de donn&#233;es dans un objet de donn&#233;es | Microsoft Docs"
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
  - "formats de données (WPF), répertorier"
  - "classe DataFormats (WPF)"
  - "glisser-déplacer (WPF), répertorier des formats de données"
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: r&#233;pertorier les formats de donn&#233;es dans un objet de donn&#233;es
Les exemples suivants indiquent comment utiliser les surcharges de méthode <xref:System.Windows.DataObject.GetFormats%2A> pour obtenir un tableau de chaînes qui désigne chaque format de données disponible dans un objet de données.  
  
## Exemple  
  
### Description  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetFormats%2A> pour obtenir un tableau de chaînes qui désigne tous les formats de données disponibles dans un objet de données \(formats natifs et convertibles automatiquement\).  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## Exemple  
  
### Description  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetFormats%2A> pour obtenir un tableau de chaînes qui désigne uniquement les formats de données disponibles dans un objet de données \(les formats de données convertibles automatiquement sont filtrés\).  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## Voir aussi  
 <xref:System.Windows.IDataObject>   
 [Vue d'ensemble du glisser\-déplacer](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)