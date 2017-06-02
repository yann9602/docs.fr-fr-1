---
title: "Comment&#160;: cr&#233;er une forme &#224; l&#39;aide d&#39;un StreamGeometry | Microsoft Docs"
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
  - "classes, StreamGeometry"
  - "graphiques (WPF), formes"
  - "formes, créer avec la classe StreamGeometry"
  - "StreamGeometry (classe)"
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er une forme &#224; l&#39;aide d&#39;un StreamGeometry
<xref:System.Windows.Media.StreamGeometry> est une alternative légère de <xref:System.Windows.Media.PathGeometry> pour créer des formes géométriques.  Utilisez un <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe mais souhaitez éviter les charges mémoire liées à la prise en charge de la liaison des données, de l'animation ou du changement.  Par exemple, la classe <xref:System.Windows.Media.StreamGeometry> est un bon choix pour décrire des ornements en raison de son efficacité.  
  
## Exemple  
 L'exemple suivant utilise la syntaxe d'attribut pour créer un <xref:System.Windows.Media.StreamGeometry> triangulaire en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Pour plus d'informations sur la syntaxe d'attribut <xref:System.Windows.Media.StreamGeometry>, consultez la page [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.StreamGeometry> pour définir un triangle dans le code.  En premier lieu, l'exemple crée un <xref:System.Windows.Media.StreamGeometry>, puis obtient un <xref:System.Windows.Media.StreamGeometryContext> et l'utilise pour décrire le triangle.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## Exemple  
 L'exemple suivant crée une méthode qui utilise un <xref:System.Windows.Media.StreamGeometry> et <xref:System.Windows.Media.StreamGeometryContext> pour définir une forme géométrique en fonction des paramètres spécifiés.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## Voir aussi  
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Media.StreamGeometry>   
 <xref:System.Windows.Media.StreamGeometryContext>   
 [Créer une forme à l'aide d'un PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)   
 [Vue d'ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)