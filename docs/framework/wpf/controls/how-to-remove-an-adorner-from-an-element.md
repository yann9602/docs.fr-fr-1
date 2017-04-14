---
title: "Comment&#160;: supprimer un ornement d&#39;un &#233;l&#233;ment | Microsoft Docs"
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
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: supprimer un ornement d&#39;un &#233;l&#233;ment
Cet exemple montre comment supprimer par programme un ornement spécifique d'un <xref:System.Windows.UIElement> spécifié.  
  
## Exemple  
 Cet exemple de code en clair supprime le premier ornement du tableau des ornements retourné par <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Cet exemple récupère les ornements d'un <xref:System.Windows.UIElement> nommé *myTextBox*.  Si l'élément spécifié dans l'appel à <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> n'a pas d'ornements, `null` est retourné.  Ce code recherche explicitement un tableau null, et il est particulièrement adapté aux applications dans lesquelles un tableau null est supposé être relativement commun.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## Exemple  
 Cet exemple de code condensé est fonctionnellement équivalent à l'exemple en clair ci\-dessus.  Ce code ne recherche pas explicitement un tableau null. Par conséquent, une exception <xref:System.NullReferenceException> peut être levée.  Ce code est particulièrement adapté aux applications dans lesquelles un tableau null est supposé rare.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## Voir aussi  
 [Vue d'ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md)