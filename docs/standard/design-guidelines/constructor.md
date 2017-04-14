---
title: "Conception de constructeurs | Microsoft Docs"
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
  - "règles de conception de membres, constructeurs"
  - "constructeurs, les règles de conception"
  - "constructeurs d'instance"
  - "constructeurs de type"
  - "membres virtuels"
  - "constructeurs, types"
  - "constructeurs par défaut"
  - "constructeurs statiques"
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Conception de constructeurs
Il existe deux types de constructeurs : tapez les constructeurs et les constructeurs d’instance.  
  
 Constructeurs de type sont statiques et sont exécutés par le CLR avant que le type est utilisé. Constructeurs d’instance exécuté lorsqu’une instance d’un type est créée.  
  
 Constructeurs de type ne peut pas prendre des paramètres. Constructeurs d’instance peuvent. Constructeurs d’instances qui n’acceptent pas de paramètres sont souvent appelées constructeurs par défaut.  
  
 Les constructeurs sont le moyen le plus naturel pour créer des instances d’un type. La plupart des développeurs recherche et essayez d’utiliser un constructeur avant d’autres méthodes de création d’instances \(par exemple, les méthodes de fabrique\).  
  
 **✓ envisagez** fournissant simple, dans l’idéal, par défaut, les constructeurs.  
  
 Un constructeur simple possède un très petit nombre de paramètres, et tous les paramètres sont des primitives ou enums. Ces constructeurs simples augmentent la facilité d’utilisation de l’infrastructure.  
  
 **✓ envisagez** à l’aide d’une méthode de fabrique statique au lieu d’un constructeur si la sémantique de l’opération requise ne correspond pas directement à la construction d’une nouvelle instance, ou si les règles de conception du constructeur vous semblent pas naturelles.  
  
 **✓ faire** utiliser les paramètres de constructeur comme des raccourcis pour définir les propriétés principales.  
  
 Il ne doit y avoir aucune différence sémantique entre l’utilisation du constructeur vide suivi par des jeux de propriétés et un constructeur à plusieurs arguments.  
  
 **✓ faire** utiliser le même nom pour les paramètres du constructeur et une propriété si les paramètres de constructeur sont utilisés pour définir simplement la propriété.  
  
 La seule différence entre ces paramètres et les propriétés est la casse.  
  
 **✓ faire** un minimum de travail dans le constructeur.  
  
 Les constructeurs ne beaucoup de travail autre que capturer les paramètres du constructeur. Le coût de tout autre traitement doit être différé jusqu'à ce que nécessaire.  
  
 **✓ faire** lever des exceptions à partir des constructeurs d’instance, le cas échéant.  
  
 **✓ faire** déclarer explicitement le constructeur public par défaut dans les classes, si un tel constructeur est requis.  
  
 Si vous ne déclarez explicitement de constructeur sur un type, nombreux langages \(tels que c\#\) ajoute automatiquement un constructeur public par défaut. \(Les classes abstraites obtenir un constructeur protégé.\)  
  
 Ajoutez un constructeur paramétrable à une classe empêche le compilateur d’ajouter le constructeur par défaut. Cela entraîne souvent des modifications avec rupture accidentelle.  
  
 **X éviter** définition explicite des constructeurs par défaut sur les structures.  
  
 Création d’un tableau rend plus rapidement, car si le constructeur par défaut n’est pas défini, il n’a pas à être exécuté sur tous les emplacements dans le tableau. Notez que de nombreux compilateurs, notamment c\#, ne pas autoriser les structs peuvent avoir des constructeurs sans paramètre pour cette raison.  
  
 **X éviter** appel des membres virtuels sur un objet à l’intérieur de son constructeur.  
  
 Appel d’un membre virtuel entraîne le remplacement de la plus dérivé est appelée, même si le constructeur du type plus dérivé n'a pas été entièrement exécuté.  
  
### Instructions de constructeur de type  
 **✓ faire** rendre constructeurs statiques privé.  
  
 Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type. Le CLR appelle le constructeur statique avant la première instance du type est créée ou que des membres statiques de ce type sont appelées. L’utilisateur n’a aucun contrôle sur lorsque le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par du code autre que le CLR. Selon les opérations effectuées dans le constructeur, cela peut provoquer un comportement inattendu. Le compilateur c\# force des constructeurs statiques comme privé.  
  
 **X ne pas** lever des exceptions à partir des constructeurs statiques.  
  
 Si une exception est levée à partir d’un constructeur de type, le type n’est pas utilisable dans le domaine d’application actuel.  
  
 **✓ envisagez** l’initialisation de champs statiques inline au lieu d’explicitement à l’aide de constructeurs statiques, car le runtime est en mesure d’optimiser les performances des types qui n’ont pas un constructeur statique explicitement défini.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)