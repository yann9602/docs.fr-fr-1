---
title: "Conception de champs | Microsoft Docs"
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
  - "champs, les règles de conception"
  - "champs en lecture seule"
  - "règles de conception de membres, champs"
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Conception de champs
Le principe d’encapsulation est un des notions principales dans la conception orientée objet. Ce principe établit que les données stockées à l’intérieur d’un objet doivent être accessibles uniquement à cet objet.  
  
 Un moyen utile d’interpréter le principe consiste à dire qu’un type doit être conçu afin que les modifications apportées aux champs de ce type \(modification du nom ou type\) peuvent être apportées sans rupture du code autre que pour les membres du type. Cette interprétation implique immédiatement que tous les champs doivent être privés.  
  
 Nous exclure constantes et statiques des champs en lecture seule de cette restriction stricte, car ces champs, presque par définition, ne sont jamais tenus à modifier.  
  
 **X ne pas** contiennent des champs d’instance qui sont publics ou protégés.  
  
 Vous devez fournir des propriétés pour accéder à des champs au lieu de les rendre publics ou protégés.  
  
 **✓ faire** utiliser les champs constants pour les constantes qui ne changent pas.  
  
 Le compilateur augmente les valeurs des champs const directement dans le code appelant. Par conséquent, les valeurs const ne peuvent jamais être modifiées sans risquer de perdre la compatibilité.  
  
 **✓ faire** utiliser statique publique `readonly` champs pour les instances d’objet prédéfinies.  
  
 S’il existe des instances prédéfinies du type, déclarez les champs statiques en lecture seule comme publics du type lui\-même.  
  
 **X ne pas** affecter des instances de types mutables à `readonly` champs.  
  
 Un type mutable est un type avec des instances qui peuvent être modifiés une fois qu’ils sont instanciés. Par exemple, les tableaux, la plupart des collections et flux sont des types mutables, mais <xref:System.Int32?displayProperty=fullName>, <xref:System.Uri?displayProperty=fullName>, et <xref:System.String?displayProperty=fullName> sont toutes immuables. Le modificateur en lecture seule sur un champ de type référence empêche l’instance stockée dans le champ ne soit pas remplacé, mais il n’empêche pas les données d’instance du champ d’être modifié en appelant des membres modification de l’instance.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)