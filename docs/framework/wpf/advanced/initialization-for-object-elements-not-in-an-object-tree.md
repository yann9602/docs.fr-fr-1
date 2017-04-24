---
title: "Initialisation d&#39;&#233;l&#233;ments objet ne figurant pas dans une arborescence d&#39;objets | Microsoft Docs"
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
  - "éléments, initialiser"
  - "initialiser des éléments"
  - "arborescence logique"
  - "arborescence d'éléments visuels"
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Initialisation d&#39;&#233;l&#233;ments objet ne figurant pas dans une arborescence d&#39;objets
Certains aspects de l'initialisation de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont différés à des processus qui reposent généralement sur la connexion de cet élément à l'[arborescence logique](GTMT) ou à l'[arborescence visuelle](GTMT).  Cette rubrique décrit les étapes qui peuvent s'avérer nécessaires pour initialiser un élément qui n'est connecté à aucune de ces arborescences.  
  
   
  
## Éléments et arborescence logique  
 Lorsque vous créez une instance d'une classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dans le code, gardez à l'esprit que plusieurs aspects de l'initialisation d'un objet pour une classe [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne sont pas intégrés, à dessein, au code exécuté lors de l'appel du constructeur de classe.  Dans le cas d'une classe de contrôle en particulier, la plus grande partie de la représentation visuelle de ce contrôle n'est pas définie par le constructeur,  mais par le modèle du contrôle.  Le modèle peut provenir de diverses sources, mais est le plus souvent obtenu à partir de styles de thème.  La liaison des modèles est en fait tardive ; le modèle nécessaire n'est pas joint au contrôle tant que celui\-ci n'est pas prêt pour la disposition.  Et le contrôle n'est prêt pour la disposition que lorsqu'il est joint à une arborescence logique connectée à une surface de rendu à la racine.  C'est cet élément de niveau racine qui initialise le rendu de tous ses éléments enfants définis dans l'arborescence logique.  
  
 L'arborescence visuelle prend également part à ce processus.  Les éléments intégrés à l'arborescence visuelle par le biais des modèles ne sont eux aussi totalement instanciés que lorsqu'ils sont connectés.  
  
 En raison de ce comportement, certaines opérations reposant sur les caractéristiques visuelles complétées d'un élément requièrent des étapes supplémentaires.  C'est le cas notamment si vous tentez d'obtenir les caractéristiques visuelles d'une classe qui a été générée mais pas encore attachée à une arborescence.  Par exemple, si vous voulez appeler <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> sur un <xref:System.Windows.Media.Imaging.RenderTargetBitmap> et que le visuel que vous transmettez est un élément non connecté à une arborescence, cet élément est incomplet d'un point de vue visuel tant que les étapes d'initialisation supplémentaires ne sont pas terminées.  
  
### Utilisation de BeginInit et EndInit pour initialiser l'élément  
 Différentes classes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentent l'interface <xref:System.ComponentModel.ISupportInitialize>.  Les méthodes <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> et <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> de l'interface vous permettent de désigner une région de votre code contenant des étapes d'initialisation \(telles que la définition des valeurs de propriétés affectant le rendu\).  Après avoir appelé <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> dans la séquence, le système de disposition peut traiter l'élément et commencer à rechercher un style implicite.  
  
 Si l'élément dont vous définissez les propriétés est une classe dérivée <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, vous pouvez appeler les versions de classe de <xref:System.Windows.FrameworkElement.BeginInit%2A> et <xref:System.Windows.FrameworkElement.EndInit%2A> au lieu d'effectuer un cast en <xref:System.ComponentModel.ISupportInitialize>.  
  
### Exemple de code  
 L'exemple suivant montre un exemple de code pour une application console qui utilise des [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de rendu et <xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=fullName> d'un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre pour illustrer le positionnement correct de <xref:System.Windows.FrameworkElement.BeginInit%2A> et <xref:System.Windows.FrameworkElement.EndInit%2A> autour d'autres appels d'[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] qui définissent des propriétés affectant le rendu.  
  
 Cet exemple illustre uniquement la fonction principale.  Les fonctions `Rasterize` et `Save` \(non affichées\) sont des fonctions utilitaires qui prennent en charge le traitement d'image et l'E\/S.  
  
 [!code-csharp[InitializeElements#Main](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## Voir aussi  
 [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)