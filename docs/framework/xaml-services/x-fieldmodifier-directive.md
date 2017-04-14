---
title: "x:FieldModifier Directive | Microsoft Docs"
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
  - "FieldModifier attribute in XAML [XAML Services]"
  - "x:FieldModifier attribute [XAML Services]"
  - "XAML [XAML Services], x:FieldModifier attribute"
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: 15
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 14
---
# x:FieldModifier Directive
Modifie le comportement de compilation XAML, de manière à ce que les champs des références d'objet nommées soient définis avec un accès <xref:System.Reflection.TypeAttributes?displayProperty=fullName> plutôt qu'avec le comportement par défaut <xref:System.Reflection.TypeAttributes?displayProperty=fullName>.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:FieldModifier="Public".../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|*Public*|La chaîne exacte à passer pour spécifier <xref:System.Reflection.TypeAttributes?displayProperty=fullName> et non <xref:System.Reflection.TypeAttributes?displayProperty=fullName> varie selon le langage de programmation code\-behind utilisé.  Consultez la section Notes.|  
  
## Dépendances  
 Si une production XAML utilise `x:FieldModifier` n'importe où, l'élément racine de cette production XAML doit déclarer un [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## Notes  
 `x:FieldModifier` n'est pas pertinent pour déclarer le niveau d'accès général d'une classe ou de ses membres.  Cela s'applique uniquement au comportement de traitement XAML lorsqu'un objet XAML particulier qui fait partie d'une production XAML est traité, et devient un objet qui est potentiellement accessible dans le graphique d'objet d'une application.  Par défaut, la référence de champ pour un tel objet reste privée, ce qui empêche les utilisateurs de contrôles de modifier directement le graphique d'objet.  À la place, les utilisateurs de contrôles doivent plutôt modifier le graphique d'objet à l'aide de modèles standard activés par des modèles de programmation, tels que l'obtention de la racine de disposition, de collections d'éléments enfants, de propriétés publiques dédiées, etc.  
  
 La valeur de l'attribut `x:FieldModifier` varie en fonction du langage de programmation et son objectif peut varier dans certaines infrastructures spécifiques.  La chaîne à utiliser dépend de l'implémentation par chaque langage de son <xref:System.CodeDom.Compiler.CodeDomProvider> et des convertisseurs de type qu'il retourne pour définir les significations de <xref:System.Reflection.TypeAttributes?displayProperty=fullName> et <xref:System.Reflection.TypeAttributes?displayProperty=fullName>, et varie également selon que ce langage respecte la casse ou pas.  
  
-   Pour [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est `public`.  
  
-   Pour [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est `Public`.  
  
-   Pour [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], aucune cible n'existe actuellement pour XAML ; par conséquent, la chaîne à passer est indéfinie.  
  
 Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes?displayProperty=fullName> \(`internal` dans [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` in [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]\), mais spécifiant que <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est inhabituel car `NotPublic` est déjà le comportement par défaut.  
  
 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> est le comportement par défaut car il est rare que le code en dehors de l'assembly qui a compilé le code XAML ait besoin d'accéder à un élément créé par XAML.  L'architecture de sécurité WPF ainsi que le comportement de compilation XAML ne déclarera pas les champs qui stockent des instances d'élément comme publics, à moins que vous ne définissiez spécifiquement `x:FieldModifier` pour autoriser l'accès public.  
  
 `x:FieldModifier` est uniquement pertinent pour les éléments avec un [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md), car ce nom est utilisé pour faire référence au champ lorsqu'il est public.  
  
 Par défaut, la classe partielle de l'élément racine est publique ; toutefois, vous pouvez la rendre non publique à l'aide de [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  L'[x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md) affecte également le niveau d'accès de l'instance de la classe d'élément racine.  Vous pouvez placer `x:Name` et `x:FieldModifier` dans l'élément racine, mais cela permet uniquement de créer une copie du champ public de l'élément racine, le niveau d'accès de la classe d'élément racine réel étant toujours contrôlé par [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## Voir aussi  
 [XAML et classes personnalisées pour WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [Code\-behind et XAML dans WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md)   
 [Génération d'une application WPF \(WPF\)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)