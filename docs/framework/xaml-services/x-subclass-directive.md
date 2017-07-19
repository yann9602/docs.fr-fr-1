---
title: "x:Subclass Directive | Microsoft Docs"
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
  - "Subclass"
  - "xSubclass"
  - "x:Subclass"
helpviewer_keywords: 
  - "x:Subclass attribute [XAML Services]"
  - "XAML [XAML Services], x:Subclass attribute"
  - "Subclass attribute in XAML [XAML Services]"
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Subclass Directive
Modifie le comportement de compilation du balisage XAML lorsque `x:Class` est également fourni.  Au lieu de créer une classe partielle selon la classe `x:Class`, la `x:Class` fournie est créée comme une classe intermédiaire, ensuite, votre classe dérivée fournie est censée être basée sur `x:Class`.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|Facultatif.  Spécifie un espace de noms CLR qui contient `classname`.  Si `namespace` est spécifié, un point \(.\) sépare `namespace` et `classname`.|  
|`classname`|Obligatoire.  Spécifie le nom CLR de la classe partielle qui connecte le XAML chargé et votre code\-behind pour ce XAML.  Consultez la section Notes.|  
|`subclassNamespace`|Facultatif.  Peut être différent de `namespace` si chaque espace de noms peut résoudre l'autre.  Spécifie un espace de noms CLR qui contient `subclassName`.  Si `subclassName` est spécifié, un point \(.\) sépare `subclassNamespace` et `subclassName`.|  
|`subclassName`|Obligatoire.  Spécifie le nom CLR de la sous\-classe.|  
  
## Dépendances  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) doit également être fourni sur le même objet et cet objet doit être l'élément racine de la production XAML.  
  
## Notes  
 À l'origine, `x:Subclass` est destiné aux langages qui ne prennent pas en charge les déclarations de classes partielles.  
  
 La classe utilisée comme `x:Subclass` ne peut pas être une classe imbriquée, et `x:Subclass` doit faire référence à l'objet racine, comme expliqué dans la section « Dépendances » ci\-dessus.  
  
 Au delà de ceci, la signification conceptuelle de `x:Subclass` est indéfinie par l'implémentation des services XAML .NET Framework.  Cela est dû au fait que le comportement des services XAML .NET Framework ne spécifie pas l'intégralité du modèle de programmation par lequel le balisage XAML et le code de stockage sont connectés.  Les implémentations de concepts supplémentaires connexes à `x:Class` et `x:Subclass` sont exécutées par des frameworks spécifiques qui utilisent des modèles de programmation ou des modèles d'application pour définir comment connecter le balisage XAML, le balisage compilé et le code\-behind basé sur CLR.  Chacune de ces infrastructures peut avoir ses propres actions de génération qui activent une partie du comportement, ou des composants spécifiques qui doivent être inclus dans l'environnement de génération.  Dans une infrastructure, les actions de génération peuvent également varier selon le langage CLR spécifique utilisé pour le code\-behind.  
  
## Remarques sur l'utilisation de WPF  
 `x:Subclass` peut être sur une racine de page ou sur la racine <xref:System.Windows.Application> dans la définition d'application, qui a déjà `x:Class`.  La déclaration de `x:Subclass`  sur un élément autre qu'une racine de page ou d'application, ou sa spécification lorsqu'aucun `x:Class` n'existe, provoque une erreur de compilation.  
  
 La création de classes dérivées qui fonctionnent correctement pour le scénario `x:Subclass` est relativement complexe.  Vous devrez peut\-être examiner les fichiers intermédiaires \(les fichiers .g produits dans le dossier obj de votre projet par compilation de balise, dont le nom comprend le nom du fichier .xaml\).  Ces fichiers intermédiaires peuvent vous aider à déterminer l'origine de certaines constructions de programmation dans les classes partielles jointes au sein de l'application compilée.  
  
 Les gestionnaires d'événements dans la classe dérivée doivent être `internal override` \(`Friend Overrides` dans [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]\) afin de substituer les stubs pour les gestionnaires créés dans la classe intermédiaire au moment de la compilation.  Sinon, les implémentations de classe dérivée masqueront l'implémentation de la classe intermédiaire et les gestionnaires de classe intermédiaire ne sont pas appelés.  
  
 Lorsque vous définissez `x:Class` et `x:Subclass`, vous ne devez pas fournir d'implémentation pour la classe référencée par `x:Class`.  Vous devez uniquement lui attribuer un nom via l'attribut `x:Class`, afin que le compilateur puisse avoir une idée de la classe créée dans les fichiers intermédiaires \(dans ce cas, le compilateur ne sélectionne pas de nom par défaut\).  Vous pouvez donner à la classe `x:Class` une implémentation ; toutefois, ce n'est pas le scénario classique pour l'utilisation de `x:Class` et de `x:Subclass`.  
  
## Voir aussi  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [XAML et classes personnalisées pour WPF](../../../ocs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)