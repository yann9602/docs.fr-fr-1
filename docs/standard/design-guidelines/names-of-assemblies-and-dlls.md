---
title: "Noms d’assemblys et de DLL | Microsoft Docs"
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
  - "noms (.NET Framework), DLL"
  - "noms d’assemblys (.NET Framework),"
  - "assemblys (.NET Framework), noms"
  - "DLL, noms"
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Noms d’assemblys et de DLL
Un assembly est l’unité de déploiement et d’identité pour les programmes de code managé. Bien que les assemblys peuvent s’étendre sur un ou plusieurs fichiers, en général, un assembly effectue un mappage avec une DLL. Par conséquent, cette section décrit uniquement conventions d’affectation de noms DLL, qui peuvent alors être appliquées aux conventions de nom d’assembly.  
  
 **✓ faire** choisissez des noms pour vos DLL d’assembly qui suggèrent des grands segments de fonctionnalités, telles que System.Data.  
  
 Noms d’assembly et les DLL ne devront correspondent aux noms d’espace de noms, mais il est conseillé d’utiliser l’espace de noms lorsque vous nommez des assemblys. Une bonne règle empirique consiste à nommer la DLL basée sur le préfixe commun des assemblys contenus dans l’assembly. Par exemple, un assembly avec deux espaces de noms, `MyCompany.MyTechnology.FirstFeature` et `MyCompany.MyTechnology.SecondFeature`, peut être appelée `MyCompany.MyTechnology.dll`.  
  
 **✓ envisagez** nommer les DLL selon le modèle suivant :  
  
 `<Company>.<Component>.dll`  
  
 où `<Component>` contient une ou plusieurs clauses séparées par un point. Exemple :  
  
 `Litware.Controls.dll`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)