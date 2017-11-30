---
title: x:FactoryMethod, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 0d53db49961c2a75e4547f6b57240cefd2cc17c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod, directive
Spécifie une méthode autre qu’un constructeur qu’un processeur XAML doit utiliser pour initialiser un objet après avoir résolu son type de stockage.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Utilisation d’attributs XAML, aucune x : Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Utilisation d’attribut XAML, x : Arguments comme élément (s)  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`methodname`|Le nom de méthode de chaîne d’une méthode qui appellent des processeurs XAML pour initialiser l’instance spécifié comme `object`. Consultez la section Notes.|  
|`oneOrMoreObjectElements`|Un ou plusieurs éléments objet pour les objets qui spécifient les paramètres de méthode de fabrique. Ordre est significatif ; Il désigne l’ordre dans lequel les arguments doivent être passés à la méthode de fabrique.|  
  
## <a name="remarks"></a>Remarques  
 Si `methodname` est une méthode d’instance, il ne peut pas être qualifié.  
  
 Les méthodes statiques en tant que méthodes de fabrique sont prises en charge. Si `methodname` est une méthode statique, `methodname` est fournie comme un *typeName*. *methodName* combinaison, où *typeName* nomme la classe qui définit la méthode de fabrique statique. *nom de type* peut être qualifié par un préfixe s’il fait référence à un type dans un xmlns mappé. *typeName* peut être un type différent de `typeof(``object``)`.  
  
 La méthode de fabrique doit être une méthode publique déclarée du type qui stocke l’élément objet appropriée.  
  
 La méthode de fabrique doit retourner une instance ne peut être assignée à l’objet correspondant. Méthodes de fabrique ne doivent jamais retourner null.  
  
 `x:Arguments`fonctionne sur un principe de meilleure correspondance pour les signatures des méthodes de fabrique. Mise en correspondance évalue d’abord le nombre de paramètres. S’il existe plusieurs correspondances possibles pour un nombre de paramètres, le type de paramètre est évaluée et la meilleure correspondance est déterminée. S’il reste une ambiguïté après cette phase d’évaluation, le comportement du processeur XAML est non défini.  
  
 Le `x:FactoryMethod` utilisation de l’élément n’est pas utilisation des éléments de propriété dans le sens classique, étant donné que le balisage de la directive ne référence pas de type de l’élément objet contenant. Il est probable que l’utilisation d’élément est moins courant que l’utilisation d’attributs. `x:Arguments`(utilisation d’attribut ou élément) peut être utilisée avec `x:FactoryMethod` utilisation de l’élément, mais ce n’est pas affiché spécifiquement dans les sections d’utilisation.  
  
 `x:FactoryMethod`comme un élément doit précéder tous les autres éléments de propriété, doit précéder tout `x:Arguments` également fourni en tant qu’éléments et doit précéder tout contenu/interne texte/texte d’initialisation.  
  
## <a name="see-also"></a>Voir aussi  
 [x:Arguments (directive)](../../../docs/framework/xaml-services/x-arguments-directive.md)
