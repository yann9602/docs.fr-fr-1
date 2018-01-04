---
title: x:Null, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- Null
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b10d759a4f79eabe973a0fcd60736428e46f659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xnull-markup-extension"></a>x:Null, extension de balisage
Spécifie `null` en tant que valeur d’un membre XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Notes  
 Le mot clé pour une référence null dans [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] et [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] a la valeur null. Le [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] mot clé pour une référence null est `Nothing`, mais vous utilisez toujours `{x:Null}` comme utilisation de XAML quel que soit le langage de code-behind associer avec le code XAML.  
  
 Le `x:Null` extension de balisage ne dispose pas de propriétés définissables.  
  
 L’utilisation d’une valeur null est souvent associée à l’exposition des membres XAML d’un type CLR <xref:System.Nullable%601> valeur.  
  
 Le `x:Null` extension de balisage, comme toutes les extensions de balisage XAML, utilise les accolades (`{,}`) pour la gestion des valeurs d’attribut soient autre chose que des littéraux ou des références de gestionnaire d’événements de séquence d’échappement. La syntaxe d’attribut est la syntaxe la plus fréquemment utilisée avec cette extension de balisage. Syntaxe d’élément objet `<x:Null />` est techniquement possible, mais est rarement utilisée, car le `x:Null` extension de balisage n’a pas les paramètres positionnels ou les arguments de construction.  
  
 Pour plus d’informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Dans les Services XAML .NET Framework, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Markup.NullExtension> classe.  
  
## <a name="wpf-usage-notes"></a>Notes d’utilisation WPF  
 Notez que `null` n’est pas nécessairement la valeur initiale non définie pour une propriété de dépendance de type référence. La valeur par défaut initiale peut varier pour chaque propriété de dépendance et peut être basée sur les métadonnées spécifiques à la propriété. De nombreuses propriétés de dépendance n’acceptent pas `null` en tant que valeur, par le biais de balisage ou de code en raison de leurs implémentations de rappel de validation. Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [Vue d’ensemble du langage XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
