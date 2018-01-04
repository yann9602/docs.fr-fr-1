---
title: PresentationOptions:Freeze, attribut
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb305c69cec7c4e4766153ae64d37b19ab0bccea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze, attribut
Définit le <xref:System.Windows.Freezable.IsFrozen%2A> l’état `true` sur le contenant <xref:System.Windows.Freezable> élément. Comportement par défaut un <xref:System.Windows.Freezable> sans le `PresentationOptions:Freeze` attribut spécifié est que <xref:System.Windows.Freezable.IsFrozen%2A> est `false` au moment du chargement et général en fonction <xref:System.Windows.Freezable> comportement lors de l’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Un préfixe d’espace de noms XML, qui peut être n’importe quelle chaîne de préfixe valide, conformément à la spécification XML 1.0. Le préfixe `PresentationOptions` est utilisé à des fins d’identification dans cette documentation.|  
|`freezableElement`|Un élément qui instancie toute classe dérivée de <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Notes  
 Le `Freeze` attribut est le seul attribut ou élément de programmation défini dans le `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` espace de noms XML. Le `Freeze` attribut existe dans cet espace de noms spécial spécifiquement afin qu’il peut être désigné comme pouvant être ignoré, à l’aide de [mc : attribut Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) dans le cadre des déclarations d’élément racine. La raison qui `Freeze` doit pouvoir être ignoré n’étant donné que tous les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentations de processeur sont en mesure de figer un <xref:System.Windows.Freezable> au moment du chargement ; cette fonctionnalité n’est pas dans le cadre de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spécification.  
  
 La possibilité de traiter la `Freeze` attribut spécifiquement créé dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur traite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour les applications compilées. L’attribut n’est pas pris en charge par n’importe quelle classe, et la syntaxe d’attribut n’est pas extensible ou modifiable. Si vous implémentez votre propre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur, vous pouvez choisir du comportement de gel en parallèle la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur lors du traitement de la `Freeze` de l’attribut <xref:System.Windows.Freezable> éléments au moment du chargement.  
  
 Toute valeur pour le `Freeze` attribut autre que `true` (non sensible à la casse) génère une erreur de temps de chargement. (En spécifiant la `Freeze` sous la forme `false` n’est pas une erreur, mais qui est déjà le paramètre par défaut, par conséquent, pour `false` n’exécute aucune opération).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Freezable>  
 [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
