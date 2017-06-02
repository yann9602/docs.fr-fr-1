---
title: "S&#233;curit&#233; de propri&#233;t&#233; de d&#233;pendance | Microsoft Docs"
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
  - "propriétés de dépendance, access"
  - "propriétés de dépendance, sécurité"
  - "sécurité, propriétés de dépendance"
  - "sécurité, wrappers"
  - "validation, propriétés de dépendance"
  - "wrappers, access"
  - "wrappers, sécurité"
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# S&#233;curit&#233; de propri&#233;t&#233; de d&#233;pendance
Les propriétés de dépendance doivent en général être considérées comme des propriétés publiques.  La nature du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] empêche de définir des garanties de sécurité à propos d'une valeur de propriété de dépendance.  
  
   
  
<a name="AccessSecurity"></a>   
## Accès et sécurité des wrappers et des propriétés de dépendance  
 En général, les propriétés de dépendance sont implémentées avec les propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] « wrapper » qui simplifient l'obtention ou la définition de la propriété à partir d'une instance.  Cependant, les wrappers ne sont que des méthodes pratiques pour implémenter les appels statiques <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> sous\-jacents utilisés lors de l'interaction avec les propriétés de dépendance.  D'un autre point de vue, les propriétés sont exposées en tant que propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] qui sont stockées par une propriété de dépendance et non par un champ privé.  Les mécanismes de sécurité appliqués aux wrappers ne placent pas en parallèle le comportement du système de propriétés et l'accès de la propriété de dépendance sous\-jacente.  Le fait de placer une demande de sécurité sur le wrapper empêchera seulement l'utilisation de la méthode pratique mais n'empêchera pas les appels à <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>.  De même, le fait de placer un niveau d'accès protégé ou privé sur les wrappers n'offre pas de sécurité efficace.  
  
 Si vous écrivez vos propres propriétés de dépendance, vous devez déclarer les wrappers et le champ d'identificateur <xref:System.Windows.DependencyProperty> comme membres publics, afin que les appelants n'obtiennent pas d'informations trompeuses sur le niveau d'accès réel de cette propriété \(car son magasin est implémenté en tant que propriété de dépendance\).  
  
 Pour une propriété de dépendance personnalisée, vous pouvez enregistrer votre propriété comme propriété de dépendance en lecture seule. Vous empêchez ainsi efficacement qu'une propriété définie par une personne ne contiennent pas de référence au <xref:System.Windows.DependencyPropertyKey> pour cette propriété.  Pour plus d'informations, consultez [Propriétés de dépendance en lecture seule](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Vous pouvez éventuellement déclarer comme privé un champ d'identificateur <xref:System.Windows.DependencyProperty>, par exemple pour réduire l'espace de noms immédiatement exposé d'une classe personnalisée. Cependant, une telle propriété ne doit pas être considérée comme « privée » dans le même sens que les définitions de langage [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] définissent ce niveau d'accès. Les raisons sont décrites dans la section suivante.  
  
<a name="PropertySystemExposure"></a>   
## Exposition du système de propriétés pour les propriétés de dépendance  
 Il n'est généralement pas utile, et même potentiellement trompeur, de déclarer un niveau d'accès autre que public pour une <xref:System.Windows.DependencyProperty>.  Ce paramètre de niveau d'accès empêche seulement à une personne d'obtenir une référence à l'instance auprès de la classe déclarant.  Toutefois, plusieurs aspects du système de propriétés retourneront une <xref:System.Windows.DependencyProperty> comme moyen d'identifier une propriété telle qu'elle existe sur une instance d'une classe ou d'une classe dérivée. Cet identificateur peut être utilisé dans un appel <xref:System.Windows.DependencyObject.SetValue%2A> même si l'identificateur statique d'origine est déclaré comme non public.  De même, les méthodes virtuelles <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> reçoivent des informations de toute propriété de dépendance existante dont la valeur a changé.  En outre, la méthode <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> retourne des identificateurs pour toute propriété sur des instances avec une valeur localement définie.  
  
### Validation et sécurité  
 Le fait d'appliquer une demande à un <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> et d'attendre l'échec de validation sur l'échec d'une demande pour empêcher la définition d'une propriété n'est pas un mécanisme de sécurité adéquat.  L'invalidation de la valeur définie appliquée via <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> pourrait également être supprimée par des appelants malveillants, si ces derniers opèrent dans le domaine d'application.  
  
## Voir aussi  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)