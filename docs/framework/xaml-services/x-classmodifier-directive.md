---
title: "x:ClassModifier Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xClassModifier"
  - "x:ClassModifier"
  - "ClassModifier"
helpviewer_keywords: 
  - "XAML [XAML Services], x:ClassModifier attribute"
  - "x:ClassModifier attribute [XAML Services]"
  - "ClassModifier attribute in XAML [XAML Services]"
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 21
---
# x:ClassModifier Directive
Modifie le comportement de compilation XAML lorsque `x:Class` est également fourni.  Plus précisément, au lieu de créer une `class` partielle qui possède un niveau d'accès `Public` \(valeur par défaut\), la `x:Class` fournie est créée avec un niveau d'accès `NotPublic`.  Cela affecte le niveau d'accès de la classe dans les assemblys générés.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|*NotPublic*|La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes?displayProperty=fullName> et non <xref:System.Reflection.TypeAttributes?displayProperty=fullName> varie selon le langage de programmation code\-behind utilisé.  Consultez la section Notes.|  
  
## Dépendances  
 [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) doit également être fourni dans le même élément, et cet élément doit être l'élément racine dans une page.  Pour plus d'informations, consultez [\[MS\-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## Notes  
 La valeur de `x:ClassModifier` dans l'utilisation des services XAML .NET Framework varie en fonction du langage de programmation.  La chaîne à utiliser dépend de l'implémentation par chaque langage de son <xref:System.CodeDom.Compiler.CodeDomProvider> et des convertisseurs de type qu'il retourne pour définir les significations de <xref:System.Reflection.TypeAttributes?displayProperty=fullName> et <xref:System.Reflection.TypeAttributes?displayProperty=fullName>, et varie également selon que ce langage respecte la casse ou pas.  
  
-   Pour [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est `internal`.  
  
-   Pour [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est `Friend`.  
  
-   Pour [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], il n'existe aucune cible qui prenne en charge la compilation XAML ; par conséquent la valeur à passer n'est pas spécifiée.  
  
 Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes?displayProperty=fullName> \(`public` en [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Public` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]\); toutefois, <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est rarement spécifié car <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est déjà le comportement par défaut.  
  
 D'autres valeurs avec des restrictions du niveau d'accès du code utilisateur équivalentes, par exemple `private` en [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], ne sont pas pertinentes pour `x:ClassModifier`, parce que les références de classe imbriquées ne sont pas prises en charge dans XAML et par conséquent, le modificateur <xref:System.Reflection.TypeAttributes?displayProperty=fullName> a le même effet.  
  
## Notes de sécurité  
 Le niveau d'accès comme déclaré dans `x:ClassModifier` est soumis encore à interprétation par les infrastructures particulières et leurs fonctions.  WPF inclut des fonctions pour charger et instancier des types où `x:ClassModifier` est `internal`, si cette classe est référencée par une ressource WPF via une référence URI à en\-tête pack.  En raison de ce cas et peut\-être d'autres cas similaires implémentés par d'autres infrastructures, ne comptez pas exclusivement sur `x:ClassModifier` pour bloquer toutes les tentatives possibles d'instanciation.  
  
## Voir aussi  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [Code\-behind et XAML dans WPF](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [x:FieldModifier Directive](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)   
 [Sécurité \(WPF\)](../../../ocs/framework/wpf/security-wpf.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)