---
title: "Conception des propri&#233;t&#233;s | Microsoft Docs"
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
  - "règles de conception de membres, propriétés"
  - "Propriétés (.NET Framework), les règles de conception"
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Conception des propri&#233;t&#233;s
Bien que les propriétés sont techniquement très similaires aux méthodes, ils sont très différents en termes de leurs scénarios d’utilisation. Ils doivent être considérés comme des champs intelligents. Ils ont la syntaxe d’appel de champs et la souplesse des méthodes.  
  
 **✓ faire** créer des propriétés get\-only si l’appelant ne doit pas être en mesure de modifier la valeur de la propriété.  
  
 N’oubliez pas qu’en l’absence du type de la propriété est un type référence mutable, la valeur de propriété peut être modifiée même si la propriété est get\-only.  
  
 **X ne pas** fournissent uniquement des propriétés ou des propriétés avec la méthode setter ayant la plus large d’accessibilité de l’accesseur Get.  
  
 Par exemple, n’utilisez pas de propriétés avec un setter public et un accesseur Get protégé.  
  
 Si l’accesseur Get de propriété ne peut pas être fourni, implémenter les fonctionnalités en tant que méthode. Pensez à commencer avec le nom de la méthode `Set` et suivez avec ce que vous avez appellerait la propriété. Par exemple, <xref:System.AppDomain> possède une méthode appelée `SetCachePath` au lieu d’avoir une propriété uniquement appelée `CachePath`.  
  
 **✓ faire** fournissent des valeurs par défaut raisonnables pour toutes les propriétés, garantissant que les valeurs par défaut n’entraînent pas une faille de sécurité ou du code très inefficace.  
  
 **✓ faire** permettent d’être définies dans n’importe quel ordre, même si cela aboutit à un état temporaire non valide de l’objet.  
  
 Il est courant pour les deux ou plusieurs propriétés être liés à un point où des valeurs d’une propriété peuvent être non valides d’après les valeurs des autres propriétés sur le même objet. Dans ce cas, les exceptions qui résultent de l’état non valide doivent être reportées jusqu'à ce que les propriétés de corrélation sont réellement conjointement par l’objet.  
  
 **✓ faire** conserver la valeur précédente si un accesseur Set de propriété lève une exception.  
  
 **X éviter** lever des exceptions à partir des accesseurs Get de propriété.  
  
 Accesseurs Get de propriété doivent être des opérations simples et ne doivent pas les conditions préalables. Si un accesseur Get peut lever une exception, il doit probablement être modifiée pour une méthode. Notez que cette règle ne s’applique pas aux indexeurs, où les exceptions à la suite valider les arguments devrait.  
  
### Conception de propriétés indexées  
 Une propriété indexée est une propriété spéciale qui peut avoir des paramètres et peut être appelée avec une syntaxe spéciale semblable à l’indexation de tableau.  
  
 Les propriétés indexées sont couramment appelées les indexeurs. Indexeurs doivent être utilisées uniquement dans les API qui donnent accès aux éléments d’une collection logique. Par exemple, une chaîne est un ensemble de caractères et l’indexeur sur <xref:System.String?displayProperty=fullName> a été ajouté pour accéder à ses caractères.  
  
 **✓ envisagez** des indexeurs pour fournir l’accès aux données stockées dans un tableau interne.  
  
 **✓ envisagez** fournir des indexeurs sur les types représentant des collections d’éléments.  
  
 **X éviter** à l’aide des propriétés avec plusieurs paramètres indexées.  
  
 Si la conception requiert plusieurs paramètres, reconsidérez si la propriété représente vraiment un accesseur à une collection logique. Si elle n’est pas le cas, utilisez plutôt les méthodes. Pensez à commencer avec le nom de la méthode `Get` ou `Set`.  
  
 **X éviter** indexeurs avec les types de paramètres autres que <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.String?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, ou d’un enum.  
  
 Si le design nécessite d’autres types de paramètres, est important si l’API représente réellement un accesseur à une collection logique. Si elle n’est pas le cas, utilisez une méthode. Pensez à commencer avec le nom de la méthode `Get` ou `Set`.  
  
 **✓ faire** utilisent le nom `Item` pour les propriétés indexées, sauf s’il existe un nom plus \(par exemple, consultez le <xref:System.String.Chars%2A> propriété sur `System.String`\).  
  
 En c\#, les indexeurs par défaut nommé « Item ». Le <xref:System.Runtime.CompilerServices.IndexerNameAttribute> peut être utilisé pour personnaliser ce nom.  
  
 **X ne pas** fournir à la fois un indexeur et des méthodes qui sont sémantiquement équivalentes.  
  
 **X ne pas** fournissent plusieurs familles d’indexeurs surchargés dans un type.  
  
 Ceci est renforcé par le compilateur c\#.  
  
 **X ne pas** différent de l’utilisation des propriétés indexées.  
  
 Ceci est renforcé par le compilateur c\#.  
  
### Événements de Notification de modification de propriété  
 Il est parfois utile de fournir un événement notifier l’utilisateur des modifications apportées à une valeur de propriété. Par exemple, `System.Windows.Forms.Control` déclenche un `TextChanged` événement après la valeur de son `Text` propriété a changé.  
  
 **✓ envisagez** déclenchement modifier les événements de notification lorsque les valeurs de propriété dans les API de niveau supérieur \(généralement concepteur composants\) sont modifiés.  
  
 S’il existe un bon scénario d’un utilisateur de savoir quand une propriété d’un objet change, l’objet doit déclencher un événement de notification de modification de la propriété.  
  
 Toutefois, il est peu de chances d’être sérieusement le traitement de déclencher des événements pour les API de bas niveau tels que les types de base ou des collections. Par exemple, <xref:System.Collections.Generic.List%601> ne déclenchera pas ces événements lorsqu’un nouvel élément est ajouté à la liste et le `Count` de propriété est modifiée.  
  
 **✓ envisagez** déclenchement modifier les événements de notification lorsque la valeur d’une propriété modifiée par l’intermédiaire des forces extérieures.  
  
 Si une valeur de propriété est modifiée par une force externe \(de façon différente en appelant des méthodes sur l’objet\), déclencher des événements indiquent au développeur que la valeur change et a été modifié. Un bon exemple est le `Text` propriété d’un contrôle de zone de texte. Lorsque l’utilisateur tape du texte dans un `TextBox`, la valeur de propriété change automatiquement.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)