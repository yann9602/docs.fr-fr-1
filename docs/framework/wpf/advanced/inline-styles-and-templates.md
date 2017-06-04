---
title: "Mod&#232;les et styles intralignes | Microsoft Docs"
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
  - "styles intralignes"
  - "modèles inline"
  - "styles, inline"
  - "modèles, inline"
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Mod&#232;les et styles intralignes
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit des objets <xref:System.Windows.Style> et des objets de modèle \(sous\-classes <xref:System.Windows.FrameworkTemplate>\) pour définir l'apparence visuelle d'un élément dans les ressources, afin qu'ils puissent être utilisés à plusieurs reprises.  Pour cette raison, les attributs en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui prennent les types <xref:System.Windows.Style> et <xref:System.Windows.FrameworkTemplate> font presque toujours référence aux styles et modèles existant des ressources plutôt que d'en définir de nouveaux intralignes.  
  
## Limitations des styles et modèles intralignes  
 En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez techniquement définir les propriétés de style et de modèle de l'une des deux manières suivantes.  Vous pouvez utiliser la syntaxe d'attribut pour faire référence à un style défini dans une ressource, par exemple `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.  Ou bien vous pouvez utiliser la syntaxe de l'élément de propriété pour définir un style intraligne, par exemple :  
  
 `<` *object* `>`  
  
 `<` *object* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *object* `.Style>`  
  
 `</` *object* `>`  
  
 L'utilisation d'attribut est beaucoup plus fréquente.  Un style qui est défini intraligne et mais n'est pas paramétré dans les ressources se limite forcément à l'élément contenant et ne peut pas être réutilisé aussi facilement car il n'a aucune clé de ressource.  En général, un style défini par une ressource est plus versatile et utile et est plus conforme au principe de modèle de programmation [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] général, qui consiste à séparer la logique du programme dans le code de la conception dans le balisage.  
  
 Aucune raison ne justifie habituellement de définir un style ou un modèle intraligne, même si vous projetez seulement d'utiliser ce style ou modèle à cet emplacement.  La plupart des éléments qui peuvent prendre un style ou un modèle prennent également en charge une propriété et un modèle de contenu.  Si vous utilisez seulement une arborescence logique créée une fois dans un style ou un modèle, il sera même plus facile de renseigner simplement cette propriété de contenu avec les éléments enfants équivalents dans les balises directes.  Vous ignorerez ainsi les mécanismes de style et de modèle.  
  
 Il est également possible d'utiliser pour les styles et les modèles d'autres syntaxes activées par les extensions de balisage qui renvoient un objet.  Deux extensions associées à des scénarios possibles comprennent [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) et <xref:System.Windows.Data.Binding>.  
  
## Voir aussi  
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)