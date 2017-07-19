---
title: "mc:ProcessContent, attribut | Microsoft Docs"
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
  - "mc:ProcessContent (attribut)"
  - "XAML, mc:ProcessContent (attribut)"
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# mc:ProcessContent, attribut
Spécifie les éléments [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dont le contenu devrait encore être traité par les éléments parents pertinents, même si l'élément parent immédiat peut être ignoré par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en raison de la spécification de [mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).  L'attribut `mc:ProcessContent` prend en charge la compatibilité de balise pour le mappage de l'espace de noms personnalisé et pour le versioning [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
## Utilisation d'attributs XAML  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|*ignorablePrefix*|Toute chaîne de préfixes valide, conformément à la spécification XML 1.0.|  
|*ignorableUri*|Tout URI valide pour la désignation d'un espace de noms, conformément à la spécification XML 1.0.|  
|*ThisElementCanBeIgnored*|Élément pouvant être ignoré par les implémentations de processeur [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], si le type sous\-jacent ne peut pas être résolu.|  
|*\[content\]*|*ThisElementCanBeIgnored* est marqué comme pouvant être ignoré.  Si le processeur ignore cet élément, *\[contenu\]* est traité par l'*objet*.|  
  
## Notes  
 Par défaut, un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignore le contenu d'un élément ignoré.  Vous pouvez spécifier un élément spécifique par `mc:ProcessContent`, et un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] continuera à traiter le contenu dans l'élément ignoré.  Cela serait généralement utilisé si le contenu est imbriqué dans plusieurs balises, dont une au moins peut être ignorée et une au moins ne peut pas être ignorée.  
  
 Plusieurs préfixes peuvent être spécifiés dans l'attribut, à l'aide d'un espace de séparation, par exemple : `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 L'espace de noms [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] définit d'autres éléments et attributs qui ne sont pas documentés dans cette zone du [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].  Pour plus d'informations, consultez [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## Voir aussi  
 [mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)