---
title: "Comment&#160;: r&#233;cup&#233;rer des donn&#233;es dans un format de donn&#233;es particulier | Microsoft Docs"
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
  - "classe DataFormats (WPF), récupérer des données"
  - "classe DataObject (WPF), récupérer des données"
  - "glisser-déplacer (WPF), récupérer des données"
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: r&#233;cup&#233;rer des donn&#233;es dans un format de donn&#233;es particulier
Les exemples suivants montrent comment récupérer des données depuis un objet de données dans un format déterminé.  
  
## Exemple  
  
### Description  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> pour vérifier si un format de données spécifié est disponible \(en mode natif ou par conversion automatique\) ; si le format spécifié est disponible, l'exemple récupère les données à l'aide de la méthode <xref:System.Windows.DataObject.GetData%28System.String%29>.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## Exemple  
  
### Description  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> pour vérifier si un format de données spécifié est disponible en mode natif \(les formats de données convertibles automatiquement sont filtrés\) ; si le format spécifié est disponible, l'exemple récupère les données à l'aide de la méthode <xref:System.Windows.DataObject.GetData%28System.String%29>.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## Voir aussi  
 <xref:System.Windows.IDataObject>   
 [Vue d'ensemble du glisser\-déplacer](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)