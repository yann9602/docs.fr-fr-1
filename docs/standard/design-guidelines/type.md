---
title: "Conception de type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tapez les instructions de conception"
  - "type sur la conception, la conception de type"
  - "indications de conception de bibliothèques de classes (.NET Framework), la conception de type"
  - "types (.NET Framework), les règles de conception"
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Conception de type
Du point de vue CLR, il existe seulement deux catégories de types : types référence et les types valeur, mais pour une discussion sur la conception d’infrastructure, nous divisons types en groupes plus logiques, chacun avec ses propres règles de conception spécifiques.  
  
 Les classes sont des types référence générale. Ils constituent la majorité des types dans la plupart des infrastructures. Classes de régler leur popularité pour la riche jeu de fonctionnalités orientées objet qu’ils prennent en charge et leur applicabilité générale. Classes de base et les classes abstraites sont des groupes logiques spéciales relatives à l’extensibilité.  
  
 Les interfaces sont des types qui peuvent être implémentées par les types référence et les types de valeur. Elles peuvent donc servir racines des hiérarchies polymorphes des types référence et les types valeur. En outre, interfaces peuvent être utilisés pour simuler l’héritage multiple, ce qui n’est pas pris en charge en mode natif par le CLR.  
  
 Les structures sont des types valeur générale et doivent être réservés pour les types simples, similaires aux primitives de langage.  
  
 Énumérations sont un cas spécial de types de valeur utilisé pour définir des jeux court de valeurs, telles que les jours de la semaine, les couleurs de console et ainsi de suite.  
  
 Les classes statiques sont destinés à être des conteneurs pour les membres statiques de types. Ils sont souvent utilisés pour fournir des raccourcis à d’autres opérations.  
  
 Délégués, des exceptions, des attributs, des tableaux et des collections sont tous les cas spéciaux de types de référence destinés à des utilisations spécifiques, et les recommandations en matière de conception et d’utilisation sont étudiées ailleurs dans ce guide.  
  
 **✓ faire** vous assurer que chaque type est un ensemble bien défini de membres associés, pas seulement un ensemble aléatoire de fonctionnalités non liées.  
  
## Dans cette section  
 [Choix entre les classes et structs](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Conception de classes abstraites](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Conception de classes statiques](../../../docs/standard/design-guidelines/static-class.md)  
 [Conception de l’interface](../../../docs/standard/design-guidelines/interface.md)  
 [Conception de structures](../../../docs/standard/design-guidelines/struct.md)  
 [Conception d’énumérations](../../../docs/standard/design-guidelines/enum.md)  
 [Types imbriqués](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)