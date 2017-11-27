---
title: Instructions de conception de types
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b24a934285f88386daa764c5b28bd82cf5d39a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-design-guidelines"></a>Instructions de conception de types
Du point de vue du CLR, il existe uniquement deux catégories de types : types référence et les types valeur, mais pour une discussion sur la conception d’infrastructure, nous allons diviser les types en groupes plus logiques, chacun avec ses propres règles de conception spécifiques.  
  
 Les classes sont des types de référence de manière générale. Ils constituent la majorité des types dans la plupart des infrastructures. Classes à régler leur fréquence pour la riche ensemble de fonctionnalités orientées objet qu’ils prennent en charge et leur applicabilité générale. Classes de base et les classes abstraites sont des groupes logiques spéciales relatives à l’extensibilité.  
  
 Les interfaces sont des types qui peuvent être implémentées par les types référence et les types de valeur. Elles constituent donc racines des hiérarchies polymorphes des types référence et les types valeur. En outre, interfaces peuvent être utilisés pour simuler l’héritage multiple, ce qui n’est pas pris en charge en mode natif par le CLR.  
  
 Les structures sont des types de valeur de manière générale et doivent être réservés pour les types simples, comme des primitives de langage.  
  
 Les énumérations sont un cas spécial de types valeur utilisés pour définir des jeux court de valeurs, telles que des jours de la semaine, les couleurs de console et ainsi de suite.  
  
 Les classes statiques sont destinés à être des conteneurs pour les membres statiques de types. Elles sont utilisées pour fournir des raccourcis vers les autres opérations.  
  
 Les délégués, des exceptions, des attributs, des tableaux et des collections sont tous les cas spéciaux de types de référence prévus pour des utilisations spécifiques, et des recommandations pour la conception et d’utilisation sont traitées ailleurs dans ce guide.  
  
 **✓ FAIRE** Vérifiez que chaque type est un ensemble bien défini de membres associés, pas seulement une collection aléatoire des fonctionnalités non liées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Choix entre les classes et structs](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Conception d’une classe abstraite](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Conception d’une classe statique](../../../docs/standard/design-guidelines/static-class.md)  
 [Conception de l’interface](../../../docs/standard/design-guidelines/interface.md)  
 [Conception d’un struct](../../../docs/standard/design-guidelines/struct.md)  
 [Conception de l’enum](../../../docs/standard/design-guidelines/enum.md)  
 [Types imbriqués](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
