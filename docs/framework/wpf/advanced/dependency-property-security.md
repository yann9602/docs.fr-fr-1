---
title: "Sécurité de propriété de dépendance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd6f9d7025de9f5deb836d48a8ce9c7134973d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-property-security"></a>Sécurité de propriété de dépendance
Les propriétés de dépendance doivent généralement être considérées comme des propriétés publiques. La nature du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] empêche de pouvoir garantir la sécurité d’une valeur de propriété de dépendance.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Accès et sécurité des wrappers et des propriétés de dépendance  
 En règle générale, les propriétés de dépendance sont implémentées avec des propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] « wrappers » qui simplifient l’obtention ou la définition de la propriété à partir d’une instance. Mais les wrappers sont des méthodes pratiques simplement qu’implémentent sous-jacent <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> appels statiques qui sont utilisés lors de l’interaction avec les propriétés de dépendance. Pris d’un autre point de vue, les propriétés sont exposées en tant que propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] stockées par une propriété de dépendance plutôt que par un champ privé. Les mécanismes de sécurité appliqués aux wrappers ne sont pas identiques au comportement du système de propriétés et au niveau d’accès de la propriété de dépendance sous-jacente. Placer une demande de sécurité sur le wrapper empêchera seulement l’utilisation de la méthode pratique mais n’empêchera pas les appels à <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>. De même, placer un niveau d’accès privé ou protégé sur les wrappers ne procure pas une sécurité efficace.  
  
 Si vous écrivez vos propres propriétés de dépendance, vous devez déclarer les wrappers et <xref:System.Windows.DependencyProperty> identificateur de champ en tant que membres publics, afin que les appelants ne pas obtenir trompeuses plus d’informations sur le niveau d’accès réel de cette propriété (en raison de son magasin en cours implémenté comme une propriété de dépendance).  
  
 Pour une propriété de dépendance personnalisée, vous pouvez enregistrer votre propriété comme une propriété de dépendance en lecture seule, et il fournit un moyen efficace d’empêcher une propriété définie par toute personne qui ne possède pas une référence à la <xref:System.Windows.DependencyPropertyKey> pour cette propriété. Pour plus d’informations, consultez [Propriétés de dépendance en lecture seule](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Déclaration d’un <xref:System.Windows.DependencyProperty> identificateur champ privé n’est pas interdit et il peut éventuellement être utilisé afin de réduire l’espace de noms immédiatement exposé d’une classe personnalisée, mais une telle propriété n’est pas « private » dans le même sens que le [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] définitions de la langue définissent ce niveau d’accès, pour les raisons détaillées dans la section suivante.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Exposition des propriétés de dépendance par le système de propriétés  
 Il est généralement pas utile, et il est potentiellement trompeur, de déclarer un <xref:System.Windows.DependencyProperty> niveau d’accès autre que public. Ce paramètre de niveau d’accès empêche seulement une personne d’obtenir une référence à l’instance à partir de la classe de déclaration. Mais il existe plusieurs aspects du système de propriétés qui retournera un <xref:System.Windows.DependencyProperty> en tant que moyen d’identifier une propriété particulière, il existe sur une instance d’une classe ou une instance de la classe dérivée, cet identificateur est encore utilisable dans un <xref:System.Windows.DependencyObject.SetValue%2A> appeler même Si l’identificateur statique d’origine est déclaré comme non public. En outre, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> méthodes virtuelles reçoivent des informations de n’importe quelle propriété de dépendance existant qui a changé de valeur. En outre, le <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> méthode retourne des identificateurs pour n’importe quelle propriété sur des instances avec définie localement valeur.  
  
### <a name="validation-and-security"></a>Validation et sécurité  
 Application d’une demande à un <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> et attendu de l’échec de validation sur l’échec d’une demande pour empêcher une propriété d’être définie n’est pas un mécanisme de sécurité adéquat. Invalidation de la valeur définie appliquée via <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> pourrait également être supprimée par des appelants malveillants, si ces derniers opèrent dans le domaine d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
