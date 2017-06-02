---
title: "Lev&#233;e d’exceptions | Microsoft Docs"
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
  - "lever des exceptions"
  - "lever explicitement des exceptions"
  - "lever des exceptions, des instructions de conception"
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Lev&#233;e d’exceptions
Levée d’exceptions les instructions décrites dans cette section requièrent une bonne définition de la signification de l’échec d’exécution. Échec d’exécution se produit chaque fois qu’un membre ne peut pas qu’il avait été conçu \(ce que le nom de membre implique\). Par exemple, si le `OpenFile` méthode ne peut pas retourner un handle de fichier ouvert à l’appelant, il peut être considéré comme un échec d’exécution.  
  
 La plupart des développeurs sont à l’aise avec l’utilisation d’exceptions pour les erreurs d’utilisation telles que la division par zéro ou de références null. Dans le Framework, les exceptions sont utilisées pour toutes les conditions d’erreur, y compris les erreurs d’exécution.  
  
 **X ne pas** renvoyer les codes d’erreur.  
  
 Les exceptions sont le principal moyen de signaler les erreurs dans les infrastructures.  
  
 **✓ faire** rapport d’erreurs d’exécution en levant des exceptions.  
  
 **✓ envisagez** mettre fin au processus en appelant `System.Environment.FailFast` \(fonctionnalité de .NET Framework 2.0\) au lieu de lever une exception si votre code rencontre une situation où il est risqué pour davantage de l’exécution.  
  
 **X ne pas** utilise des exceptions pour le flux normal de contrôle, si possible.  
  
 À l’exception des défaillances du système et les opérations avec des conditions de concurrence potentielle, concepteurs doivent concevoir les API pour les utilisateurs peuvent écrire du code qui ne lève pas d’exceptions. Par exemple, vous pouvez fournir un moyen de vérifier les conditions préalables avant d’appeler un membre pour les utilisateurs peuvent écrire du code qui ne lève pas d’exceptions.  
  
 Le membre permet de vérifier les conditions préalables d’un autre membre est souvent appelé un testeur et le membre qui effectue réellement le travail est appelé un exécuteur.  
  
 Il existe des cas lorsque le modèle Doer peut avoir une surcharge de performances inacceptables. Dans ce cas, le modèle d’analyse de Try soi\-disant convient \(voir [Exceptions et performances](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Pour plus d’informations\).  
  
 **✓ envisagez** les implications en matière de performances de lever des exceptions. Taux de throw supérieure à 100 par seconde sont susceptibles d’affecter sensiblement les performances de la plupart des applications.  
  
 **✓ faire** document toutes les exceptions levées par les membres pouvant être appelés publiquement en raison d’une violation du membre de contrat \(au lieu d’une défaillance du système\) et les traitent dans le cadre de votre contrat.  
  
 Les exceptions qui font partie du contrat de ne doivent pas changer d’une version à l’autre \(exception ne doit pas changer, et de nouvelles exceptions ne doivent pas être ajoutées\).  
  
 **X ne pas** ont des membres publics qui peuvent lever ou non basé sur une option.  
  
 **X ne pas** avoir des membres publics qui retournent des exceptions comme valeur de retour ou un `out` paramètre.  
  
 Retourner des exceptions à partir des API publiques au lieu de lever les va à l’encontre de nombreux avantages du rapport d’erreurs de type exception.  
  
 **✓ envisagez** à l’aide des méthodes de générateur d’exceptions.  
  
 Il est courant lève la même exception à partir de différents endroits. Pour éviter un excès de code, utilisez les méthodes d’assistance qui créent des exceptions et initialisent leurs propriétés.  
  
 En outre, les membres qui lèvent des exceptions ne sont pas récupérées inline. Déplacement de l’instruction throw dans le Générateur de peut permettre au membre d’être inline.  
  
 **X ne pas** lever des exceptions à partir de blocs de filtre d’exception.  
  
 Lorsqu’un filtre d’exceptions lève une exception, l’exception est interceptée par le CLR, et le filtre retourne false. Ce comportement est indiscernable le filtre exécute et retourne explicitement la valeur false et est donc très difficile à déboguer.  
  
 **X éviter** lever explicitement des exceptions à partir de blocs finally. Les exceptions levées implicitement résultant des appels de méthodes sont acceptables.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Instructions de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md)