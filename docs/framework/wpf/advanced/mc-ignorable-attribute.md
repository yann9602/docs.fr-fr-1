---
title: "mc:Ignorable, attribut | Microsoft Docs"
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
  - "mc (préfixe d'espace de noms XML)"
  - "mc:Ignorable (attribut)"
  - "mc:ProcessContent (attribut)"
  - "XAML, mc:Ignorable (attribut)"
  - "XAML, mc:ProcessContent (attribut)"
  - "XML, mc (préfixe d'espace de noms)"
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# mc:Ignorable, attribut
Spécifie les préfixes de l'espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] rencontrés dans un fichier de balisage qui peuvent être ignorés par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  L'attribut `mc:Ignorable` prend en charge la compatibilité de balisage à la fois pour le mappage de l'espace de noms personnalisé et pour le contrôle de version [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
## Utilisation des attributs XAML \(un seul préfixe\)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## Utilisation des attributs XAML \(deux préfixes\)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|*ignorablePrefix, ignorablePrefix1, etc.*|Toute chaîne de préfixes valide, conformément à la spécification XML 1.0.|  
|*ignorableUri*|Tout URI valide pour la désignation d'un espace de noms, conformément à la spécification XML 1.0.|  
|*ThisElementCanBeIgnored*|Élément pouvant être ignoré par les implémentations de processeur [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], si le type sous\-jacent ne peut pas être résolu.|  
  
## Notes  
 Le préfixe d'espace de noms `mc`[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] est la convention de préfixe recommandée à utiliser lors du mappage de l'espace de noms de compatibilité [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Les éléments ou les attributs dans lesquels la partie préfixe du nom de l'élément est identifiée en tant que `mc:Ignorable` ne déclenchent pas d'erreurs lorsqu'ils sont traités par un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Si cet attribut n'a pas pu être résolu vers un type sous\-jacent ou une construction de programmation, cet élément est ignoré.  Notez toutefois que les éléments ignorés peuvent générer des erreurs d'analyse supplémentaires pour des spécifications d'élément supplémentaires. Ces erreurs sont une des conséquences du fait que cet élément n'est pas traité.  Par exemple, un modèle de contenu d'élément particulier peut exiger exactement un élément enfant, mais si l'élément enfant spécifié était dans un préfixe `mc:Ignorable` et n'a pas pu être résolu vers un type, le processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peut déclencher une erreur.  
  
 `mc:Ignorable` s'applique uniquement aux mappages d'espace de noms à des chaînes d'identification.  `mc:Ignorable` ne s'applique pas aux mappages d'espace de noms dans les assemblys, qui spécifient un espace de noms [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et un assembly \(ou renvoient par défaut le fichier exécutable actuel en tant qu'assembly\).  
  
 Si vous implémentez un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], votre implémentation de processeur ne doit pas déclencher d'erreurs d'analyse ou de traitement sur la résolution de type pour tout élément ou attribut qualifié par un préfixe identifié comme `mc:Ignorable`.  Votre implémentation de processeur peut toutefois continuer à déclencher des exceptions dues à l'impossibilité de charger ou de traiter un élément, tel que l'exemple d'élément à enfant unique présenté un peu plus tôt.  
  
 Par défaut, un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignore le contenu d'un élément ignoré.  Vous pouvez toutefois spécifier un attribut supplémentaire, [mc:ProcessContent, attribut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), afin de demander la poursuite du traitement du contenu d'un élément ignoré par l'élément parent disponible suivant.  
  
 Plusieurs préfixes peuvent être spécifiés dans l'attribut, en utilisant un ou plusieurs caractères d'espace blanc en guise de séparateur. Par exemple : `mc:Ignorable="ignore1 ignore2"`.  
  
 L'espace de noms [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] définit d'autres éléments et attributs qui ne sont pas documentés dans cette zone du [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].  Pour plus d'informations, consultez [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## Voir aussi  
 <xref:System.Windows.Markup.XamlReader>   
 [PresentationOptions:Freeze, attribut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)