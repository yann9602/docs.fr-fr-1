---
title: x:Members, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 230c6359c59b9f00738de9ce7ceeccd69899135f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xmembers-directive"></a>x:Members, directive
Contient un jeu de membres qui sont définis dans le balisage, et qui s’appliquent à x : Class de l’élément parent.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`className`|Nom de la classe de stockage ou de la classe partielle pour la production XAML. Consultez la section Notes.|  
|`oneOrMoreMembers`|Un ou plusieurs éléments objet qui représentent des définitions de membre. En règle générale, il s’agit `x:Property` éléments objet. Consultez la section Notes.|  
  
## <a name="remarks"></a>Remarques  
 Dans l’implémentation de Services XAML .NET Framework, il n’existe aucune classe de stockage ou d’une implémentation d’un membre sous-jacent pour `x:Members`. `x:Members`est un membre XAML spécial qui peut exister en tant que membre sur n’importe quel type. Dans un flux de nœud XAML, `x:Members` est représenté sous la forme d’un membre nommé `Members`, à partir de l’espace de noms XAML du langage XAML. Le membre `Members` contient une liste générique en lecture seule de `Member` objets. Dans le balisage par défaut, les membres individuels sont spécifiés comme `x:Property` éléments de propriété. `x:Property`est un type plus précis, en particulier pour les propriétés des types et ne peut être assigné à `x:Member`. Pour plus d’informations, consultez [x : Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).  
  
 Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable. Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`. Toutefois, le mécanisme permettant d'associer des types et des membres ou de générer des définitions de membre dynamique n'est pas pris en charge au niveau des services XAML .NET Framework. En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML. Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x : Members pour Windows Workflow Foundation  
 Pour Windows Workflow Foundation, `x:Members` contient les membres d’une activité personnalisée entièrement composée en XAML ou XAML : défini par les membres dynamiques pour un concepteur d’activités avec code-behind. L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML. Cela n'est pas obligatoire dans le cadre des services XAML .NET Framework, mais le devient quand la production XAML est chargée par les actions de génération MSBUILD qui prennent en charge les activités personnalisées et le XAML de Windows Workflow Foundation en général. `x:Members`doit être le premier élément enfant dans le balisage de l’élément objet qui déclare le `x:Class`.
