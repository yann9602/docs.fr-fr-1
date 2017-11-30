---
title: x:Class, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 1828ef3614cc1f3a81d8aeff62c15ed5accfe380
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xclass-directive"></a>x:Class, directive
Configure la compilation du balisage XAML pour joindre des classes partielles entre le balisage et code-behind. La classe partielle du code est définie dans un fichier de code séparé dans un [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] langage, tandis que la classe partielle du balisage est créée par la génération de code lors de la compilation du code XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|Facultatif. Spécifie un [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] espace de noms qui contient la classe partielle identifiée par `classname`. Si `namespace` est spécifié, un point (.) sépare `namespace` et `classname`. Consultez la section Notes.|  
|`classname`|Obligatoire. Spécifie le [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] nom de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML.|  
  
## <a name="dependencies"></a>Dépendances  
 `x:Class`peut uniquement être spécifié sur l’élément racine d’une production XAML. `x:Class`n’est pas valide sur n’importe quel objet qui a un parent dans la production XAML. Pour plus d’informations, consultez [ \[MS-XAML\] Section 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Remarques  
 Le `namespace` valeur peut contenir des points supplémentaires pour organiser des espaces de noms connexes en hiérarchies de noms, qui est une technique courante en programmation .NET Framework. Seul le dernier point dans une chaîne de `x:Class` valeurs est interprété pour séparer `namespace` et `classname.` la classe qui est utilisée en tant que `x:Class` ne peut pas être une classe imbriquée. Les classes imbriquées ne sont pas autorisés, car la détermination de la signification de points pour `x:Class` chaînes est ambiguë si les classes imbriquées sont autorisées.  
  
 Existant qui utilisent les modèles de programmation `x:Class`, `x:Class` est facultatif dans le sens où il est entièrement valide d’avoir une page XAML qui ne possède aucun code-behind. Toutefois, cette fonctionnalité interagit avec les actions de génération comme étant implémentées par les infrastructures qui utilisent XAML. `x:Class`fonctionnalité est également influencée par les rôles que différentes classifications de contenu XAML dans un modèle d’application et les actions de génération, qui correspond. Si votre code XAML déclare l’attribut de la gestion des événements, les valeurs ou instancie des éléments personnalisés où les classes définies sont dans la classe code-behind, vous devez fournir le `x:Class` directive référence (ou [x : Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) à la classe appropriée pour le code-behind.  
  
 La valeur de la `x:Class` la directive doit être une chaîne qui spécifie le nom qualifié complet d’une classe mais sans informations d’assembly (équivalent à la <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Pour les applications simples, vous pouvez omettre les informations d’espace de noms CLR si le code-behind est également structuré de cette manière (code de définition commence au niveau de la classe).  
  
 Le fichier code-behind d’une définition de page ou d’une application doit figurer dans un fichier de code qui est inclus dans le cadre du projet qui produit une application compilée et implique la compilation du balisage. Vous devez suivre les règles de noms pour les classes CLR. Pour plus d’informations, consultez [les règles de conception de Framework](../../../docs/standard/design-guidelines/index.md). Par défaut, la classe code-behind doit être `public`; Toutefois, vous pouvez définir un niveau d’accès différent à l’aide de la [x : ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
 Cette interprétation de le `x:Class` attribut s’applique uniquement à une implémentation XAML basée sur le CLR, en particulier pour les Services XAML .NET Framework. D’autres implémentations XAML qui ne sont pas basées sur CLR et qui n’utilisent pas les Services XAML .NET Framework peuvent utiliser une formule de résolution différente pour la connexion au balisage XAML et le code au moment de l’exécution de la sauvegarde. Pour plus d’informations sur les interprétations plus générales de `x:Class`, consultez [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Un certain niveau de l’architecture, la signification de `x:Class` n’est pas définie dans les Services XAML .NET Framework. Il s’agit des Services XAML .NET Framework ne spécifie pas le modèle de programmation par XAML balisage et le code de stockage sont connectés. Autres utilisations de la `x:Class` directive peut être implémentée par les infrastructures spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML et code-behind basé sur CLR. Chacune de ces infrastructures peut avoir ses propres actions de génération qui activent une partie du comportement ou des composants spécifiques qui doivent être inclus dans l’environnement de génération. Dans une infrastructure, les actions de génération peuvent également varier selon le langage CLR spécifique qui est utilisé pour le code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x : Class dans le modèle de programmation WPF  
 Dans les applications WPF et le modèle d’application WPF, `x:Class` peuvent être déclarés en tant qu’attribut pour tout élément qui est la racine d’un fichier XAML et est compilé (où le code XAML est inclus dans un projet d’application WPF avec `Page` action de génération), ou pour le < C4 > <xref:System.Windows.Application>  racine dans la définition d’application d’une application WPF compilée. Déclaration `x:Class` sur un élément autre qu’une racine de la page ou de la racine de l’application, ou un fichier XAML WPF qui n’est pas compilé, provoque une erreur de compilation sous le [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] et [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] compilateur XAML WPF. Pour plus d’informations sur les autres aspects de `x:Class` la gestion dans WPF, consultez [Code-Behind et XAML dans WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x : Class pour Windows Workflow Foundation  
 Pour Windows Workflow Foundation, `x:Class` nomme la classe d’une activité personnalisée entièrement composée en XAML, ou nomme la classe partielle de la page XAML pour un concepteur d’activités avec code-behind.  
  
## <a name="silverlight-usage-notes"></a>Notes d’utilisation de Silverlight  
 `x:Class`pour Silverlight est documenté séparément. Pour plus d’informations, consultez [XAML Namespace (x :)) Fonctionnalités de langage (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Voir aussi  
 [x:Subclass, directive](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [XAML et classes personnalisées pour WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [x:ClassModifier, directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [Types migrés de WPF vers System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
