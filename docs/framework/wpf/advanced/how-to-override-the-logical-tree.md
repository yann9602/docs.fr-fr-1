---
title: "Comment&#160;: remplacer l&#39;arborescence logique | Microsoft Docs"
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
  - "arborescence logique, substituer"
  - "substituer l'arborescence logique"
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: remplacer l&#39;arborescence logique
Bien que cela ne soit pas nécessaire dans la plupart des cas, les auteurs de contrôle avancés peuvent remplacer l'[arborescence logique](GTMT).  
  
## Exemple  
 Cet exemple explique comment sous\-classer <xref:System.Windows.Controls.StackPanel> pour remplacer l'arborescence logique \(dans ce cas, pour appliquer un comportement que seul le panneau peut avoir et qui restitue un seul élément enfant\).  Ce comportement, qui n'est pas nécessairement souhaitable, est repris dans cet exemple afin d'illustrer le scénario permettant de remplacer l'arborescence logique normale d'un élément.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Pour plus d'informations sur l'arborescence logique, consultez [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).