---
title: "Comment&#160;: substituer les m&#233;tadonn&#233;es d&#39;une propri&#233;t&#233; de d&#233;pendance | Microsoft Docs"
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
  - "propriétés de dépendance, substituer des métadonnées pour"
  - "métadonnées, substituer pour des propriétés de dépendance"
  - "substituer des métadonnées pour des propriétés de dépendance"
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: substituer les m&#233;tadonn&#233;es d&#39;une propri&#233;t&#233; de d&#233;pendance
Cet exemple montre comment remplacer des métadonnées de propriété de dépendance par défaut héritées d'une classe en appelant la méthode <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> et en fournissant des métadonnées de type.  
  
## Exemple  
 En définissant ses <xref:System.Windows.PropertyMetadata>, une classe peut définir les comportements de la [propriété de dépendance](GTMT), tels que sa valeur par défaut et ses rappels de système de propriétés.  Un grand nombre de classes de propriété de dépendance disposent de métadonnées par défaut définies dans le cadre de leur processus d'inscription.  Cela inclut les propriétés de dépendance qui font partie de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].  Une classe qui hérite de la propriété de dépendance via son héritage de classe peut remplacer les métadonnées d'origine pour que les caractéristiques de la propriété qui peut être altérée à travers des métadonnées réponde aux conditions de sous\-classe.  
  
 Le remplacement des métadonnées dans une propriété de dépendance doit être effectué avant que la propriété soit placée pour être utilisée par le système de propriétés \(cela correspond au moment où des instances spécifiques des objets qui inscrivent la propriété sont instanciées\).  Les appels à <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> doivent être effectués dans les constructeurs statiques du type qui correspond lui\-même au paramètre `forType` de <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.  Si vous essayez de modifier les métadonnées lorsque les instances du type propriétaire existent , vous ne levez pas d'exception, mais vous générez des comportements incohérents dans le système de propriétés.  En outre, les métadonnées peuvent être remplacées une seule fois par type.  Toute nouvelle tentative de remplacement des métadonnées dans le même type lève une exception.  
  
 Dans l'exemple suivant, la classe personnalisée `MyAdvancedStateControl` remplace les métadonnées fournies pour `StateProperty` par `MyAdvancedStateControl` par de nouvelles métadonnées de propriété.  Par exemple, la valeur par défaut de la `StateProperty` est maintenant `true` lorsque la propriété est interrogée dans une nouvelle instance `MyAdvancedStateControl` construite.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## Voir aussi  
 <xref:System.Windows.DependencyProperty>   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)