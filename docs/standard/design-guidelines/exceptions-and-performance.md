---
title: Exceptions et performances
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9a876a818086e0d54251f53a1e8f83cc74a574ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-and-performance"></a>Exceptions et performances
Un problème courant lié aux exceptions est que si les exceptions sont utilisées pour le code qui échoue régulièrement, les performances de l’implémentation sera inacceptable. Il s’agit d’un problème valid. Lorsqu’un membre lève une exception, ses performances peuvent être beaucoup plus lent. Toutefois, il est possible d’obtenir de bonnes performances tout en respectant strictement les instructions de l’exception interdire l’utilisation de codes d’erreur. Deux modèles sont décrites dans cette section proposent des solutions pour ce faire.  
  
 **X ne sont pas** utiliser des codes d’erreur en raison de problèmes qu’exceptions peuvent affecter négativement les performances.  
  
 Pour améliorer les performances, il est possible d’utiliser le modèle utilisateur testeur ou le modèle d’analyse de Try, décrites dans les deux sections suivantes.  
  
## <a name="tester-doer-pattern"></a>Modèle de l’exécuteur de testeur  
 Parfois, les performances d’un membre de la levée d’exceptions peuvent être améliorées en divisant le membre en deux. Examinons le <xref:System.Collections.Generic.ICollection%601.Add%2A> méthode de la <xref:System.Collections.Generic.ICollection%601> interface.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 La méthode `Add` lève si la collection est en lecture seule. Cela peut poser un problème de performances dans les scénarios où l’appel de méthode est censé échouent souvent. Un des moyens d’atténuer ce problème consiste à vérifier si la collection est accessible en écriture avant d’essayer d’ajouter une valeur.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Le membre utilisé pour tester une condition qui, dans notre exemple, est la propriété `IsReadOnly`, est appelé par le testeur. Le membre utilisé pour effectuer une opération potentiellement levée d’exceptions, la `Add` méthode dans notre exemple, est appelé l’exécuteur.  
  
 **✓ Envisagez** le modèle utilisateur testeur pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.  
  
## <a name="try-parse-pattern"></a>Essayez de l’analyse de modèle  
 Pour les API de très sensibles aux performances, un modèle plus rapide que le modèle utilisateur testeur décrites dans la section précédente doit être utilisé. Le modèle appelle pour ajuster le nom de membre pour effectuer un test bien défini de cas une partie de la sémantique de membre. Par exemple, <xref:System.DateTime> définit un <xref:System.DateTime.Parse%2A> méthode qui lève une exception en cas de l’analyse d’une chaîne. Il définit également un correspondant <xref:System.DateTime.TryParse%2A> méthode qui tente d’analyser, mais retourne la valeur false si l’analyse échoue et retourne le résultat d’une analyse réussie à l’aide un `out` paramètre.  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 Lorsque vous utilisez ce modèle, il est important de définir la fonctionnalité de try en termes de stricts. Si le membre échoue pour une raison quelconque autre que le bloc try bien défini, le membre doit lève toujours une exception correspondante.  
  
 **✓ Envisagez** le modèle d’analyse de Try pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.  
  
 **✓ FAIRE** utilisent le préfixe « Try » et la valeur booléenne de type de retour pour les méthodes d’implémentation de ce schéma.  
  
 **✓ FAIRE** fournissent un membre levant des exceptions pour chaque membre de l’utilisation du modèle d’analyse de Try.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)
