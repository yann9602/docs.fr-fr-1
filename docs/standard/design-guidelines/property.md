---
title: "Conception des propriétés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 477b3b69ce1b8a3bb160e8e120885239e3d99e56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="property-design"></a>Conception des propriétés
Bien que les propriétés sont techniquement très semblables aux méthodes, ils sont très différents en termes de leurs scénarios d’utilisation. Ils doivent être considérés comme des champs intelligents. Ils ont la syntaxe d’appel de champs et la flexibilité des méthodes.  
  
 **✓ FAIRE** créer des propriétés get-only si l’appelant ne doit pas être en mesure de modifier la valeur de la propriété.  
  
 Gardez à l’esprit ce cas le type de la propriété est un type référence mutable, la valeur de propriété peut être modifiée même si la propriété est get-only.  
  
 **X ne sont pas** fournissent des propriétés ou propriétés à définir uniquement avec la méthode setter ayant le plus large d’accessibilité de l’accesseur Get.  
  
 Par exemple, n’utilisez pas de propriétés avec un accesseur Set public et un accesseur Get protégé.  
  
 Si l’accesseur Get de propriété ne peut pas être fourni, implémenter la fonctionnalité en tant que méthode à la place. Pensez à démarrer avec le nom de la méthode `Set` et suivez avec ce que vous avez appellerait la propriété. Par exemple, <xref:System.AppDomain> possède une méthode appelée `SetCachePath` au lieu d’avoir une propriété de jeu uniquement appelée `CachePath`.  
  
 **✓ FAIRE** fournissent des valeurs par défaut raisonnables pour toutes les propriétés, garantissant que les valeurs par défaut n’entraînent pas une faille de sécurité ou du code très inefficace.  
  
 **✓ FAIRE** permettent d’être définie dans n’importe quel ordre, même si cela aboutit à un état temporaire non valide de l’objet.  
  
 Il est courant pour les deux ou plusieurs propriétés être reliés entre eux à un point où des valeurs d’une propriété peuvent être non valides, étant donné les valeurs des autres propriétés sur le même objet. Dans ce cas, les exceptions résultant de l’état non valide doivent être différées jusqu'à ce que les propriétés liées entre elles sont réellement utilisées ensemble par l’objet.  
  
 **✓ FAIRE** conserver la valeur précédente si un accesseur Set de propriété lève une exception.  
  
 **X Évitez** lever des exceptions à partir des accesseurs Get de propriété.  
  
 Accesseurs Get de propriété doit être des opérations simples et ne doit pas avoir toutes les conditions préalables. Si un accesseur Get peut lever une exception, il doit probablement être modifiée pour être une méthode. Notez que cette règle ne s’applique pas à des indexeurs, où devrait exceptions à la suite de valider les arguments.  
  
### <a name="indexed-property-design"></a>Conception de la propriété indexée  
 Une propriété indexée est une propriété spéciale qui peut avoir des paramètres et peut être appelée avec une syntaxe spéciale semblable à l’indexation de tableau.  
  
 Les propriétés indexées sont communément appelé indexeurs. Les indexeurs doivent être utilisés uniquement dans les API qui donnent accès aux éléments d’une collection logique. Par exemple, une chaîne est un ensemble de caractères et que l’indexeur sur <xref:System.String?displayProperty=nameWithType> a été ajouté à accéder à ses caractères.  
  
 **✓ Envisagez** des indexeurs pour fournir l’accès aux données stockées dans un tableau interne.  
  
 **✓ Envisagez** fournir des indexeurs sur les types de collections d’éléments.  
  
 **X Évitez** à l’aide des propriétés avec plusieurs paramètres indexées.  
  
 Si la conception requiert plusieurs paramètres, reconsidérez si la propriété représente réellement un accesseur à une collection logique. Si elle n’est pas le cas, utilisez à la place des méthodes. Pensez à démarrer avec le nom de la méthode `Get` ou `Set`.  
  
 **X Évitez** indexeurs avec les types de paramètres autres que <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, ou d’un enum.  
  
 Si la conception nécessite d’autres types de paramètres, est important si l’API représente réellement un accesseur à une collection logique. Si elle n’est pas le cas, utilisez une méthode. Pensez à démarrer avec le nom de la méthode `Get` ou `Set`.  
  
 **✓ FAIRE** utiliser le nom `Item` pour des propriétés indexées, sauf s’il existe un meilleur nom (par exemple, consultez la <xref:System.String.Chars%2A> propriété sur `System.String`).  
  
 En c#, les indexeurs sont par défaut nommé « Item ». Le <xref:System.Runtime.CompilerServices.IndexerNameAttribute> peut être utilisé pour personnaliser ce nom.  
  
 **X ne sont pas** fournissent à la fois un indexeur et des méthodes qui sont sémantiquement équivalents.  
  
 **X ne sont pas** fournissent plusieurs familles d’indexeurs surchargés dans un type.  
  
 Elle est appliquée par le compilateur c#.  
  
 **X ne sont pas** différent de l’utilisation des propriétés indexées.  
  
 Elle est appliquée par le compilateur c#.  
  
### <a name="property-change-notification-events"></a>Événements de Notification de modification de propriété  
 Il est parfois utile de fournir un événement de notification à l’utilisateur des modifications dans une valeur de propriété. Par exemple, `System.Windows.Forms.Control` déclenche un `TextChanged` événement après la valeur de son `Text` propriété a changé.  
  
 **✓ Envisagez** modifier les déclenchement d’événements de notification lorsque les valeurs de propriété dans les API de niveau supérieur (composants de concepteur généralement) sont modifiés.  
  
 S’il existe un bon scénario d’un utilisateur de savoir quand une propriété d’un objet change, l’objet doit déclencher un événement de notification de modification de la propriété.  
  
 Toutefois, il est peu de chances d’être intéressant le traitement de déclencher des événements pour les API de bas niveau tels que les types de base ou des collections. Par exemple, <xref:System.Collections.Generic.List%601> ne déclenchera pas ces événements quand un nouvel élément est ajouté à la liste et le `Count` de propriété est modifiée.  
  
 **✓ Envisagez** déclenchement modifier les événements de notification lorsque la valeur d’une propriété modifiée via la force externe.  
  
 Si une valeur de propriété change via une force externe (d’une manière différente en appelant des méthodes sur l’objet), déclencher des événements indiquent au développeur que la valeur change et qu’il a été modifié. Un bon exemple est le `Text` propriété d’un contrôle de zone de texte. Lorsque l’utilisateur tape du texte dans un `TextBox`, la valeur de propriété change automatiquement.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
