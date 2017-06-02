---
title: "Comment&#160;: enregistrer une propri&#233;t&#233; jointe | Microsoft Docs"
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
  - "propriétés jointes, inscrire"
  - "inscrire des propriétés jointes"
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: enregistrer une propri&#233;t&#233; jointe
Cet exemple indique comment inscrire une [propriété jointe](GTMT) et fournir des accesseurs publics pour utiliser la propriété en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et dans le code.  Les propriétés jointes sont un concept de syntaxe défini par le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  La plupart des propriétés jointes pour les types [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont également implémentées comme [propriétés de dépendance](GTMT).  Vous pouvez utiliser [des propriétés de dépendance](GTMT) dans tous les types <xref:System.Windows.DependencyObject>.  
  
## Exemple  
 L'exemple suivant montre comment inscrire une propriété jointe sous la forme d'une propriété de dépendance en utilisant la méthode <xref:System.Windows.DependencyProperty.RegisterAttached%2A>.  La classe de fournisseur peut fournir les métadonnées par défaut de la propriété applicable lorsque la propriété est utilisée dans une autre classe si la classe ne remplace pas les métadonnées.  Dans cet exemple, la valeur par défaut de la propriété `IsBubbleSource` est `false`.  
  
 La classe de fournisseur d'une propriété jointe \(même si elle n'est pas inscrite comme propriété de dépendance\) doit fournir des accesseurs get et set statiques qui respectent la convention d'attribution de noms `Set`*\[NomPropriétéJointe\]* et `Get`*\[NomPropriétéJointe\]*. Ces accesseurs sont nécessaires pour que le lecteur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] actif puisse reconnaître la propriété sous la forme d'un attribut en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et résoudre les types appropriés.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## Voir aussi  
 <xref:System.Windows.DependencyProperty>   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)