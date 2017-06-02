---
title: "Comment&#160;: d&#233;terminer si un format de donn&#233;es est pr&#233;sent dans un objet de donn&#233;es | Microsoft Docs"
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
  - "formats de données (WPF), déterminer s'ils sont présents"
  - "classe DataFormats (WPF)"
  - "glisser-déplacer (WPF), formats de données présents"
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: d&#233;terminer si un format de donn&#233;es est pr&#233;sent dans un objet de donn&#233;es
Les exemples suivants indiquent comment utiliser les différentes surcharges de méthode <xref:System.Windows.DataObject.GetDataPresent%2A> pour vérifier si un format de données particulier est présent dans un objet de données.  
  
## Exemple  
  
### Description  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> pour chercher la présence d'un format de données particulier par chaîne de descripteur.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## Exemple  
  
### Description  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> pour chercher la présence d'un format de données particulier par type.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## Exemple  
  
### Description  
 Le code d'exemple suivant utilise la surcharge <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> pour chercher des données par chaîne de descripteur, en spécifiant comment traiter des formats de données convertibles automatiquement.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## Voir aussi  
 <xref:System.Windows.IDataObject>