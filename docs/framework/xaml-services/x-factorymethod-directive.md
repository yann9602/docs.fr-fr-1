---
title: "x:FactoryMethod Directive | Microsoft Docs"
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
  - "XAML. x:FactoryMethod directive [XAML Services]"
  - "FactoryMethod directive in XAML [XAML Services]"
  - "x:FactoryMethod directive [XAML Services]"
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:FactoryMethod Directive
Spécifie une méthode autre qu'un constructeur qu'un processeur XAML doit utiliser pour initialiser un objet après avoir résolu son type de stockage.  
  
## Utilisation d'attribut XAML, no x:Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## Utilisation d'attribut XAML, x:Arguments comme élément\(s\)  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`methodname`|Le nom de méthode de chaîne d'une méthode que les processeurs XAML appellent pour initialiser l'instance spécifié comme `object`.  Consultez la section Notes.|  
|`oneOrMoreObjectElements`|Un ou plusieurs éléments objet des objets qui spécifient des paramètres de méthode de fabrique.  L'ordre est significatif ; il indique la séquence selon laquelle les arguments doivent être passés à la méthode de fabrique.|  
  
## Notes  
 Si `methodname` est une méthode d'instance, il ne peut pas être qualifié.  
  
 Les méthodes statiques en tant que méthodes de fabrique sont prises en charge.  Si `methodname` est une méthode statique, `methodname` est fourni comme une combinaison *typeName*.*methodName*, où *typeName* nomme la classe qui définit la méthode de fabrique statique.  *NomType* peut être qualifié par un préfixe s'il fait référence à un type dans un xmlns mappé.  *NomType* peut être un type différent de `typeof(``object``)`.  
  
 La méthode de fabrique doit être une méthode publique déclarée du type qui stocke l'élément objet approprié.  
  
 La méthode de fabrique doit retourner une instance qui est assignable à l'objet approprié.  Les méthodes de fabrique ne doivent jamais retourner null.  
  
 `x:Arguments` fonctionne sur un principe de meilleure correspondance pour les signatures de méthodes de fabrique.  La mise en correspondance évalue en premier le nombre de paramètre.  S'il y a plusieurs correspondances possibles pour un nombre de paramètre, le type de paramètre est évalué et la meilleure correspondance est déterminée.  S'il reste une ambiguïté après cette phase d'évaluation, le comportement de processeur XAML est indéfini.  
  
 L'utilisation de l'élément `x:FactoryMethod` n'est pas une utilisation de l'élément de propriété au sens strict, car la balise de la directrice ne fait pas référence au type de l'élément objet contenant.  Il est attendu que l'utilisation de l'élément est moins commune qu'une utilisation d'attributs.  `x:Arguments` \(utilisation d'attribut ou d'élément\) peut être utilisé avec l'utilisation de l'élément `x:FactoryMethod`, mais cela n'est pas affiché spécifiquement dans les sections Utilisation.  
  
 `x:FactoryMethod` comme élément doit précéder tout autre élément de propriété, doit précéder tout `x:Arguments` également fourni comme éléments et doit précéder tout contenu\/texte interne\/texte d'initialisation.  
  
## Voir aussi  
 [x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md)