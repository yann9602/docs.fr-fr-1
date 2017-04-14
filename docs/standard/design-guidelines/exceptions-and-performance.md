---
title: "Exceptions et performances | Microsoft Docs"
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
  - "tester-doer (modèle)"
  - "TryParse (modèle)"
  - "lever des exceptions"
  - "exceptions, performances"
  - "lever des exceptions, performances"
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Exceptions et performances
Un problème courant lié aux exceptions est que si les exceptions sont utilisées pour le code qui échoue régulièrement, les performances de l’implémentation sera inacceptables. Il s’agit d’une inquiétude. Lorsqu’un membre lève une exception, ses performances peuvent être beaucoup plus lent. Toutefois, il est possible d’obtenir de bonnes performances tout en respectant strictement les instructions de l’exception qui sont autorisés à l’aide des codes d’erreur. Deux modèles décrits dans cette section indiquent comment procéder.  
  
 **X ne pas** utiliser des codes d’erreur en raison de problèmes que les exceptions peuvent dégrader les performances.  
  
 Pour améliorer les performances, il est possible d’utiliser le modèle Doer ou le modèle d’analyse Try, décrites dans les deux sections suivantes.  
  
## Tester\-Doer \(modèle\)  
 Parfois, les performances d’un membre de la levée d’exceptions peuvent être améliorées en divisant le membre en deux. Examinons le <xref:System.Collections.Generic.ICollection%601.Add%2A> Procédé de la <xref:System.Collections.Generic.ICollection%601> interface.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 La méthode `Add` lève une exception si la collection est en lecture seule. Cela peut être un problème de performances dans les scénarios où l’appel de méthode est censé échouent souvent. Une des méthodes pour atténuer ce problème consiste à vérifier si la collection est accessible en écriture avant d’essayer d’ajouter une valeur.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 Le membre utilisé pour tester une condition qui, dans notre exemple, est la propriété `IsReadOnly`, est appelé par le testeur. Le membre utilisé pour effectuer une opération potentiellement levée d’exceptions, la `Add` méthode dans notre exemple, est appelé l’exécuteur.  
  
 **✓ envisagez** le Tester\-Doer \(modèle\) pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.  
  
## Try\-analyse de modèle  
 Pour les API très sensibles aux performances, un modèle encore plus rapide que le modèle Tester\-Doer décrites dans la section précédente doit être utilisé. Le modèle appelle pour ajuster le nom de membre pour effectuer un test précis cas une partie de la sémantique du membre. Par exemple, <xref:System.DateTime> définit un <xref:System.DateTime.Parse%2A> méthode qui lève une exception en cas de l’analyse d’une chaîne. Il définit également un correspondant <xref:System.DateTime.TryParse%2A> méthode tente d’analyser, mais retourne la valeur false si l’analyse échoue et retourne le résultat d’une analyse réussie utilisant un `out` paramètre.  
  
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
  
 Lorsque vous utilisez ce modèle, il est important de définir la fonctionnalité de try en termes stricts. Si le membre échoue pour une raison quelconque autre que le bloc try bien défini, le membre doit lève toujours une exception correspondante.  
  
 **✓ envisagez** le modèle d’analyse de Try pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.  
  
 **✓ faire** utilisent le préfixe « Try » et la valeur booléenne de type de retour pour les méthodes d’implémentation de ce modèle.  
  
 **✓ faire** fournissent un membre levant des exceptions pour chaque membre de l’utilisation du modèle d’analyse de Try.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Instructions de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md)