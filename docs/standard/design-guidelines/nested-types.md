---
title: "Types imbriqués"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ae09df49b97cc2fe84285c3a37e1562da185f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types"></a>Types imbriqués
Un type imbriqué est un type défini dans l’étendue d’un autre type, qui est appelé le type englobant. Un type imbriqué a accès à tous les membres de son type englobant. Par exemple, il a accès à des champs privés définis dans le type englobant et protéger les champs définis dans tous les ascendants du type englobant.  
  
 En général, les types imbriqués doivent être utilisés avec modération. et ce, pour plusieurs raisons. Certains développeurs ne connaissent pas complètement le concept. Les développeurs peuvent, par exemple, rencontrer des problèmes avec la syntaxe de déclaration de variables de types imbriqués. Les types imbriqués sont également très étroitement avec leurs types englobants et par conséquent ne sont pas adaptés pour être des types à usage général.  
  
 Les types imbriqués sont mieux adaptées pour modéliser les détails d’implémentation de ses types englobants. L’utilisateur final doivent rarement avoir à déclarer des variables d’un type imbriqué et presque jamais devez instancier explicitement les types imbriqués. Par exemple, l’énumérateur d’une collection peut être un type imbriqué de cette collection. En général, les énumérateurs sont instanciés par leur type englobant, et de nombreux langages prenant en charge l’instruction foreach, les variables de l’énumérateur ont rarement être déclaré par l’utilisateur final.  
  
 **✓ FAIRE** utilisez des types imbriqués lorsque la relation entre le type imbriqué et son type externe est telle que sémantique de l’accessibilité des membres est souhaitable.  
  
 **X ne sont pas** utiliser les types imbriqués publics en tant qu’un regroupement logique construire ; utilisez des espaces de noms pour ce.  
  
 **X Évitez** exposées publiquement des types imbriqués. La seule exception est si les variables du type imbriqué doivent être déclarées que dans les rares scénarios sous-classement ou d’autres scénarios de personnalisation avancées.  
  
 **X ne sont pas** utilisez des types imbriqués, si le type est susceptible d’être référencés en dehors du type conteneur.  
  
 Par exemple, un enum passé à une méthode définie sur une classe ne doit pas être défini comme un type imbriqué dans la classe.  
  
 **X ne sont pas** utilisez des types imbriqués s’ils doivent être instancié par le code client.  Si un type a un constructeur public, il doit probablement pas être imbriqué.  
  
 Si un type peut être instancié, qui semble indiquer le type a un lieu dans le cadre de son propre (vous pouvez créer, utiliser et détruire sans passer par le type externe) et ne doivent donc pas être imbriquées. Types internes ne doivent pas être réutilisés largement en dehors du type externe sans aucune relation quelque type externe.  
  
 **X ne sont pas** définir un type imbriqué en tant que membre d’une interface. De nombreux langages ne gèrent pas une construction de ce type.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de type](../../../docs/standard/design-guidelines/type.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
