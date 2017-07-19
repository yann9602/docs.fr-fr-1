---
title: "Comment : orner les enfants d&#39;un Panel | Microsoft Docs"
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
  - "ornements, lier aux enfants de contrôles Panel"
  - "Panel (contrôle), lier des ornements aux enfants"
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment : orner les enfants d&#39;un Panel
Cet exemple montre comment lier par programme un ornement aux enfants d'un <xref:System.Windows.Controls.Panel> spécifié.  
  
## Exemple  
 Pour lier un ornement aux enfants d'un <xref:System.Windows.Controls.Panel>, suivez ces étapes :  
  
1.  Déclarez un nouvel objet <xref:System.Windows.Documents.AdornerLayer> et appelez `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour rechercher une couche d'ornement pour l'élément dont les enfants seront ornés.  
  
2.  Énumérez les enfants de l'élément parent et appelez la méthode <xref:System.Windows.Documents.AdornerLayer.Add%2A> pour lier un ornement à chaque élément enfant.  
  
 L'exemple suivant lie un SimpleCircleAdorner \(montré ci\-dessus\) aux enfants d'un <xref:System.Windows.Controls.StackPanel> nommé *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  L'utilisation de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n'est pas prise en charge actuellement.  
  
## Voir aussi  
 [Vue d'ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md)