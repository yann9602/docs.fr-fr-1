---
title: "Early and Late Binding (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "early binding"
  - "objects [Visual Basic], late-bound"
  - "objects [Visual Basic], early-bound"
  - "objects [Visual Basic], late bound"
  - "early binding, Visual Basic compiler"
  - "binding, late and early"
  - "objects [Visual Basic], early bound"
  - "Visual Basic compiler, early and late binding"
  - "late binding"
  - "late binding, Visual Basic compiler"
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Early and Late Binding (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] exécute un processus appelé `binding` lorsqu'un objet est assigné à une variable objet.  Un objet est à *liaison anticipée* \(early binding\) lorsqu'il est assigné à une variable déclarée comme étant d'un type d'objet spécifique.  Les objets à liaison anticipée permettent au compilateur d'allouer de la mémoire et d'effectuer d'autres optimisations avant l'exécution d'une application.  Par exemple, le fragment de code suivant déclare une variable comme étant du type <xref:System.IO.FileStream> :  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <xref:System.IO.FileStream> étant un type d'objet spécifique, l'instance assignée à `FS` fait l'objet d'une liaison anticipée.  
  
 Par opposition, un objet est à *liaison tardive* \(late binding\) lorsque cet objet est assigné à une variable déclarée comme étant du type `Object`.  Les objets de ce type peuvent contenir des références à n'importe quel objet, mais ne présentent pas nombre des avantages des objets à liaison anticipée.  Par exemple, le fragment de code suivant déclare une variable objet qui doit contenir un objet retourné par la fonction `CreateObject` :  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## Avantages de la liaison anticipée  
 Vous devez utiliser des objets à liaison anticipée chaque fois que cela est possible, car ils permettent au compilateur d'effectuer d'importantes optimisations, avec pour résultat des applications plus efficaces.  Ils sont beaucoup plus rapides que les objets à liaison tardive et facilitent la lecture et la gestion du code en indiquant avec exactitude les types d'objets utilisés.  La liaison anticipée présente également l'avantage d'activer des fonctionnalités utiles, telles que la saisie semi\-automatique du code et l'Aide dynamique, car l'environnement de développement intégré \(IDE, Integrated Development Environment\) [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] peut déterminer avec précision le type d'objet utilisé lorsque vous modifiez le code.  Elle réduit le nombre et la gravité des erreurs d'exécution en permettant au compilateur de signaler les erreurs lors de la compilation d'un programme.  
  
> [!NOTE]
>  La liaison tardive peut seulement être utilisée pour accéder à des membres de type déclarés comme `Public`.  L'accès à des membres déclarés comme `Friend` ou `Protected Friend` provoque une erreur d'exécution.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)