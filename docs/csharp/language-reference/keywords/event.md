---
title: "event (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "event"
  - "remove"
  - "event_CSharpKeyword"
  - "add"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "event (mot clé C#)"
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# event (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `event` est utilisé pour déclarer un événement dans une classe d'éditeur.  
  
## Exemple  
 L'exemple suivant montre comment déclarer et déclencher un événement qui utilise <xref:System.EventHandler> comme type délégué sous\-jacent.  Pour obtenir l'exemple de code complet qui illustre aussi comment utiliser le type délégué générique <xref:System.EventHandler%601> et comment s'abonner à un événement et créer une méthode de gestionnaire d'événements, consultez [Comment : publier des événements conformes aux indications du .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]  
  
 Les événements constituent un type spécial de délégué multicast qui peut uniquement être appelé au sein de la classe ou de la structure où ils sont déclarés \(la classe d'éditeur\).  Si d'autres classes ou structures s'abonnent à l'événement, leurs méthodes de gestionnaire d'événements sont appelées lorsque la classe d'éditeur déclenche l'événement.  Pour plus d'informations et d'exemples de code, consultez [Événements](../../../csharp/programming-guide/events/index.md) et [Délégués](../../../csharp/programming-guide/delegates/index.md).  
  
 Les événements peuvent être marqués comme étant [publics](../../../csharp/language-reference/keywords/public.md), [privés](../../../csharp/language-reference/keywords/private.md), [protégés](../../../csharp/language-reference/keywords/protected.md), [internes](../../../csharp/language-reference/keywords/internal.md) ou  `protected` `internal`.  Ces modificateurs d'accès définissent comment les utilisateurs de la classe peuvent accéder à l'événement.  Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## Mots clés et événements  
 Les mots clés suivants s'appliquent aux événements.  
  
|Mot clé|Description|Pour plus d'informations|  
|-------------|-----------------|------------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Rend l'événement disponible aux appelants à tout instant, même si aucune instance de la classe n'existe.|[Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Permet aux classes dérivées de substituer le comportement de l'événement à l'aide du mot clé [override](../../../csharp/language-reference/keywords/override.md).|[Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Spécifie que pour les classes dérivées le comportement n'est plus virtuel.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Le compilateur ne génère pas les blocs d'accesseurs d'événement `add` et `remove`, et par conséquent, les classes dérivées doivent fournir leur propre implémentation.||  
  
 Un événement peut être déclaré comme un événement statique à l'aide du mot clé [static](../../../csharp/language-reference/keywords/static.md).  Cela rend l'événement disponible aux appelants à tout moment, même si aucune instance de la classe n'existe.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Un événement peut être marqué comme événement virtuel à l'aide du mot clé [virtual](../../../csharp/language-reference/keywords/virtual.md).  Les classes dérivées peuvent ainsi substituer le comportement de l'événement à l'aide du mot clé [override](../../../csharp/language-reference/keywords/override.md).  Pour plus d'informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  Un événement qui se substitue à un événement virtuel peut également être [sealed](../../../csharp/language-reference/keywords/sealed.md), ce qui spécifie que pour les classes dérivées elle n'est plus virtuelle.  Enfin, un événement peut être déclaré [abstrait](../../../csharp/language-reference/keywords/abstract.md), ce qui signifie que le compilateur ne génère pas les blocs d'accesseurs d'événement `add` et `remove`.  Par conséquent, les classes dérivées doivent fournir leur propre implémentation.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [ajouter](../../../csharp/language-reference/keywords/add.md)   
 [supprimer](../../../csharp/language-reference/keywords/remove.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [Comment : combiner des délégués \(délégués multicast\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)