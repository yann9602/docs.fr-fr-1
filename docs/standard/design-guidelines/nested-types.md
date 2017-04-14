---
title: "Types imbriqu&#233;s | Microsoft Docs"
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
  - "types imbriqués"
  - "types imbriqués publics"
  - "Tapez les instructions de conception, les types imbriqués"
  - "types imbriqués"
  - "membres (.NET Framework), tapez"
  - "types d’instructions (.NET Framework), imbriquées de conception bibliothèque (classe)"
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Types imbriqu&#233;s
Un type imbriqué est un type défini dans la portée d’un autre type, qui est appelé le type englobant. Un type imbriqué a accès à tous les membres de son type englobant. Par exemple, il a accès à des champs privés définis dans le type englobant et protégés des champs définis dans tous les ascendants du type englobant.  
  
 En général, les types imbriqués doivent être utilisés avec modération. et ce, pour plusieurs raisons. Certains développeurs ne sont pas entièrement familiarisés avec le concept. Ces développeurs peuvent, par exemple, avoir des problèmes avec la syntaxe de déclaration de variables de types imbriqués. Les types imbriqués sont également très étroitement avec leurs types englobants et par conséquent ne conviennent pas pour les types à usage général.  
  
 Les types imbriqués sont mieux adaptées pour la modélisation des détails d’implémentation de ses types englobants. L’utilisateur final doivent rarement avoir à déclarer des variables d’un type imbriqué et presque jamais devez instancier explicitement des types imbriqués. Par exemple, l’énumérateur d’une collection peut être un type imbriqué de cette collection. En général, les énumérateurs sont instanciés par leur type englobant, et de nombreux langages prenant en charge l’instruction foreach, variables d’énumérateur rarement doivent être déclaré par l’utilisateur final.  
  
 **✓ faire** utiliser des types imbriqués lorsque la relation entre le type imbriqué et son type externe est telle que la sémantique d’accessibilité du membre est souhaitable.  
  
 **X ne pas** utilisez les types imbriqués publics en tant qu’un regroupement logique construire ; espaces de noms à utiliser.  
  
 **X éviter** exposée publiquement les types imbriqués. La seule exception est si les variables du type imbriqué doivent être déclarées uniquement dans les rares scénarios tels que sous\-classement ou d’autres scénarios de personnalisation avancée.  
  
 **X ne pas** utiliser des types imbriqués, si le type est susceptible d’être référencés en dehors du type conteneur.  
  
 Par exemple, un enum passé à une méthode définie sur une classe ne doit pas être défini comme un type imbriqué dans la classe.  
  
 **X ne pas** utiliser des types imbriqués s’ils doivent être instanciés par code client.  Si un type possède un constructeur public, il ne doit probablement pas être imbriqué.  
  
 Si un type peut être instancié, qui semble indiquer le type a un lieu dans le cadre de son propre \(vous pourrez créer, utiliser et supprimer sans jamais à l’aide du type externe\) et ne doit donc pas être imbriquées. Types internes ne doivent pas être réutilisés largement en dehors du type externe sans aucune relation quelque type externe.  
  
 **X ne pas** définir un type imbriqué en tant que membre d’une interface. De nombreux langages ne permettent pas une telle construction.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)