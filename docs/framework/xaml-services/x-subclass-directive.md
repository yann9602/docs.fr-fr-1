---
title: x:Subclass, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5c6e91fcecb60dee2577ea62c2313f8b2c7eecbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xsubclass-directive"></a>x:Subclass, directive
Modifie le comportement de compilation du balisage XAML lorsque `x:Class` est également fourni. Au lieu de créer une classe partielle qui est basée sur `x:Class`, fourni `x:Class` est créée comme une classe intermédiaire, et ensuite votre classe dérivée fournie est censée être basée sur `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|Facultatif. Spécifie un espace de noms CLR contenant `classname`. Si `namespace` est spécifié, un point (.) sépare `namespace` et `classname`.|  
|`classname`|Obligatoire. Spécifie le nom CLR de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML. Consultez la section Notes.|  
|`subclassNamespace`|Facultatif. Peut être différent de `namespace` si chaque espace de noms peut résoudre l’autre. Spécifie un espace de noms CLR contenant `subclassName`. Si `subclassName` est spécifié, un point (.) sépare `subclassNamespace` et `subclassName`.|  
|`subclassName`|Obligatoire. Spécifie le nom CLR de la sous-classe.|  
  
## <a name="dependencies"></a>Dépendances  
 [x : Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) doit également être fourni sur le même objet, et cet objet doit être l’élément racine de la production XAML.  
  
## <a name="remarks"></a>Remarques  
 `x:Subclass`l’utilisation est principalement utilisée pour les langages qui ne prennent pas en charge les déclarations de classe partielle.  
  
 La classe utilisée comme le `x:Subclass` ne peut pas être une classe imbriquée, et `x:Subclass` doit faire référence à l’objet racine, comme expliqué dans la section « Dépendances ».  
  
 Dans le cas contraire, la signification conceptuelle de `x:Subclass` n’est pas définie par une implémentation de Services XAML .NET Framework. Il s’agit, car le comportement des Services XAML .NET Framework ne spécifie pas le modèle de programmation général en XAML balisage et le code de stockage sont connectés. Les implémentations de concepts supplémentaires liés à `x:Class` et `x:Subclass` sont effectuées par les infrastructures spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML compilé de balisage et code-behind basé sur CLR. Chacune de ces infrastructures peut avoir ses propres actions de génération qui activent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l’environnement de génération. Dans une infrastructure, les actions de génération peuvent également varier selon le langage CLR spécifique qui est utilisé pour le code-behind.  
  
## <a name="wpf-usage-notes"></a>Notes d’utilisation WPF  
 `x:Subclass`peut être sur une racine de page ou le <xref:System.Windows.Application> racine dans la définition d’application, qui a déjà `x:Class`. Déclaration `x:Subclass` sur tout élément autre qu’une racine de page ou d’une application, ou sa spécification lorsqu’aucun `x:Class` existe, provoque une erreur de compilation.  
  
 Création de classes dérivées qui fonctionnent correctement pour le `x:Subclass` scénario est relativement complexe. Vous devrez peut-être examiner les fichiers intermédiaires (les fichiers .g produits dans le dossier obj de votre projet par la compilation de balisage, avec des noms qui incorporent les noms de fichier .xaml). Ces fichiers intermédiaires peuvent vous aider à déterminer l’origine de certaines constructions de programmation dans les classes partielles jointes dans l’application compilée.  
  
 Gestionnaires d’événements dans la classe dérivée doivent être `internal override` (`Friend Overrides` dans [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) afin de substituer les stubs pour les gestionnaires créés dans la classe intermédiaire au moment de la compilation. Sinon, les implémentations de classe dérivée masqueront l’implémentation de la classe intermédiaire et les gestionnaires de classe intermédiaire ne sont pas appelés.  
  
 Lorsque vous définissez `x:Class` et `x:Subclass`, vous n’avez pas besoin de fournir d’implémentation pour la classe qui est référencée par `x:Class`. Vous devez uniquement afin de lui donner un nom via le `x:Class` attribut afin que le compilateur dispose de quelques conseils pour la classe qu’il crée dans les fichiers intermédiaires (dans ce cas, le compilateur ne sélectionne pas de nom par défaut). Vous pouvez donner le `x:Class` une implémentation de la classe ; Toutefois, cela n’est pas le scénario classique pour l’utilisation `x:Class` et `x:Subclass`.  
  
## <a name="see-also"></a>Voir aussi  
 [x:Class, directive](../../../docs/framework/xaml-services/x-class-directive.md)  
 [XAML et classes personnalisées pour WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
