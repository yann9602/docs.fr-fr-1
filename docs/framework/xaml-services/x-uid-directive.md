---
title: "x:Uid Directive | Microsoft Docs"
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
  - "XAML [XAML Services], localizable content attribute"
  - "XAML [XAML Services], x:Uid attribute"
  - "x:Uid attribute [XAML Services]"
  - "Uid attribute [XAML Services]"
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: 12
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 12
---
# x:Uid Directive
Fournit un identificateur unique pour les éléments de balisage.  Dans de nombreux scénarios, cet identificateur unique est utilisé par les outils et les processus de localisation XAML.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:Uid="identifier"... />  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`identifier`|Une chaîne créée manuellement ou automatiquement qui doit être unique dans un fichier lorsqu'il est interprété par un consommateur de `x:Uid`.|  
  
## Notes  
 Dans \[MS\-XAML\], `x:Uid` est défini comme une directive.  Pour plus d'informations, consultez [\[MS\-XAML\] Section 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid` est différent de `x:Name` à cause du scénario de localisation XAML déclaré et parce que les identificateurs utilisés pour la localisation n'aient pas de dépendances sur les conséquences de modèle de programmation de `x:Name`.  Également, `x:Name` est régi par la portée de noms XAML ; cependant, `x:Uid` n'est pas gouverné par un concept défini de langage XAML de mise en conformité d'unicité.  Les processeurs XAML au sens générique du terme \(processeurs qui ne font pas partie du processus de localisation\), ne sont pas supposés appliquer l'unicité des valeurs `x:Uid`.  Cette responsabilité revient conceptuellement à l'initiateur des valeurs.  L'attente d'unicité de valeurs `x:Uid` dans une source XAML unique est justifiée pour les consommateurs des valeurs, par exemple des processus ou des outils de globalisation dédiés.  Le modèle d'unicité typique signifie que les valeurs `x:Uid` d'un fichier encodé XML représentant du XAML seront uniques.  
  
 Les outils possédant une connaissance significative d'un schéma XAML particulier peuvent choisir d'appliquer uniquement `x:Uid` pour les chaînes localisables true, plutôt que pour tous les cas dans lesquels une valeur de chaîne de texte est rencontrée dans la balise.  
  
 Les Frameworks peuvent spécifier une propriété particulière dans leur modèle objet pour en faire un alias pour `x:Uid` en appliquant l'attribut <xref:System.Windows.Markup.UidPropertyAttribute> au type défini.  Si une infrastructure spécifie une propriété particulière, elle est valide pour spécifier `x:Uid` et le membre ajouté en alias sur le même objet.  Si `x:Uid` et le membre ajouté en alias sont spécifiés, l'API des services XAML .NET Framework lève généralement <xref:System.Xaml.XamlDuplicateMemberException> pour ce cas.  
  
## Remarques sur l'utilisation de WPF  
 Pour plus d'informations sur le rôle de `x:Uid` dans le processus de localisation WPF et dans le formulaire BAML de XAML, consultez [Globalisation pour WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) ou <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## Voir aussi  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>   
 <xref:Microsoft.Build.Tasks.Windows.UidManager>   
 [Globalisation pour WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)