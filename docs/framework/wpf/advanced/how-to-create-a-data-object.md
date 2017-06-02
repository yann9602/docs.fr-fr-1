---
title: "Comment&#160;: cr&#233;er un objet de donn&#233;es | Microsoft Docs"
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
  - "objets de données (WPF), créer"
  - "classe DataObject (WPF), créer"
  - "glisser-déplacer (WPF), créer des objets de données"
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: cr&#233;er un objet de donn&#233;es
Les exemples suivants indiquent différentes manières de créer un objet de données à l'aide des constructeurs fournis par la classe <xref:System.Windows.DataObject>.  
  
## Exemple  
  
### Description  
 L'exemple de code suivant crée un objet de données et utilise l'un des constructeurs surchargés \(<xref:System.Windows.DataObject.%23ctor%28System.Object%29>\) pour initialiser l'objet de données à l'aide d'une chaîne.  Dans ce cas, un format de données approprié est déterminé automatiquement d'après le type des données stockées, et la conversion automatique des données stockées est autorisée par défaut.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### Description  
 L'exemple de code suivant est une version condensée du code ci\-dessus.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## Exemple  
  
### Description  
 L'exemple de code suivant crée un objet de données et utilise l'un des constructeurs surchargés \(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>\) pour initialiser l'objet de données à l'aide d'une chaîne et d'un format de données spécifié.  Dans ce cas, le format de données est spécifié par une chaîne ; la classe <xref:System.Windows.DataFormats> fournit un ensemble de chaînes de type prédéfinies.  La conversion automatique des données stockées est autorisée par défaut.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### Description  
 L'exemple de code suivant est une version condensée du code ci\-dessus.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## Exemple  
  
### Description  
 L'exemple de code suivant crée un objet de données et utilise l'un des constructeurs surchargés \(<xref:System.Windows.DataObject.%23ctor%2A>\) pour initialiser l'objet de données à l'aide d'une chaîne et d'un format de données spécifié.  Dans ce cas, le format de données est spécifié par un paramètre <xref:System.Type>.  La conversion automatique des données stockées est autorisée par défaut.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### Description  
 L'exemple de code suivant est une version condensée du code ci\-dessus.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## Exemple  
  
### Description  
 L'exemple de code suivant crée un objet de données et utilise l'un des constructeurs surchargés \(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>\) pour initialiser l'objet de données à l'aide d'une chaîne et d'un format de données spécifié.  Dans ce cas, le format de données est spécifié par une chaîne ; la classe <xref:System.Windows.DataFormats> fournit un ensemble de chaînes de type prédéfinies.  Cette surcharge de constructeur particulière permet à l'appelant de spécifier si la conversion automatique est autorisée.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### Description  
 L'exemple de code suivant est une version condensée du code ci\-dessus.  
  
### Code  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## Voir aussi  
 <xref:System.Windows.IDataObject>