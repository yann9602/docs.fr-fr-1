---
title: Noms de membres de type
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d489d4cf61adfe8550bd16b85cd658e0d545c861
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-type-members"></a>Noms de membres de type
Les types sont constitués de membres : méthodes, propriétés, événements, constructeurs et les champs. Les sections suivantes décrivent les conventions de dénomination des membres de type.  
  
## <a name="names-of-methods"></a>Noms des méthodes  
 Étant donné que les méthodes sont le moyen d’une action, les règles de conception méthode les noms doivent être verbes ou verbaux. Suivez ces indications également sert à distinguer les noms de méthode à partir des noms de propriété et le type, qui sont des expressions nominales ou adjectif.  
  
 **✓ FAIRE** indiquent les noms de méthodes qui sont des verbes ou des phrases de verbe.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Noms des propriétés  
 Contrairement aux autres membres, les propriétés doivent être fournies expression nominale ou noms adjectivales. C'est-à-dire, car une propriété qui fait référence aux données et le nom de la propriété reflète qui. Casse Pascal est toujours utilisé pour les noms de propriété.  
  
 **✓ FAIRE** nom des propriétés à l’aide d’un nom, une expression nominale ou un adjectif.  
  
 **X ne sont pas** ont des propriétés qui correspondent au nom de méthodes « Get » comme dans l’exemple suivant :  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Ce modèle indique généralement que la propriété doit être réellement d’une méthode.  
  
 **✓ FAIRE** nom des propriétés de la collection avec une expression au pluriel décrivant les éléments de la collection au lieu d’utiliser une expression au singulier, suivie de la « Liste » ou « Collection ».  
  
 **✓ FAIRE** propriétés de type Boolean une expression affirmative (`CanSeek` au lieu de `CantSeek`). Si vous le souhaitez, vous pouvez également faire précéder propriétés booléennes avec « Est », « peut » ou « A » mais uniquement lorsqu’il ajoute la valeur.  
  
 **✓ Envisagez** donnant une propriété le même nom que son type.  
  
 Par exemple, la propriété suivante correctement Obtient et définit une valeur d’énumération nommée `Color`, de sorte que la propriété est nommée `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Noms des événements  
 Événements font toujours référence à une action, soit celui se produise ou celui qui s’est produite. Par conséquent, comme avec les méthodes, les événements sont nommées avec les verbes et conjugaison de verbes est utilisé pour indiquer l’heure lorsque l’événement est déclenché.  
  
 **✓ FAIRE** nommer des événements avec un verbe ou une expression verbale.  
  
 Exemples `Clicked`, `Painting`, `DroppedDown`, et ainsi de suite.  
  
 **✓ FAIRE** indiquent les noms des événements avec un concept d’avant et après, en utilisant le présent et passé temps.  
  
 Par exemple, un événement de fermeture qui est déclenché avant la fermeture d’une fenêtre est être appelé `Closing`, et qui est déclenché après la fermeture de la fenêtre se nomme `Closed`.  
  
 **X ne sont pas** utiliser « Before » ou « After » préfixes ou suffixes pour indiquer les et les post-événements. Utilisation actuelle et le temps passé comme décrit ci-dessus.  
  
 **✓ FAIRE** nom de gestionnaires d’événements (délégués utilisés comme types d’événements) avec le suffixe « EventHandler », comme indiqué dans l’exemple suivant :  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ FAIRE** utiliser deux paramètres nommés `sender` et `e` dans les gestionnaires d’événements.  
  
 Le paramètre sender représente l’objet qui a déclenché l’événement. Le paramètre de l’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.  
  
 **✓ FAIRE** nom d’événement avec le suffixe « EventArgs » classes d’argument.  
  
## <a name="names-of-fields"></a>Noms de champs  
 Les instructions d’affectation de noms de champ s’appliquent pour les champs statiques publics et protégés. Les champs internes et privés ne sont pas couverts par les instructions et des champs d’instance publics ou protégés ne sont pas autorisées par le [les règles de conception de membre](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ FAIRE** utilisent la casse Pascal dans les noms de champ.  
  
 **✓ FAIRE** nom des champs à l’aide d’un nom, une expression nominale ou un adjectif.  
  
 **X ne sont pas** utiliser un préfixe pour les noms de champ.  
  
 Par exemple, n’utilisez pas « g_ » ou « s_ » pour indiquer les champs statiques.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
