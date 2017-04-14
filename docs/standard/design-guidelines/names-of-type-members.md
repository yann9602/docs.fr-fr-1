---
title: "Noms des membres de Type | Microsoft Docs"
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
  - "événements (.NET Framework), noms"
  - "méthodes (.NET Framework), noms"
  - "membres de type"
  - "Propriétés (.NET Framework), noms"
  - "champs de noms"
  - "noms de champs"
  - "noms de membres de type (.NET Framework),"
  - "membres (.NET Framework), tapez"
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Noms des membres de Type
Les types sont constitués de membres : méthodes, propriétés, événements, constructeurs et les champs. Les sections suivantes décrivent les conventions de dénomination des membres de type.  
  
## Noms des méthodes  
 Étant donné que les méthodes sont les moyens de réagir, les règles de conception méthode les noms doivent être verbes ou verbaux. Suivez ces indications également sert à distinguer les noms de méthode à partir des noms de propriété et le type, qui sont des expressions nominales ou adjectif.  
  
 **✓ faire** donner des noms de méthodes sont des verbes ou des phrases de verbe.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
  
```  
  
## Noms des propriétés  
 Contrairement aux autres membres, propriétés convient expression nominale ou noms adjectives. C’est parce qu’une propriété fait référence aux données et le nom de la propriété reflète cette. Casse Pascal est toujours utilisé pour les noms de propriété.  
  
 **✓ faire** nom des propriétés à l’aide d’un nom, une expression nominale ou un adjectif.  
  
 **X ne pas** ont des propriétés qui correspondent au nom de méthodes « Get » comme dans l’exemple suivant :  
  
 `public string TextWriter { get {...} set {...} }`   
 `public string GetTextWriter(int value) { ... }`  
  
 Ce modèle indique généralement que la propriété doit être vraiment une méthode.  
  
 **✓ faire** nomment les propriétés de collection avec une phrase au pluriel décrivant les éléments de la collection au lieu d’utiliser une phrase au singulier suivie de « List » ou « Collection ».  
  
 **✓ faire** propriétés de type Boolean une expression affirmative \(`CanSeek` au lieu de `CantSeek`\). Si vous le souhaitez, vous pouvez également ajouter préfixe propriétés booléennes avec « Est », « peut » ou « A » mais uniquement lorsqu’il ajoute la valeur.  
  
 **✓ envisagez** donnant une propriété le même nom que son type.  
  
 Par exemple, la propriété suivante correctement Obtient et définit une valeur d’énumération nommée `Color`, de sorte que la propriété est nommée `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## Noms des événements  
 Événements font toujours référence à une action, un problème ou celui qui s’est produite. Par conséquent, comme avec les méthodes, les événements sont nommés avec des verbes et conjugaison de verbes est utilisé pour indiquer l’heure lorsque l’événement est déclenché.  
  
 **✓ faire** nommer des événements avec un verbe ou une phrase verbale.  
  
 Exemples `Clicked`, `Painting`, `DroppedDown`, et ainsi de suite.  
  
 **✓ faire** donner des noms d’événements avec un concept d’avant et après, en utilisant le présent et aux temps passé.  
  
 Par exemple, un événement de fermeture qui est déclenché avant la fermeture d’une fenêtre portera `Closing`, et qui est déclenché après la fermeture de la fenêtre est appelée `Closed`.  
  
 **X ne pas** utiliser « Before » ou « After » préfixes ou suffixes pour indiquer avant et après les événements. Utilisation actuelle et temps passé comme décrit ci\-dessus.  
  
 **✓ faire** nom de gestionnaires d’événements \(des délégués utilisés comme types d’événements\) du suffixe « EventHandler », comme illustré dans l’exemple suivant :  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ faire** utiliser deux paramètres nommés `sender` et `e` dans les gestionnaires d’événements.  
  
 Le paramètre sender représente l’objet qui a déclenché l’événement. Le paramètre d’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.  
  
 **✓ faire** nom événement classes argument avec le suffixe « EventArgs ».  
  
## Noms des champs  
 Les instructions d’affectation de noms de champ s’appliquent à des champs statiques publics et protégés. Les champs internes et privés ne sont pas couverts par les instructions et les champs d’instance publics ou protégés ne sont pas autorisées par le [règles de conception de membres](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ faire** utilisent la casse Pascal dans les noms de champ.  
  
 **✓ faire** nommer les champs à l’aide d’un nom, une expression nominale ou un adjectif.  
  
 **X ne pas** utiliser un préfixe pour les noms de champ.  
  
 Par exemple, n’utilisez pas « g\_ » ou « s\_ » pour indiquer les champs statiques.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)