---
title: "ColorConvertedBitmap, extension de balisage | Microsoft Docs"
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
  - "ColorConvertedBitmap (extension de balisage)"
  - "XAML, ColorConvertedBitmap (extension de balisage)"
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# ColorConvertedBitmap, extension de balisage
Cette extension permet de spécifier une source d'image bitmap qui ne comporte pas de profil incorporé.  Les contextes\/profils de couleur sont spécifiés par l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], tout comme [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de l'image source.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de l'image bitmap non profilée.|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la configuration du profil source.|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de la configuration du profil de destination.|  
  
## Notes  
 Cette extension de balisage est conçue pour remplir un jeu connexe de valeurs de propriétés de source d'image, comme <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  `ColorConvertedBitmap` \(ou `ColorConvertedBitmapExtension`\) ne peut pas être utilisé dans la syntaxe de l'élément de propriété, car les valeurs ne peuvent être définies qu'en tant que valeurs dans le constructeur initial, qui correspond à la chaîne qui suit l'identificateur d'extension.  
  
 `ColorConvertedBitmap` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  Toutes les extensions de balisage en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d'attributs. Cette convention indique au convertisseur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que l'extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)