---
title: "x:Code, type XAML intrinsèque"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d39249a5d1c0e230d21e6d889b92d0b57c98e2ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code, type XAML intrinsèque
Permet la sélection élective de code dans une production XAML. Ce code peut être compilé par une implémentation du processeur XAML qui compile XAML ou à gauche dans la production XAML pour une utilisation ultérieure comme interprétation par un runtime.  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Notes  
 Le code dans le `x:Code` élément de directive XAML est toujours interprété dans l’espace de noms XML général et les espaces de noms XAML fourni. Par conséquent, il est généralement nécessaire de placer le code utilisé pour `x:Code` à l’intérieur d’un `CDATA` segment.  
  
 `x:Code`n’est pas autorisé pour tous les mécanismes de déploiement d’une production XAML. Le code doit être compilé dans les infrastructures spécifiques (par exemple WPF). Dans d’autres infrastructures, `x:Code` utilisation peut être refusée de façon générale.  
  
 Pour les infrastructures qui autorisent managé `x:Code` du contenu, le compilateur de langage correct à utiliser pour `x:Code` contenu est déterminé par les paramètres et les cibles du projet contenant utilisé pour compiler l’application.  
  
## <a name="wpf-usage-notes"></a>Notes d’utilisation WPF  
 Code déclaré dans `x:Code` pour WPF a plusieurs limitations notables :  
  
-   Le `x:Code` élément de directive doit être un élément enfant immédiat de l’élément racine de la production XAML.  
  
-   [x : Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) doit être fourni sur l’élément racine parent.  
  
-   Le code placé dans `x:Code` sera traité par compilation pour figurer dans la portée de la classe partielle qui est déjà en cours de création pour cette page XAML. Par conséquent, tout code que vous définissez doit être membres ou des variables de cette classe partielle.  
  
-   Vous ne pouvez pas définir de classes supplémentaires autrement qu’en imbriquant une classe à l’intérieur de la classe partielle (l’imbrication est autorisée, mais il n’est pas typique, car les classes imbriquées ne peuvent pas être référencés en XAML). Espaces de noms CLR autres que l’espace de noms qui est utilisé pour la classe partielle existante ne peut pas être définie ou ajoutée à.  
  
-   Références à des entités de code en dehors de l’espace de noms CLR classe partielle doivent être qualifiés complet. Si les membres déclarés sont des remplacements pour les membres substituables de classe partielle, il est obligatoire avec le mot clé override de langage spécifique. Si les membres déclarés dans `x:Code` conflit avec des membres de la classe partielle est créé à partir du XAML, de sorte que le compilateur signale le conflit, le fichier XAML ne peut pas compiler ou charger.  
  
## <a name="see-also"></a>Voir aussi  
 [x:Class, directive](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Code-behind et XAML dans WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
