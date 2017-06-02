---
title: "PresentationOptions:Freeze, attribut | Microsoft Docs"
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
  - "éléments Freezable"
  - "Freeze (attribut)"
  - "PresentationOptions (préfixe)"
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# PresentationOptions:Freeze, attribut
Définit l'état <xref:System.Windows.Freezable.IsFrozen%2A> selon `true` sur l'élément <xref:System.Windows.Freezable> contenant.  Le comportement par défaut pour un <xref:System.Windows.Freezable> sans l'attribut `PresentationOptions:Freeze` spécifié est que <xref:System.Windows.Freezable.IsFrozen%2A> est `false` au moment du chargement, et dépendant du comportement <xref:System.Windows.Freezable> général pendant l'exécution.  
  
## Utilisation d'attributs XAML  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Préfixe d'espace de noms XML, qui peut être toute chaîne de préfixe valide conforme à la spécification XML 1.0.  Le préfixe `PresentationOptions` est utilisé à des fins d'identification dans cette documentation.|  
|`freezableElement`|Élément qui instancie toute classe dérivée de <xref:System.Windows.Freezable>.|  
  
## Notes  
 L'attribut `Freeze` est le seul attribut ou élément de programmation défini dans l'espace de noms XML `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`.  L'attribut `Freeze` existe spécifiquement dans cet espace de noms spécial afin qu'il puisse être désigné comme pouvant être ignoré, en utilisant l'[mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) dans le cadre des déclarations d'élément racine.  La raison pour laquelle `Freeze` doit être en mesure de pouvoir être ignoré est parce que toutes les implémentations de processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ne sont pas en mesure de figer un <xref:System.Windows.Freezable> au moment du chargement ; cette fonctionnalité ne faisant pas partie de la spécification [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 La capacité à traiter l'attribut `Freeze` est intégrée spécifiquement au processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui traite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour les applications compilées.  L'attribut n'est pris en charge par aucune classe, et la syntaxe d'attribut n'est pas extensible ou modifiable.  Si vous implémentez votre propre processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez choisir de placer parallèlement le comportement de gel du processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lors du traitement de l'attribut `Freeze` sur les éléments <xref:System.Windows.Freezable> au moment du chargement.  
  
 Toute valeur pour l'attribut `Freeze` autre que `true` \(non sensible à la casse\) génère une erreur au moment du chargement.  \(Spécifier l'attribut `Freeze` comme étant `false` ne constitue pas une erreur, mais comme il s'agit déjà de la valeur par défaut, le fait de spécifier `false` n'accomplit rien\).  
  
## Voir aussi  
 <xref:System.Windows.Freezable>   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [mc:Ignorable, attribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)