---
title: "Instructions relatives aux Collections | Microsoft Docs"
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
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Instructions relatives aux Collections
N’importe quel type conçu spécifiquement pour manipuler un groupe d’objets ayant des caractéristiques communes peut être considéré comme une collection. Il est presque toujours appropriée pour ces types d’implémenter <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, donc dans cette section, nous ne considérons que les types implémentant une ou deux de ces interfaces sont les collections.  
  
 **X ne pas** utiliser des collections faiblement typées dans les API publiques.  
  
 Le type de toutes les valeurs de retour et paramètres représentant les éléments de la collection doit être le type exact d’élément, pas un de ses types de base \(cela s’applique uniquement aux membres publics de la collection\).  
  
 **X ne pas** utiliser <xref:System.Collections.ArrayList> ou <xref:System.Collections.Generic.List%601> dans les API publiques.  
  
 Ces types sont des structures de données conçus pour être utilisés dans l’implémentation interne, pas dans les API publiques.`List<T>` est optimisé pour les performances et la puissance au détriment de la propreté de l’API et de flexibilité. Par exemple, si vous retournez `List<T>`, vous pas jamais sera en mesure de recevoir des notifications lorsque le code client modifie la collection. En outre, `List<T>` expose de nombreux membres, tels que <xref:System.Collections.Generic.List%601.BinarySearch%2A>, qui ne sont pas utiles ou applicable dans de nombreux scénarios. Les suivantes sections décrivent les types \(abstractions\) conçus spécifiquement pour une utilisation dans les API publiques.  
  
 **X ne pas** utiliser `Hashtable` ou `Dictionary<TKey,TValue>` dans les API publiques.  
  
 Ces types sont des structures de données conçus pour être utilisé dans l’implémentation interne. Les API publiques doivent utiliser <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, ou un type personnalisé implémentant une ou les deux interfaces.  
  
 **X ne pas** utiliser <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, ou tout autre type qui implémente une de ces interfaces, sauf comme type de retour d’un `GetEnumerator` \(méthode\).  
  
 Types de retour des énumérateurs à partir de méthodes autres que `GetEnumerator` ne peut pas être utilisé avec la `foreach` instruction.  
  
 **X ne pas** implémente deux `IEnumerator<T>` et `IEnumerable<T>` sur le même type. Ces conditions s’appliquent aux interfaces non génériques `IEnumerator` et `IEnumerable`.  
  
## Paramètres de collecte  
 **✓ faire** utiliser possibles spécialisé au moins un type comme type de paramètre. La plupart des membres lors de collections de paramètres utilisent la `IEnumerable<T>` interface.  
  
 **X éviter** à l’aide de <xref:System.Collections.Generic.ICollection%601> ou <xref:System.Collections.ICollection> en tant que paramètre uniquement pour accéder à la `Count` propriété.  
  
 Envisagez plutôt d’utiliser `IEnumerable<T>` ou `IEnumerable` et vérification de manière dynamique si l’objet implémente `ICollection<T>` ou `ICollection`.  
  
## Propriétés de la collection et les valeurs de retour  
 **X ne pas** fournissent des propriétés de collection définissables.  
  
 Les utilisateurs peuvent remplacer le contenu de la collection en effaçant la collection tout d’abord, puis ajouter le nouveau contenu. Si le remplacement de la collection entière est un scénario courant, vous pouvez obtenir le `AddRange` méthode sur la collection.  
  
 **✓ faire** utiliser `Collection<T>` ou une sous\-classe de `Collection<T>` pour les propriétés ou le retour des valeurs qui représentent les collections en lecture\/écriture.  
  
 Si `Collection<T>` ne répond pas à certaines conditions \(par exemple, la collection ne doit pas implémenter <xref:System.Collections.IList>\), utilisez une collection personnalisée en implémentant `IEnumerable<T>`, `ICollection<T>`, ou <xref:System.Collections.Generic.IList%601>.  
  
 **✓ faire** utiliser <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, une sous\-classe de `ReadOnlyCollection<T>`, ou dans de rares cas `IEnumerable<T>` pour les propriétés ou le retour des valeurs qui représentent les collections en lecture seule.  
  
 En général, préférez `ReadOnlyCollection<T>`. Si celui\-ci ne remplit pas certaines conditions \(par exemple, la collection ne doit pas implémenter `IList`\), utilisez une collection personnalisée en implémentant `IEnumerable<T>`, `ICollection<T>`, ou `IList<T>`. Si vous implémentez un regroupement personnalisé en lecture seule, implémenter `ICollection<T>.ReadOnly` retourne false.  
  
 Dans le cas où vous êtes sûr que le seul scénario, vous devez toujours prendre en charge est itération avant uniquement, vous pouvez simplement utiliser `IEnumerable<T>`.  
  
 **✓ envisagez** à l’aide des sous\-classes de collections génériques de base au lieu d’utiliser directement les collections.  
  
 Ainsi, pour un meilleur nom et d’ajouter des membres d’assistance qui ne sont pas présents sur les types de collection de base. Cela s’applique en particulier aux API de niveau supérieur.  
  
 **✓ envisagez** retournant une sous\-classe de `Collection<T>` ou `ReadOnlyCollection<T>` à partir de méthodes et propriétés fréquemment utilisées.  
  
 Il sera ainsi possible d’ajouter des méthodes d’assistance ou de modifier l’implémentation de la collection à l’avenir.  
  
 **✓ envisagez** à l’aide d’une collection à clé si les éléments stockés dans la collection aient des clés uniques \(nom, ID, etc.\). Collections à clé sont des collections peuvent être indexées par un entier et une clé et qui sont généralement implémentées en héritant de `KeyedCollection<TKey,TItem>`.  
  
 Collections à clé généralement ont supérieure à un prix abordable et ne doivent pas être utilisées si la charge mémoire dépasse les avantages d’avoir les clés.  
  
 **X ne pas** retournent des valeurs null à partir des propriétés de collection ou de méthodes qui retournent des collections. Retourne une collection vide ou un tableau vide à la place.  
  
 La règle générale est que les collections \(élément 0\) null et vides ou les tableaux doivent être traitées de la même.  
  
### Instantanés par rapport aux Collections en direct  
 Qui représente un état à un moment donné dans le temps de collections sont appelées des collections d’instantanés. Par exemple, une collection qui contient les lignes retournées par une requête de base de données serait un instantané. Les collections représentent toujours l’état actuel sont appelées des collections en direct. Par exemple, une collection de `ComboBox` est une collection en direct.  
  
 **X ne pas** retournent des collections de capture instantanée à partir des propriétés. Propriétés doivent retourner des collections en direct.  
  
 Accesseurs Get de propriété doivent être des opérations très légers. Renvoi d’une capture instantanée requiert la création d’une copie d’une collection interne dans une opération o \(n\).  
  
 **✓ faire** utiliser une collection de capture instantanée ou une `IEnumerable<T>` \(ou son sous\-type\) pour représenter les regroupements volatiles \(c'est\-à\-dire, qui peut changer sans modification explicite de la collection\).  
  
 En règle générale, toutes les collections qui représente une ressource partagée \(par exemple, les fichiers dans un répertoire\) sont volatiles. Ces collections sont très difficiles ou impossibles à implémenter en tant que collections dynamiques, sauf si l’implémentation est simplement un énumérateur avant uniquement.  
  
## Choix entre les tableaux et Collections  
 **✓ faire** préférer les collections sur les tableaux.  
  
 Collections offrent un contrôle accru de contenu peuvent évoluer au fil du temps et ne sont plus utilisables. En outre, l’utilisation de tableaux pour les scénarios en lecture seule est déconseillée, car le coût de clonage du tableau est excessif. Études ont montré que certains développeurs convient le mieux à l’aide des API basées sur la collection.  
  
 Toutefois, si vous développez des API de bas niveau, il peut être préférable d’utiliser des tableaux pour les scénarios en lecture\-écriture. Les tableaux ont un plus faible encombrement mémoire, ce qui permet de réduire le jeu de travail, et accès aux éléments d’un tableau est plus rapide car il est optimisé par le runtime.  
  
 **✓ envisagez** à l’aide de tableaux dans les API de bas niveau pour réduire la consommation de mémoire et optimiser les performances.  
  
 **✓ faire** utiliser des tableaux d’octets au lieu de collections d’octets.  
  
 **X ne pas** utiliser des tableaux pour les propriétés si la propriété devrait renvoyer un nouveau tableau \(par exemple, une copie du tableau interne\) chaque fois que l’accesseur Get est appelé.  
  
## Implémenter des Collections personnalisées  
 **✓ envisagez** héritant de `Collection<T>`, `ReadOnlyCollection<T>`, ou `KeyedCollection<TKey,TItem>` lors de la création de nouvelles collections.  
  
 **✓ faire** implémenter `IEnumerable<T>` lors de la création de nouvelles collections. Envisagez d’implémenter `ICollection<T>` ou même `IList<T>` où il est préférable.  
  
 Lors de l’implémentation de ce type de collection personnalisé, suivez établi par le modèle de l’API `Collection<T>` et `ReadOnlyCollection<T>` autant que possible. Autrement dit, implémentez explicitement les membres de mêmes, nommez les paramètres tels que le nom de ces deux collections leur et ainsi de suite.  
  
 **✓ envisagez** l’implémentation des interfaces de collection non générique \(`IList` et `ICollection`\) si la collection doit souvent être passée à l’API en prenant ces interfaces en tant qu’entrée.  
  
 **X éviter** implémenter des interfaces de collection sur des types avec des API complexes sans rapport avec le concept d’une collection.  
  
 **X ne pas** héritent des collections de base non génériques comme `CollectionBase`. Utilisez `Collection<T>`, `ReadOnlyCollection<T>`, et `KeyedCollection<TKey,TItem>` à la place.  
  
### Regroupements personnalisés d’affectation de noms  
 Collections \(types qui implémentent `IEnumerable`\) sont créés principalement pour deux raisons : \(1\) pour créer une nouvelle structure de données avec des opérations spécifiques à la structure et souvent différentes caractéristiques de performance de structures de données existantes \(par exemple,  <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>\) et \(2\) pour créer une collection spécialisée pour maintenir un ensemble spécifique d’éléments \(par exemple,  <xref:System.Collections.Specialized.StringCollection>\). Structures de données sont souvent utilisées dans l’implémentation interne des applications et des bibliothèques. Les collections spécialisées sont principalement destinées à être exposées dans les API \(les types de propriété et de paramètre\).  
  
 **✓ faire** utiliser le suffixe « Dictionnaire » dans les noms de l’implémentation des abstractions `IDictionary` ou `IDictionary<TKey,TValue>`.  
  
 **✓ faire** utiliser le suffixe « Collection » dans les noms de types implémentant `IEnumerable` \(ou un de ses descendants\) et représentant une liste d’éléments.  
  
 **✓ faire** utiliser le nom de structure de données approprié pour les structures de données personnalisées.  
  
 **X éviter** à l’aide de tous les suffixes qui implique une implémentation particulière, tels que « LinkedList » ou « Table de hachage » dans les noms des abstractions de la collection.  
  
 **✓ envisagez** préfixer les noms de collection avec le nom du type d’élément. Par exemple, une collection de stocker des éléments de type `Address` \(l’implémentation `IEnumerable<Address>`\) doit être nommé `AddressCollection`. Si le type d’élément est une interface, préfixe « I » de l’élément de type peut être omis. Par conséquent, une collection de <xref:System.IDisposable> éléments peuvent être appelées `DisposableCollection`.  
  
 **✓ envisagez** à l’aide du préfixe « ReadOnly » dans les noms de collections en lecture seule si une collection accessible en écriture correspondante peut être ajoutée ou existe déjà dans l’infrastructure.  
  
 Par exemple, une collection en lecture seule de chaînes doit être appelée `ReadOnlyStringCollection`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)