---
title: Choix entre classe et structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68a3d2c7335ff15706925f9a7986164e6d9c0c36
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-class-and-struct"></a>Choix entre classe et structure
Les décisions de conception de base que fait face à chaque concepteur framework consiste à concevoir un type en tant que classe (type référence) ou en tant que struct (un type valeur). Bien comprendre les différences dans le comportement des types référence et les types de valeur est vitale pour rendre ce choix.  
  
 La première différence entre les types référence et les types de valeur nous étudierons est que les types référence sont alloués sur le tas et le garbage collector, tandis que les types valeur sont alloués sur la pile ou inline dans les types et libérée lorsque la pile déroule ou lorsque son type conteneur obtient désallouée. Par conséquent, les allocations et désallocations de types valeur sont en général moins cher que les allocations et désallocations de types référence.  
  
 Ensuite, les tableaux de référence sont des types allouée hors ligne, ce qui signifie que le tableau d’éléments sont simplement les références aux instances du type référence résidant sur le tas. Les tableaux de types valeur sont allouées en ligne, ce qui signifie que les éléments du tableau sont les instances réelles du type valeur. Par conséquent, les allocations et désallocations de tableaux de type valeur sont beaucoup moins coûteuse que les allocations et désallocations de tableaux de type référence. En outre, dans la majorité des cas de tableaux de type valeur présentent bien une meilleure localité de référence.  
  
 La différence suivante concerne l’utilisation de mémoire. Types valeur obtient convertie (boxed) lors de la conversion vers un type référence ou d’une des interfaces qu’ils implémentent. Ils obtiennent unboxed lors de la conversion vers le type de valeur. Étant donné que les zones sont des objets qui sont alloués sur le tas et sont par le garbage collector, trop boxing et unboxing peut avoir un impact négatif sur le tas, le garbage collector et, finalement, les performances de l’application.  En revanche, pas de boxing se produit comme types référence sont convertis.  
  
 Ensuite, les assignations de type référence copier la référence, alors que les assignations de type valeur copiez la valeur entière. Par conséquent, des types référence volumineux sont moins cher que les affectations de types de valeur élevée.  
  
 Enfin, les types référence sont passés par référence, tandis que les types valeur sont passés par valeur. Modifications apportées à une instance d’un type référence affectent toutes les références pointant vers l’instance. Instances de type valeur sont copiés lorsqu’ils sont passés par valeur. Lorsqu’une instance d’un type valeur est modifiée, elle naturellement n’affecte pas un de ses copies. Étant donné que les copies ne sont pas créés explicitement par l’utilisateur, mais sont créés implicitement lorsque les arguments sont passés ou retournent les valeurs sont retournées, les types de valeur qui peuvent être modifiés peuvent être déconcertant pour de nombreux utilisateurs. Par conséquent, les types valeur doivent être immuables.  
  
 En règle générale, la plupart des types dans une infrastructure doit-elle être des classes. Toutefois, il existe certaines situations dans lesquelles les caractéristiques d’un type valeur qu’il est plus approprié à utiliser les structures.  
  
 **✓ Envisagez** définition d’un struct au lieu d’une classe si les instances du type sont généralement de courte durée et de petite taille ou sont généralement incorporés dans d’autres objets.  
  
 **X Évitez** définition d’un struct, sauf si le type possède toutes les caractéristiques suivantes :  
  
-   Il représente logiquement une seule valeur, semblable aux types primitifs (`int`, `double`, etc..).  
  
-   Il a une taille d’instance inférieure à 16 octets.  
  
-   Il est immuable.  
  
-   Il n’aura pas à être convertie (boxed) fréquemment.  
  
 Dans tous les autres cas, vous devez définir vos types en tant que classes.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
