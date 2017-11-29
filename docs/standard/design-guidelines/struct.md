---
title: Conception de structures
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
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1566d2b67e1dda5b0b221a2c10affb6bdaea888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="struct-design"></a>Conception de structures
Le type de valeur à usage général est souvent appelé un struct, le mot clé c#. Cette section fournit des instructions pour la conception de la structure générale.  
  
 **X ne sont pas** fournir un constructeur par défaut pour un struct.  
  
 Cette règle permet les tableaux de structs peuvent être créés sans avoir à exécuter le constructeur sur chaque élément du tableau. Notez que c# n’autorise pas les structures d’avoir des constructeurs par défaut.  
  
 **X ne sont pas** définissent les types de valeur mutable.  
  
 Les types de valeur mutable ont plusieurs problèmes. Par exemple, lorsqu’un accesseur Get retourne un type de valeur, l’appelant reçoit une copie. Étant donné que la copie est créée implicitement, les développeurs connaissez peut-être pas qu’ils sont mutation la copie et non la valeur d’origine. En outre, certains langages (langages dynamiques, en particulier) ont des problèmes à l’aide de types valeur mutable, car même des variables locales, fois déréférencé, une copie doit être effectuée.  
  
 **✓ FAIRE** s’assurer qu’un état où toutes les données de l’instance est défini sur zéro, false ou null (le cas échéant) est valide.  
  
 Cela empêche la création accidentelle d’instances non valides lors de la création d’un tableau des structures des.  
  
 **✓ FAIRE** implémenter <xref:System.IEquatable%601> sur les types valeur.  
  
 Le <xref:System.Object.Equals%2A?displayProperty=nameWithType> méthode sur les types valeur entraîne la conversion boxing et son implémentation par défaut n’est pas très efficace, car il utilise la réflexion. <xref:System.IEquatable%601.Equals%2A>peut avoir de bien meilleures performances et peut être implémentée afin qu’elle n’entraîne pas de boxing.  
  
 **X ne sont pas** prolonger explicitement <xref:System.ValueType>. En fait, la plupart des langages éviter ce problème.  
  
 En général, les structs peuvent être très utiles mais ne doit être utilisées que pour les valeurs de petite, unique et immuables qui ne seront pas boxed fréquemment.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de type](../../../docs/standard/design-guidelines/type.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Choix entre les classes et structs](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
