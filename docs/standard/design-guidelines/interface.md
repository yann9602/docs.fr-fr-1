---
title: "Conception de l’interface | Microsoft Docs"
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
  - "interfaces (.NET Framework), les règles de conception"
  - "conception de type, interfaces"
  - "indications de conception de bibliothèques de classes (.NET Framework), interfaces"
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Conception de l’interface
Bien que la plupart des API sont mieux modélisées à l’aide des classes et structures, il existe des cas dans lequel les interfaces sont plus appropriées ou sont la seule option.  
  
 Le CLR ne prend pas en charge l’héritage multiple \(par exemple, des classes CLR ne peuvent pas hériter de plusieurs classes de base\), mais il autorise les types à implémenter une ou plusieurs interfaces en plus de l’héritage d’une classe de base. Par conséquent, les interfaces sont souvent utilisés pour obtenir l’effet de l’héritage multiple. Par exemple, <xref:System.IDisposable> est une interface qui permet aux types de prise en charge disposability indépendant de toute autre hiérarchie d’héritage dans lequel ils veulent participer.  
  
 L’autre situation qui vous définissez une interface est appropriée est dans la création d’une interface commune qui peut être pris en charge par plusieurs types, y compris certains types de valeur. Types valeur ne peuvent pas hériter de types autres que <xref:System.ValueType>, mais elles peuvent implémenter des interfaces, par conséquent, à l’aide d’une interface est la seule option pour fournir un type de base commun.  
  
 **✓ faire** définissent une interface si vous avez besoin d’une API commune pour prendre en charge un ensemble de types qui inclut les types de valeur.  
  
 **✓ envisagez** définition d’une interface si vous avez besoin prendre en charge ses fonctionnalités sur des types qui héritent déjà d’un autre type.  
  
 **X éviter** à l’aide des interfaces de marqueur \(interfaces sans membres\).  
  
 Si vous avez besoin marquer une classe comme ayant une caractéristique spécifique \(marqueur\), utilisez en général, un attribut personnalisé plutôt que d’une interface.  
  
 **✓ faire** fournir au moins un type qui est une implémentation d’une interface.  
  
 Ceci contribue à valider la conception de l’interface des tâches. Par exemple, <xref:System.Collections.Generic.List%601> est une implémentation de la <xref:System.Collections.Generic.IList%601> interface.  
  
 **✓ faire** fournissent au moins une API qui utilise chacune des interfaces définies \(une méthode qui prend l’interface comme paramètre ou une propriété de type interface\).  
  
 Ceci contribue à valider la conception de l’interface des tâches. Par exemple, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> consomme la <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> interface.  
  
 **X ne pas** ajouter des membres à une interface précédemment fournie.  
  
 Cela briserait les implémentations de l’interface. Vous devez créer une nouvelle interface afin d’éviter les problèmes de versioning.  
  
 À l’exception des situations décrites dans ces instructions, vous devez, en général, choisir les classes plutôt que des interfaces dans la conception de bibliothèques réutilisables de code managé.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)