---
title: "Conception de structures | Microsoft Docs"
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
  - "indications de conception de bibliothèques de classes (.NET Framework), structures"
  - "libérer des structures"
  - "allouer des structures"
  - "types valeur, structures"
  - "conception de la structure"
  - "Tapez les instructions de conception, structures"
  - "structures (.NET Framework), les règles de conception"
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Conception de structures
Le type de valeur à usage général est souvent appelé un struct, le mot clé c\#. Cette section fournit des instructions pour la conception de la structure générale.  
  
 **X ne pas** fournir un constructeur par défaut pour un struct.  
  
 Cette règle permet les tableaux de structures doit être créé sans exécuter le constructeur sur chaque élément du tableau. Notez que c\# n’autorise pas les structures d’avoir des constructeurs par défaut.  
  
 **X ne pas** définissent les types de valeur mutable.  
  
 Types valeur mutable ont plusieurs problèmes. Par exemple, lorsqu’un accesseur Get de propriété retourne un type de valeur, l’appelant reçoit une copie. Étant donné que la copie est créée implicitement, les développeurs n’est peut\-être pas conscient qu’ils connaissent une mutation la copie et non la valeur d’origine. En outre, certains langages \(langages dynamiques, en particulier\) ont des problèmes à l’aide de types valeur mutable, car même si les variables locales, quand il est déréférencé, une copie doit être faite.  
  
 **✓ faire** garantir un état où toutes les données de l’instance est défini sur zéro, false ou null \(le cas échéant\) est valide.  
  
 Cela empêche la création accidentelle d’instances non valides lors de la création d’un tableau des structures des.  
  
 **✓ faire** implémenter <xref:System.IEquatable%601> sur des types valeur.  
  
 Le <xref:System.Object.Equals%2A?displayProperty=fullName> méthode sur des types valeur entraîne la conversion boxing et son implémentation par défaut n’est pas très efficace, car il utilise la réflexion.<xref:System.IEquatable%601.Equals%2A> peut avoir de meilleures performances et peut être implémentée afin qu’elle n’entraîne pas de boxing.  
  
 **X ne pas** étendre explicitement <xref:System.ValueType>. En fait, la plupart des langages éviter ce problème.  
  
 En général, les structures peuvent être très utiles, mais ne doivent être utilisées pour les valeurs small, unique et immuables qui ne seront pas boxed fréquemment.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Choix entre les classes et structs](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)