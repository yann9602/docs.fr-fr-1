---
title: x:Uid, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 4d49e9630b481b2daf103feabd225dd5ef0c8ca2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xuid-directive"></a>x:Uid, directive
Fournit un identificateur unique pour les éléments de balisage. Dans de nombreux scénarios, cet identificateur unique est utilisé par des outils et processus de localisation XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`identifier`|Créée manuellement ou chaîne générée automatiquement qui doit être unique dans un fichier lorsqu’il est interprété par un `x:Uid` consommateur.|  
  
## <a name="remarks"></a>Remarques  
 Dans [MS-XAML] `x:Uid` est défini comme une directive. Pour plus d’informations, consultez [ \[MS-XAML\] Section 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid`est différent de `x:Name` à la fois en raison du scénario de localisation XAML déclaré et afin que les identificateurs qui sont utilisés pour la localisation n’ont aucune dépendance sur les conséquences de modèle de programmation de `x:Name`. En outre, `x:Name` est régie par la portée de nom XAML ; Toutefois, `x:Uid` n’est pas régi par un concept de langage défini XAML de mise en œuvre de l’unicité. Les processeurs XAML au sens large (processeurs qui ne font pas partie du processus de localisation) ne sont pas prévus pour garantir l’unicité de `x:Uid` valeurs. Cette responsabilité revient conceptuellement à l’initiateur des valeurs. L’attente d’unicité de `x:Uid` des valeurs dans une source XAML unique est justifiée pour les consommateurs des valeurs, telles que le processus d’internationalisation dédié ou d’outils. Le modèle d’unicité typique est que `x:Uid` sont uniques au sein d’un fichier XML qui représente le XAML.  
  
 Les outils qui ont une connaissance significative d’un schéma XAML particulier peuvent choisir d’appliquer `x:Uid` uniquement pour les chaînes localisables true, au lieu de tous les cas où une valeur de chaîne de texte est rencontrée dans la balise.  
  
 Frameworks peuvent spécifier une propriété particulière dans leur modèle d’objet comme étant un alias pour `x:Uid` en appliquant l’attribut <xref:System.Windows.Markup.UidPropertyAttribute> pour le type de définition. Si une infrastructure spécifie une propriété particulière, il n’est pas possible de spécifier à la fois `x:Uid` et le membre d’un alias sur le même objet. Si les deux `x:Uid` et le membre d’un alias sont spécifiés, l’API des Services XAML .NET Framework lève généralement <xref:System.Xaml.XamlDuplicateMemberException> pour ce cas.  
  
## <a name="wpf-usage-notes"></a>Notes d’utilisation WPF  
 Pour plus d’informations sur le rôle de `x:Uid` dans le processus de localisation WPF et dans la forme BAML du XAML, consultez [globalisation pour WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) ou<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [Globalisation pour WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
