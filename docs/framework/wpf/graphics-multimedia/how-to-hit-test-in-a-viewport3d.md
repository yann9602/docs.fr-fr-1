---
title: "Comment&#160;: effectuer un test de positionnement dans un Viewport3D | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "objets visuels 3D, exécuter un test de positionnement pour"
  - "tests de positionnement, pour les objets visuels 3D"
  - "Viewport3D"
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: effectuer un test de positionnement dans un Viewport3D
Cet exemple montre comment effectuer un test de positionnement pour des objets visuels 3D dans un <xref:System.Windows.Controls.Viewport3D>.  
  
 Du fait que <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retourne des informations 2D et 3D, il est possible d'itérer au sein des résultats des tests pour lire uniquement les résultats de 3D.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 Le <xref:System.Windows.Media.HitTestResultBehavior> dans le code suivant détermine la manière dont les résultats de test de positionnement sont traités.  `UpdateResultInfo` et `UpdateMaterial` sont des méthodes définies localement.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## Voir aussi  
 [Test de positionnement 3D, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159959)