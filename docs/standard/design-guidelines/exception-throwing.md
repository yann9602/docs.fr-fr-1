---
title: "Levée d'exceptions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b1aa0eaccc26e1bd7cc6b78953dc0a782b2f952e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exception-throwing"></a>Levée d'exceptions
Levée d’exceptions des indications décrites dans cette section nécessitent une bonne définition de la signification de l’échec d’exécution. Échec d’exécution se produit chaque fois qu’un membre ne peut pas faire, il a été conçu pour faire (ce que le nom de membre implique). Par exemple, si le `OpenFile` méthode ne peut pas retourner un handle de fichier ouvert à l’appelant, il est considéré comme un échec d’exécution.  
  
 La plupart des développeurs sont à l’aise avec l’utilisation d’exceptions pour les erreurs d’utilisation telles que la division par zéro ou des références null. Dans le Framework, les exceptions sont utilisées pour toutes les conditions d’erreur, y compris les erreurs d’exécution.  
  
 **X ne sont pas** codes d’erreur.  
  
 Les exceptions sont le moyen principal de signalement des erreurs dans les infrastructures.  
  
 **✓ FAIRE** signale les échecs de l’exécution en levant des exceptions.  
  
 **✓ Envisagez** mettre fin au processus en appelant `System.Environment.FailFast` (fonctionnalité de .NET Framework 2.0) au lieu de lever une exception si votre code rencontre une situation où il est risqué pour obtenir de l’exécution.  
  
 **X ne sont pas** utiliser des exceptions pour le flux normal de contrôle, si possible.  
  
 À l’exception des défaillances du système et les opérations avec des conditions de concurrence potentielle, les concepteurs de framework doivent concevoir les API pour les utilisateurs peuvent écrire du code qui ne lève pas d’exceptions. Par exemple, vous pouvez fournir un moyen de vérifier les conditions préalables avant d’appeler un membre pour les utilisateurs peuvent écrire du code qui ne lève pas d’exceptions.  
  
 Le membre utilisé pour vérifier des conditions préalables d’un autre membre est communément appelée un testeur et le membre qui effectue réellement le travail est appelé un exécuteur.  
  
 Il existe des cas lorsque le modèle utilisateur testeur peut avoir une surcharge de performances inacceptables. Dans ce cas, le modèle d’analyse de Try soi-disant doit être considérée comme (consultez [Exceptions et les performances](../../../docs/standard/design-guidelines/exceptions-and-performance.md) pour plus d’informations).  
  
 **✓ Envisagez** l’impact sur les performances de lever des exceptions. Taux de throw supérieure à 100 par seconde sont susceptibles de considérablement affecter les performances de la plupart des applications.  
  
 **✓ FAIRE** document toutes les exceptions levées par les membres pouvant être appelés publiquement en raison d’une violation du membre de contrat (au lieu d’une défaillance du système) et les traitent en tant que partie de votre contrat.  
  
 Les exceptions qui font partie du contrat de ne doivent pas changer d’une version à l’autre (par exemple, type d’exception ne doit pas modifier, et de nouvelles exceptions ne doivent pas être ajoutées).  
  
 **X ne sont pas** ont des membres publics qui peuvent lever ou non basées sur une option.  
  
 **X ne sont pas** des membres publics de retournent des exceptions comme valeur de retour ou un `out` paramètre.  
  
 Retourner des exceptions à partir des API publiques, au lieu de lever les va à l’encontre de nombreux avantages de l’erreur de type exception.  
  
 **✓ Envisagez** à l’aide des méthodes de générateur d’exceptions.  
  
 Il est courant de lève la même exception à partir d’emplacements différents. Pour éviter l’excès de code, utilisez les méthodes d’assistance qui créent des exceptions et initialisent leurs propriétés.  
  
 En outre, les membres qui lèvent des exceptions n’obtiennent pas inline. Déplacement de l’instruction throw à l’intérieur du Générateur de peut permettre au membre être inline.  
  
 **X ne sont pas** lever des exceptions à partir de blocs de filtre d’exception.  
  
 Lorsqu’un filtre d’exceptions lève une exception, l’exception est interceptée par le CLR, et le filtre retourne false. Ce comportement est indiscernable le filtre exécute et retourne explicitement la valeur false et est donc très difficile à déboguer.  
  
 **X Évitez** lever explicitement des exceptions à partir de blocs finally. Les exceptions levées implicitement résultant d’appels de méthodes sont acceptables.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Règles de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md)
