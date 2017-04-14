---
title: "xml:space Handling in XAML | Microsoft Docs"
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
  - "XAML [XAML Services], xml:space attribute"
  - "XAML [XAML Services], whitespace processing"
  - "xml:space attribute [XAML Services]"
  - "whitespace processing [XAML Services]"
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: 15
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 15
---
# xml:space Handling in XAML
L'attribut `xml:space` est un attribut XML qui déclare le comportement de traitement des espaces blancs significatif dans un élément objet.  Ce comportement convient à tout le contenu \(texte interne\) de l'élément dans lequel `xml:space` est déclaré et s'étend également aux éléments enfants.  
  
## Utilisation d'attributs XAML  
  
```  
<object xml:space="preserve" />  
```  
  
 \- ou \-  
  
```  
<object xml:space="default" />  
```  
  
## Notes  
 La définition de l'attribut `xml:space` dans XAML, avec ses deux valeurs possibles, est dérivée de `xml:space`, tel que défini en tant qu'« attribut spécial » par les spécifications W3C pour XML.  
  
 La valeur par défaut de l'attribut `xml:space` est la valeur littérale `"default"`.  Pour la valeur `"default"`, ou si `xml:space` n'est pas du tout indiqué, le comportement d'analyse des espaces blancs significatifs sera la gestion par défaut, comme défini dans [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Pour conserver l'espace blancs dans le contenu d'élément objet, spécifiez `xml:space="preserve"` sur cet élément objet.  
  
 La portée des effets et de la valeur de l'attribut `xml:space` est limitée aux éléments enfants dans la plupart des interprétations.  
  
 Pour une explication complète du traitement des espaces blancs dans XAML, consultez [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## Voir aussi  
 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)