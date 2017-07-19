---
title: "Conception de classes statiques | Microsoft Docs"
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
  - "Tapez les instructions de conception, les classes statiques"
  - "indications de conception de bibliothèques de classes (.NET Framework), classes"
  - "classes (.NET Framework), statiques"
  - "classes statiques (.NET Framework)"
  - "classes (.NET Framework), les règles de conception"
  - "conception de type, classes"
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Conception de classes statiques
Une classe statique est définie comme une classe qui contient uniquement des membres statiques \(bien entendu, outre les membres d’instance héritées <xref:System.Object?displayProperty=fullName> et éventuellement un constructeur privé\). Certains langages fournissent une prise en charge intégrée des classes statiques. En c\# 2.0 et versions ultérieures, lorsqu’une classe est déclarée comme étant statique, il est scellé, abstraite et aucun membre d’instance peut être remplacée ou déclaré.  
  
 Les classes statiques sont un compromis entre la conception orientée objet et la simplicité. Ils sont souvent utilisés pour fournir des raccourcis à d’autres opérations \(telles que <xref:System.IO.File?displayProperty=fullName>\), titulaires de méthodes d’extension ou de fonctionnalités pour lequel un wrapper orienté objet est injustifié \(tel que <xref:System.Environment?displayProperty=fullName>\).  
  
 **✓ faire** utilisation des classes statiques avec parcimonie.  
  
 Classes statiques doivent être utilisés uniquement comme classes de prise en charge pour le noyau orientée objet de l’infrastructure.  
  
 **X ne pas** traitent des classes statiques comme un compartiment d’objets divers.  
  
 **X ne pas** déclarer ou substituer les membres d’instance dans les classes statiques.  
  
 **✓ faire** déclarer des classes statiques comme sealed, abstract et ajoutez un constructeur d’instance privé, si votre langage de programmation ne dispose pas de prise en charge intégrée des classes statiques.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)