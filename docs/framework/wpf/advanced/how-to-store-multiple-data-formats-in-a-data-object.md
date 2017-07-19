---
title: "Comment&#160;: stocker plusieurs formats de donn&#233;es dans un objet de donn&#233;es | Microsoft Docs"
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
  - "classe DataFormats (WPF), stocker plusieurs formats"
  - "classe DataObject (WPF), stocker plusieurs formats"
  - "glisser-déplacer (WPF), stocker plusieurs formats"
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: stocker plusieurs formats de donn&#233;es dans un objet de donn&#233;es
L'exemple suivant montre comment utiliser la méthode <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> pour ajouter des données à un objet de données dans plusieurs formats.  
  
## Exemple  
  
### Description  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## Voir aussi  
 <xref:System.Windows.IDataObject>   
 [Vue d'ensemble du glisser\-déplacer](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)