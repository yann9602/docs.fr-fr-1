---
title: "Comment&#160;: tester l&#39;&#233;galit&#233; et l&#39;in&#233;galit&#233; de structures Point4D | Microsoft Docs"
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
  - "égalité, tester dans des structures Point4D"
  - "inégalité, tester dans des structures Point4D"
  - "structures Point4D, tester égalité"
  - "structures Point4D, tester inégalité"
  - "tester, égalité des structures Point4D"
  - "tester, inégalité des structures Point4D"
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: tester l&#39;&#233;galit&#233; et l&#39;in&#233;galit&#233; de structures Point4D
Cet exemple indique comment tester l'égalité et l'inégalité des structures <xref:System.Windows.Media.Media3D.Point4D>.  
  
 Le code suivant illustre comment tester l'égalité et l'inégalité des structures <xref:System.Windows.Media.Media3D.Point4D> à l'aide des méthodes d'égalité <xref:System.Windows.Media.Media3D.Point4D>.  L'égalité des structures <xref:System.Windows.Media.Media3D.Point4D> est testée à l'aide de l'opérateur d'égalité surchargé `==` tandis que leur inégalité est testée à l'aide de l'opérateur d'inégalité surchargé `!=`. Enfin, l'égalité des structures <xref:System.Windows.Media.Media3D.Point3D> et <xref:System.Windows.Media.Media3D.Point4D> est vérifiée à l'aide de la méthode statique <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>.  
  
## Exemple  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## Voir aussi  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>   
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>   
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>