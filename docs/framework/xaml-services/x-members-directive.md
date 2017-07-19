---
title: "x:Members Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: 5
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 5
---
# x:Members Directive
Conserve un ensemble de membres définis dans le balisage qui s'appliquent au x:Class de l'élément parent.  
  
## Utilisation d'attributs XAML  
  
```  
  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`className`|Nom de la classe de stockage ou de classe partielle pour la production XAML.  Consultez la section Notes.|  
|`oneOrMoreMembers`|Un ou plusieurs éléments objet qui représentent des définitions de membre.  En général, il s'agit d'éléments objet `x:Property`.  Consultez la section Notes.|  
  
## Notes  
 Dans l'implémentation des services XAML .NET Framework, il n'y a aucune classe de prise en charge ni implémentation membre sous\-jacente pour `x:Members`.  `x:Members` est un membre XAML spécial qui peut exister en tant que membre sur n'importe quel type.  Dans un flux de nœud XAML, un élément `x:Members` est représenté comme membre nommé `Members`, à partir de l'espace de noms XAML du langage XAML.  Le membre `Members` contient une liste générique en lecture seule d'objets `Member`.  Dans le balisage type, les membres sont spécifiés en tant qu'éléments de propriété `x:Property`.  `x:Property` est un type plus précis, notamment pour les propriétés des types, et est assignable à `x:Member`.  Pour plus d'informations, consultez [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).  
  
 Pour prendre en charge une utilisation pratique de `x:Members` comme moyen de spécifier des définitions de membre dans les balises, les membres doivent être associés à une classe qui peut être modifiée.  Le modèle attendu est que `x:Members` existe en tant que membre d'un type qui spécifie `x:Class`.  Toutefois, le mécanisme pour associer des types et des membres ou pour générer des définitions de membre dynamiques n'est pas pris en charge au niveau du service du XAML de .NET Framework.  Cela est laissé aux différentes infrastructures qui ont des modèles d'application prenant en charge des définitions de membre XAML.  En général, les actions de génération MSBUILD qui balisent\-compilent le XAML et l'intègrent avec du code\-behind ou le produisent pur à partir des assembly XAML sont nécessaires pour prendre en charge cette fonctionnalité.  
  
## x:Members pour Windows Workflow Foundation  
 Pour Windows Workflow Foundation, `x:Members` contient les membres d'une activité personnalisée composée intégralement en XAML, ou des membres dynamiques définis en XAML pour un concepteur d'activités avec code\-behind.  `x:Class` doit également être spécifié dans l'élément racine de la production XAML.  Ce n'est pas une spécification au niveau des services XAML .NET Framework, mais cela devient une spécification lorsque la production XAML est chargée par les actions de génération MSBUILD qui prennent en charge les activités personnalisées et Windows Workflow Foundation XAML en général.  `x:Members` doit être le premier élément enfant dans le balisage de l'élément objet qui déclare `x:Class`.