---
title: "Walkthrough: Handling Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "event handling [Visual Basic], walkthroughs"
  - "walkthroughs [Visual Basic], event handling"
  - "variables [Visual Basic], WithEvents"
  - "events [Visual Basic], walkthroughs"
  - "WithEvents keyword, walkthroughs"
  - "event handlers [Visual Basic], walkthroughs"
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Walkthrough: Handling Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique est la deuxième des deux rubriques consacrées à la manipulation des événements.  La première rubrique, [Procédure pas à pas : déclaration et déclenchement des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), explique comment déclarer et déclencher des événements.  La présente section utilise le formulaire et la classe de la première procédure pas à pas pour montrer comment gérer les événements lorsqu'ils se produisent.  
  
 L'exemple de classe `Widget` utilise des instructions de gestion des événements traditionnelles.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit d'autres techniques pour l'utilisation des événements.  En guise d'exercice, vous pouvez modifier cet exemple de façon à utiliser des instructions `AddHandler` et `Handles`.  
  
### Pour gérer l'événement PercentDone de la classe Widget  
  
1.  Tapez le code suivant dans `Form1` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#4)]  
  
     Le mot clé `WithEvents` spécifie que la variable `mWidget` est utilisée pour gérer les événements d'un objet.  Pour spécifier le type d'objet, vous devez fournir le nom de la classe à partir de laquelle cet objet sera créé.  
  
     La variable `mWidget` est déclarée dans `Form1` parce que les variables `WithEvents` doivent être de niveau classe.  Cela est vrai quel que soit le type de classe dans lequel vous les placez.  
  
     La variable `mblnCancel` est employée pour annuler la méthode `LongTask`.  
  
## Écriture de code pour la gestion d'un événement  
 Dès que vous déclarez une variable à l'aide de `WithEvents`, le nom de la variable apparaît dans la zone de liste déroulante de gauche dans l'**éditeur de code** de la classe.  Quand vous sélectionnez `mWidget`, les événements de la classe `Widget` apparaissent dans la zone de liste déroulante de droite.  Si vous sélectionnez un événement, la procédure événementielle correspondante s'affiche, avec le préfixe `mWidget` et un caractère de soulignement.  Toutes les procédures événementielles associées à une variable `WithEvents` reçoivent comme préfixe le nom de la variable.  
  
#### Pour gérer un événement  
  
1.  Sélectionnez `mWidget` dans la zone de liste déroulante de gauche dans l'**éditeur de code**.  
  
2.  Sélectionnez l'événement `PercentDone` dans la zone de liste déroulante de droite.  L'**éditeur de code** ouvre la procédure événementielle `mWidget_PercentDone`.  
  
    > [!NOTE]
    >  L'**éditeur de code** est utile, mais pas obligatoire, pour l'insertion de nouveaux gestionnaires d'événements.  Dans cette procédure pas à pas, il est plus rapide de copier simplement les gestionnaires d'événements directement dans votre code.  
  
3.  Ajoutez le code suivant au gestionnaire d'événements `mWidget_PercentDone` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#5)]  
  
     Chaque fois que l'événement `PercentDone` est déclenché, la procédure événementielle affiche le pourcentage réalisé dans un contrôle `Label`.  La méthode `DoEvents` permet que l'étiquette soit repeinte et donne également à l'utilisateur la possibilité de cliquer sur le bouton **Annuler**.  
  
4.  Ajoutez le code suivant pour le gestionnaire d'événements `Button2_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#6)]  
  
 Si l'utilisateur clique sur le bouton **Annuler** pendant l'exécution de la méthode `LongTask`, l'événement `Button2_Click` est exécuté dès que l'instruction `DoEvents` permet le traitement de l'événement.  La variable de classe `mblnCancel` prend la valeur `True` ; l'événement `mWidget_PercentDone` la teste ensuite et assigne la valeur `True` à l'argument `ByRef Cancel`.  
  
## Association d'une variable WithEvents à un objet  
 `Form1` est désormais prêt à gérer les événements d'un objet `Widget`.  Il ne reste qu'à trouver un objet `Widget`.  
  
 Quand vous déclarez une variable `WithEvents` au moment du design, aucun objet n'est associé à celle\-ci.  Une variable `WithEvents` n'est qu'une variable objet parmi les autres.  Vous devez créer un objet et lui assigner une référence avec la variable `WithEvents`.  
  
#### Pour créer un objet et lui assigner une référence  
  
1.  Sélectionnez **\(Form1 Events\)** dans la zone de liste déroulante de gauche dans l'**éditeur de code**.  
  
2.  Sélectionnez l'événement `Load` dans la zone de liste déroulante de droite.  L'**éditeur de code** ouvre la procédure événementielle `Form1_Load`.  
  
3.  Ajoutez le code suivant pour la procédure événementielle `Form1_Load` afin de créer le `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#7)]  
  
 Lorsque ce code s'exécute, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] crée un objet `Widget` et associe ses événements aux procédures événementielles de `mWidget`.  À partir de ce moment, chaque fois que l'objet `Widget` déclenche son événement `PercentDone`, la procédure événementielle `mWidget_PercentDone` est exécutée.  
  
#### Pour appeler la méthode LongTask  
  
-   Ajoutez le code suivant au gestionnaire d'événements `Button1_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#8)]  
  
 Avant que la méthode `LongTask` ne soit appelée, l'étiquette qui affiche le pourcentage de réalisation doit être initialisée, et l'indicateur de classe `Boolean` utilisé pour l'annulation de la méthode doit avoir la valeur `False`.  
  
 La méthode `LongTask` est appelée, la durée de la tâche étant de 12,2 secondes.  L'événement `PercentDone` est déclenché tous les tiers de seconde.  À chaque déclenchement de l'événement, la procédure événementielle `mWidget_PercentDone` est exécutée.  
  
 Une fois la méthode `LongTask` terminée, la variable `mblnCancel` est testée pour déterminer si `LongTask` s'est terminée normalement ou si elle s'est arrêtée parce que `mblnCancel` avait la valeur `True`.  Le pourcentage de réalisation de la tâche est mis à jour seulement dans le premier cas.  
  
#### Pour exécuter le programme  
  
1.  Appuyez sur F5 pour passer le projet en mode exécution.  
  
2.  Cliquez sur le bouton **Start Task**.  Chaque fois que l'événement `PercentDone` est déclenché, l'étiquette est mise à jour de façon à afficher le pourcentage de tâche réalisé.  
  
3.  Cliquez sur le bouton **Cancel** pour arrêter la tâche.  Notez que l'apparence du bouton **Annuler** ne change pas immédiatement lorsque vous cliquez dessus.  L'événement `Click` ne peut pas se produire tant que l'instruction `My.Application.DoEvents` n'autorise pas le traitement de l'événement.  
  
    > [!NOTE]
    >  La méthode `My.Application.DoEvents` ne traite pas les événements exactement de la même manière que le formulaire.  Par exemple, dans cette procédure pas à pas, vous devez cliquer deux fois sur le bouton **Annuler**.  Pour permettre au formulaire de gérer les événements directement, vous pouvez utiliser le multithreading.  Pour plus d'informations, consultez [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Il peut se révéler intéressant d'exécuter le programme en appuyant sur F11 pour exécuter le code pas à pas, une ligne à la fois.  Vous verrez alors clairement comment l'exécution passe à la méthode `LongTask`, puis repasse brièvement dans `Form1` chaque fois que l'événement `PercentDone` est déclenché.  
  
 Que se passerait\-il si, une fois l'exécution de retour dans le code de `Form1`, la méthode `LongTask` était de nouveau appelée ?  Au pire, il pourrait y avoir un dépassement de capacité de la pile si la méthode `LongTask` était appelée à chaque déclenchement de l'événement.  
  
 Vous pouvez faire en sorte que la variable `mWidget` gère des événements d'un autre objet `Widget` en assignant à `mWidget` une référence au nouvel objet `Widget`.  En réalité, vous pouvez faire en sorte que le code de la procédure `Button1_Click` effectue cette opération chaque fois que vous cliquez sur ce bouton.  
  
#### Pour gérer les événements d'un autre objet Widget  
  
-   Ajoutez la ligne de code suivante à la procédure `Button1_Click`, juste avant la ligne `mWidget.LongTask(12.2, 0.33)` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#9)]  
  
 Le code ci\-dessus crée un nouvel objet `Widget` chaque fois que l'on clique sur le bouton.  Dès que la méthode `LongTask` s'achève, la référence à l'objet `Widget` est libérée et l'objet `Widget` est détruit.  
  
 Une variable `WithEvents` ne peut contenir qu'une seule référence d'objet à la fois. Dès lors, si vous assignez un autre objet `Widget` à `mWidget`, les événements de l'ancien objet `Widget` ne sont plus gérés.  Si `mWidget` est la seule variable objet qui contient une référence à l'ancien objet `Widget`, ce dernier est détruit.  Pour pouvoir gérer les événements de plusieurs objets `Widget`, utilisez l'instruction `AddHandler` qui permet de traiter séparément les événements de chaque objet.  
  
> [!NOTE]
>  Vous pouvez déclarer autant de variables `WithEvents` qu'il en faut, mais les tableaux de variables `WithEvents` ne sont pas pris en charge.  
  
## Voir aussi  
 [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)