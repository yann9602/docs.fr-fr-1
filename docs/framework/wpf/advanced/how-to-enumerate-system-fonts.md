---
title: "Comment&#160;: &#233;num&#233;rer des polices syst&#232;me | Microsoft Docs"
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
  - "énumérer, polices système"
  - "polices, énumérer"
  - "polices système, énumérer"
  - "typographie, énumérer les polices système"
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: &#233;num&#233;rer des polices syst&#232;me
## Exemple  
 L'exemple suivant indique comment énumérer les polices dans la collection de polices système.  Le nom de la famille de polices de chaque <xref:System.Windows.Media.FontFamily> dans <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> est ajouté comme élément à une zone de liste déroulante.  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Si plusieurs versions de la même famille de polices résident dans le même répertoire, l'énumération de police [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] retourne la version de la police la plus récente.  Si les informations de version ne fournissent pas de résolution, la police avec l'horodatage le plus récent est retournée.  Si les informations d'horodatage sont équivalentes, le fichier de police qui est en premier par ordre alphabétique est retourné.