---
title: "x:Class Directive | Microsoft Docs"
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
  - "x:Class"
  - "xClass"
  - "Class"
helpviewer_keywords: 
  - "Class attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:Class attribute"
  - "x:Class attribute [XAML Services]"
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 26
---
# x:Class Directive
Configure la compilation de balisage XAML pour joindre des classes partielles entre la balise et le code\-behind.  La classe partielle du code est définie dans un fichier de code distinct en langage [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)], tandis que la classe partielle du balisage est créée par la génération de code lors de la compilation XAML.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|Facultatif.  Spécifie un espace de noms [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] qui contient la classe partielle identifiée par `classname`.  Si `namespace` est spécifié, un point \(.\) sépare `namespace` et `classname`.  Consultez la section Notes.|  
|`classname`|Obligatoire.  Spécifie le nom [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] de la classe partielle qui connecte le XAML chargé et votre code\-behind pour ce XAML.|  
  
## Dépendances  
 `x:Class` peut être spécifié uniquement à l'élément racine d'une production XAML.  `x:Class` n'est pas valide sur tout objet ayant un parent dans la production XAML.  Pour plus d'informations, consultez [\[MS\-XAML\] Section 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## Notes  
 La valeur `namespace` peut contenir des points supplémentaires pour organiser des espaces de noms connexes en hiérarchies de noms, ce qui est une technique courante en programmation .NET Framework.  Seul le dernier point d'une chaîne de valeurs `x:Class` est interprété pour séparer `namespace` et `classname.`  La classe qui est utilisée comme `x:Class` ne peut pas être une classe imbriquée.  Les classes imbriquées sont rejetées parce que la détermination des significations de points pour les chaînes `x:Class` est ambiguë si les classes imbriquées sont autorisées.  
  
 Dans les modèles de programmation existants qui utilisent `x:Class`, `x:Class` est facultatif dans le sens où il est entièrement légal d'avoir une page XAML sans code\-behind.  Toutefois, cette capacité de base interagit avec les actions de génération telles qu'elles sont implémentées par les infrastructures qui utilisent XAML.  La capacité de `x:Class` est également influencée par les rôles de différentes classifications de contenu XAML dans le modèle d'application d'une infrastructure et dans les actions de génération correspondantes.  Si votre XAML déclare des valeurs d'attribut de gestion des événements, ou instancie des éléments personnalisés où les classes définies sont dans la classe code\-behind, la fourniture de la référence de directive `x:Class` \(ou [x:Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)\) à la classe appropriée pour le code\-behind est finalement requise.  
  
 La valeur de la directive `x:Class` doit être une chaîne qui spécifie le nom qualifié complet d'une classe mais sans informations d'assembly \(équivalent à <xref:System.Type.FullName%2A?displayProperty=fullName>\).  Pour les applications simples, vous pouvez omettre les informations sur les espaces de noms CLR tant que le code\-behind est également structuré de cette manière \(la définition de code démarre au niveau de la classe\).  
  
 Le fichier code\-behind d'une définition de page ou d'application doit se trouver dans un fichier de code inclus dans le projet qui produit une application compilée ou comprend une compilation de balisage.  Vous devez suivre les règles de nom des classes CLR.  Pour plus d'informations, consultez [Instructions de conception d’infrastructure](../../../ml/index.xml).  Par défaut, la classe code\-behind doit être `public` ; toutefois, vous pouvez la définir à un niveau d'accès différent à l'aide de [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
 Cette interprétation de l'attribut `x:Class` s'applique uniquement à une implémentation XAML basée sur CLR, en particulier aux services XAML .NET Framework.  D'autres implémentations XAML qui ne sont pas basées sur CLR et n'utilisent pas les services XAML .NET Framework, peuvent utiliser une formule de résolution différente pour la connexion au balisage XAML et la sauvegarde du code runtime.  Pour plus d'informations sur les interprétations plus générales de `x:Class`, consultez [\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 À un certain niveau d'architecture, la signification conceptuelle de `x:Class` est indéfinie dans les services XAML .NET Framework.  Cela est dû au fait que les services XAML .NET Framework ne spécifient pas l'intégralité du modèle de programmation par lequel le balisage XAML et le code de stockage sont connectés.  Utilisations supplémentaires de directive `x:Class` peuvent être implémentés par des frameworks spécifiques qui utilisent des modèles de programmation ou des modèles d'application pour définir comment connecter le balisage XAML et le code\-behind basé sur CLR.  Chacune de ces infrastructures peut avoir ses propres actions de génération qui activent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l'environnement de génération.  Dans une infrastructure, les actions de génération peuvent également varier selon le langage CLR spécifique utilisé pour le code\-behind.  
  
## x:Class dans le modèle de programmation WPF  
 Dans les applications WPF et le modèle d'application WPF, `x:Class` peut être déclaré en tant qu'attribut pour tout élément racine d'un fichier XAML et est compilé \(le XAML est alors inclus dans un projet d'application WPF avec l'action de génération `Page`\), ou pour la racine <xref:System.Windows.Application> de la définition d'application d'une application WPF compilée.  La déclaration de `x:Class` sur un élément autre qu'une racine ou une racine de l'application de la page, ou dans un fichier XAML WPF qui n'est pas compilé, ne provoque pas d'erreur de compilation dans le compilateur [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] et [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] XAML WPF.  Pour plus d'informations sur d'autres aspects de la gestion de `x:Class` dans WPF, consultez [Code\-behind et XAML dans WPF](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## x:Class pour Windows Workflow Foundation  
 Pour Windows Workflow Foundation, `x:Class` nomme la classe d'une activité personnalisée composée entièrement en XAML, ou nomme la classe partielle de la page XAML pour un concepteur d'activités avec code\-behind.  
  
## Notes d'utilisation de Silverlight  
 `x:Class` pour Silverlight est documenté séparément.  Pour plus d'informations, consultez [Fonctionnalités de langage d'espace de noms XAML \(x:\) \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## Voir aussi  
 [x:Subclass Directive](../../../docs/framework/xaml-services/x-subclass-directive.md)   
 [XAML et classes personnalisées pour WPF](../../../ocs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)