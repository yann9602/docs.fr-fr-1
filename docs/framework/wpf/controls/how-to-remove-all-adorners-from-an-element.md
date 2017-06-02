---
title: "Comment&#160;: supprimer tous les ornements d&#39;un &#233;l&#233;ment | Microsoft Docs"
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
  - "ornements, supprimer"
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: supprimer tous les ornements d&#39;un &#233;l&#233;ment
Cet exemple montre comment supprimer par programme tous les ornements d'un <xref:System.Windows.UIElement> spécifié.  
  
## Exemple  
 Cet exemple de code en clair supprime tous les ornements dans le tableau des ornements retourné par <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Cet exemple récupère les ornements d'un <xref:System.Windows.UIElement> nommé *myTextBox*.  Si l'élément spécifié dans l'appel à <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> n'a pas d'ornements, `null` est retourné.  Ce code recherche explicitement un tableau null, et il est particulièrement adapté aux applications dans lesquelles un tableau null est supposé être relativement commun.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## Exemple  
 Cet exemple de code condensé est fonctionnellement équivalent à l'exemple en clair ci\-dessus.  Ce code ne recherche pas explicitement un tableau null. Par conséquent, une exception <xref:System.NullReferenceException> peut être levée.  Ce code est particulièrement adapté aux applications dans lesquelles un tableau null est supposé rare.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## Voir aussi  
 [Vue d'ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md)