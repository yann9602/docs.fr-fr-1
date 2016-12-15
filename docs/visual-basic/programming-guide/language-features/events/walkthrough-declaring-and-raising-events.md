---
title: "Walkthrough: Declaring and Raising Events (Visual Basic) | Microsoft Docs"
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
  - "declarations, events"
  - "events [Visual Basic], walkthroughs"
  - "declaring events, walkthroughs"
  - "events [Visual Basic], declaring"
  - "events [Visual Basic], raising"
  - "raising events, walkthroughs"
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Declaring and Raising Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette procédure pas à pas explique comment déclarer et déclencher des événements pour une classe nommée `Widget`.  Après avoir réalisé les diverses étapes de la procédure, il peut s'avérer utile de lire la rubrique connexe, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), qui montre comment utiliser des événements à partir d'objets `Widget` afin de fournir des informations d'état dans une application.  
  
## Classe Widget  
 Envisageons pour l'instant une classe du nom de `Widget`.  Votre classe `Widget` comprend une méthode qui peut prendre du temps à s'exécuter, et vous voulez que votre application puisse afficher une sorte d'indicateur d'achèvement de cette tâche.  
  
 Il est clair que vous pourriez faire en sorte que l'objet `Widget` affiche une boîte de dialogue indiquant le pourcentage de réalisation de l'opération, mais cette boîte de dialogue apparaîtrait alors systématiquement dans tous les projets dans lesquels la classe `Widget` a été utilisée.  Un principe utile à suivre en matière de design d'objets consiste à laisser l'application qui utilise un objet le soin de gérer l'interface utilisateur, à moins que l'objectif général de l'objet soit de gérer un formulaire ou une boîte de dialogue.  
  
 `Widget` a pour objectif d'effectuer d'autres tâches, c'est pourquoi il est préférable d'ajouter un événement `PercentDone` et de laisser à la procédure qui appelle les méthodes de la classe `Widget` le soin de gérer cet événement et d'afficher des mises à jour d'état.  L'événement `PercentDone` peut également fournir un mécanisme d'annulation de la tâche.  
  
#### Pour créer l'exemple de code de cette rubrique  
  
1.  Ouvrez un nouveau projet Application Windows [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], puis créez un formulaire nommé `Form1`.  
  
2.  Ajoutez deux boutons et une étiquette à `Form1`.  
  
3.  Nommez les objets de la façon indiquée dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |-----------|---------------|---------------|  
    |`Button1`|`Text`|Start Task|  
    |`Button2`|`Text`|Cancel|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Dans le menu **Projet**, sélectionnez **Ajouter une classe** pour ajouter une classe nommée `Widget.vb` au projet.  
  
#### Pour déclarer un événement pour la classe Widget  
  
-   Utilisez le mot clé `Event` pour déclarer un événement dans la classe `Widget`.  Notez qu'un événement peut comporter des arguments `ByVal` et `ByRef`, comme l'illustre l'événement `PercentDone` de `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Lorsque l'objet appelant reçoit un événement `PercentDone`, l'argument `Percent` contient le pourcentage de tâche réalisé.  L'argument `Cancel` peut avoir la valeur `True` pour annuler la méthode ayant déclenché l'événement.  
  
> [!NOTE]
>  Vous pouvez déclarer des arguments d'événement de la même manière que pour les arguments de procédures, avec toutefois les exceptions suivantes : les événements ne peuvent pas avoir d'arguments `Optional`, `ParamArray`, ni de valeur de retour.  
  
 L'événement `PercentDone` est déclenché par la méthode `LongTask` de la classe `Widget`.  `LongTask` accepte deux arguments :  la durée pendant laquelle la méthode prétend être active et l'intervalle de temps minimal requis avant que la méthode `LongTask` ne soit suspendue pour déclencher l'événement `PercentDone`.  
  
#### Pour déclencher l'événement PercentDone  
  
1.  Pour simplifier l'accès à la propriété `Timer` utilisée par cette classe, ajoutez une instruction `Imports` en haut de la section des déclarations de votre module de classe, au\-dessus de l'instruction `Class Widget`.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Ajoutez le code suivant à la classe `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Lorsque votre application appelle la méthode `LongTask`, la classe `Widget` déclenche l'événement `PercentDone` chaque `MinimumInterval` seconde.  Lorsque l'événement est retourné, la méthode `LongTask` contrôle si l'argument `Cancel` avait la valeur `True`.  
  
 Quelques mises en garde s'imposent toutefois à ce stade.  Pour des raisons de simplicité, la procédure `LongTask` suppose que vous connaissez au préalable le temps que va durer la tâche,  ce qui n'est pratiquement jamais le cas.  Il peut être difficile de diviser les tâches en segments de même longueur et, la plupart du temps, l'information qui compte le plus aux yeux des utilisateurs est simplement le temps qui s'écoule avant qu'ils ne voient s'afficher un message indiquant que quelque chose se produit.  
  
 Il se peut que vous ayez remarqué une autre faille dans cet exemple.  La propriété `Timer` retourne le nombre de secondes écoulées depuis minuit, c'est pourquoi l'application se bloque si elle est démarrée juste avant minuit.  Une approche plus prudente pour la mesure du temps consisterait à prendre en compte des conditions de limite telles que celle\-ci ou éviter purement et simplement qu'elles n'utilisent des propriétés telles que `Now`.  
  
 Maintenant que la classe `Widget` peut déclencher des événements, vous pouvez passer à la procédure pas à pas suivante.  [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) montre comment utiliser `WithEvents` pour associer un gestionnaire d'événements à l'événement `PercentDone`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)