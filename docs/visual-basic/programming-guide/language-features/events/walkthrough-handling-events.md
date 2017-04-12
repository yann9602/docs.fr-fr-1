---
title: "La gestion des événements (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17cd0bddbe8c89cf60e19f3f2af6f448ad465d70
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a>Procédure pas à pas : gestion des événements (Visual Basic)
Il s’agit de la deuxième des deux rubriques qui montrent comment utiliser des événements. La première rubrique, [procédure pas à pas : déclaration et déclenchement des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), montre comment déclarer et déclencher des événements. Cette section utilise le formulaire et la classe à partir de cette procédure pas à pas pour montrer comment gérer les événements lorsqu’ils se produisent.  
  
 Le `Widget` exemple de classe utilise des instructions de gestion des événements traditionnelles. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fournit d’autres techniques pour l’utilisation des événements. En guise d’exercice, vous pouvez modifier cet exemple montre comment utiliser le `AddHandler` et `Handles` instructions.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pour gérer l’événement PercentDone de la classe Widget  
  
1.  Placez le code suivant dans `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     Le `WithEvents` (mot clé) Spécifie que la variable `mWidget` est utilisée pour gérer les événements d’un objet. Vous spécifiez le type d’objet en fournissant le nom de la classe à partir duquel l’objet sera créé.  
  
     La variable `mWidget` est déclarée dans `Form1` car `WithEvents` variables doivent être de niveau classe. Cela est vrai quel que soit le type de classe que vous les placez dans.  
  
     La variable `mblnCancel` est utilisée pour annuler le `LongTask` (méthode).  
  
## <a name="writing-code-to-handle-an-event"></a>Écriture de Code pour gérer un événement  
 Dès que vous déclarez une variable à l’aide `WithEvents`, le nom de la variable s’affiche dans la liste déroulante gauche de la classe **éditeur de Code**. Lorsque vous sélectionnez `mWidget`, le `Widget` événements de la classe apparaissent dans la liste déroulante à droite. Sélection d’un événement affiche la procédure d’événement correspondante, avec le préfixe `mWidget` et un trait de soulignement. Toutes les procédures d’événement associés à une `WithEvents` variable portent le nom de variable comme préfixe.  
  
#### <a name="to-handle-an-event"></a>Pour gérer un événement  
  
1.  Sélectionnez `mWidget` dans la liste déroulante dans le **éditeur de Code**.  
  
2.  Sélectionnez le `PercentDone` événement dans la liste déroulante à droite. Le **éditeur de Code** ouvre le `mWidget_PercentDone` procédure d’événement.  
  
    > [!NOTE]
    >  Le **éditeur de Code** est utile, mais pas obligatoire, pour l’insertion de nouveaux gestionnaires d’événements. Dans cette procédure pas à pas, il est plus rapide de copier simplement les gestionnaires d’événements directement dans votre code.  
  
3.  Ajoutez le code suivant au gestionnaire d'événements `mWidget_PercentDone` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     Chaque fois que le `PercentDone` événement est déclenché, la procédure événementielle affiche le pourcentage d’achèvement dans un `Label` contrôle. Le `DoEvents` méthode autorise l’étiquette soit repeinte et donne également à l’utilisateur la possibilité de cliquer sur le **Annuler** bouton.  
  
4.  Ajoutez le code suivant pour le `Button2_Click` Gestionnaire d’événements :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 Si l’utilisateur clique sur le **Annuler** tout en `LongTask` est en cours d’exécution, le `Button2_Click` événement est exécuté dès que la `DoEvents` instruction permet le traitement de l’événement. La variable de niveau classe `mblnCancel` est défini sur `True`et le `mWidget_PercentDone` événement, puis le teste et définit les `ByRef Cancel` l’argument de `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Connexion d’une Variable WithEvents à un objet  
 `Form1`est désormais configuré pour gérer un `Widget` événements de l’objet. Ne reste qu’à trouver un `Widget` quelque part.  
  
 Lorsque vous déclarez une variable `WithEvents` au moment du design, aucun objet ne lui n’est associé. A `WithEvents` variable est qu’une variable objet parmi les autres. Vous devez créer un objet et lui assigner une référence à l’aide du `WithEvents` variable.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Pour créer un objet et lui assigner une référence à celui-ci  
  
1.  Sélectionnez **(Form1 Events)** dans la liste déroulante dans le **éditeur de Code**.  
  
2.  Sélectionnez le `Load` événement dans la liste déroulante à droite. Le **éditeur de Code** ouvre le `Form1_Load` procédure d’événement.  
  
3.  Ajoutez le code suivant pour le `Form1_Load` procédure d’événement pour créer le `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 Lorsque ce code s’exécute, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] crée un `Widget` de l’objet et associe ses événements aux procédures événementielles avec `mWidget`. Partir de ce point, chaque fois que le `Widget` déclenche son `PercentDone` événement, le `mWidget_PercentDone` procédure événementielle est exécutée.  
  
#### <a name="to-call-the-longtask-method"></a>Pour appeler la méthode LongTask  
  
-   Ajoutez le code suivant au gestionnaire d'événements `Button1_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 Avant du `LongTask` méthode est appelée, l’étiquette qu’affiche le pourcentage d’achèvement doit être initialisé et niveau de la classe `Boolean` indicateur pour l’annulation de la méthode doit être définie sur `False`.  
  
 `LongTask`est appelé avec une durée de la tâche étant de 12,2 secondes. Le `PercentDone` événement est déclenché une fois tous les tiers de seconde. Chaque fois que l’événement est déclenché, le `mWidget_PercentDone` procédure événementielle est exécutée.  
  
 Lors de la `LongTask` terminée, `mblnCancel` est testé pour voir si `LongTask` s’est terminée normalement, ou si elle s’est arrêté car `mblnCancel` a été défini sur `True`. Le pourcentage d’achèvement est mis à jour uniquement dans le premier cas.  
  
#### <a name="to-run-the-program"></a>Pour exécuter le programme  
  
1.  Appuyez sur F5 pour passer le projet en cours d’exécution.  
  
2.  Cliquez sur le **démarrer la tâche** bouton. Chaque fois que le `PercentDone` événement est déclenché, l’étiquette est mise à jour avec le pourcentage de la tâche est terminée.  
  
3.  Cliquez sur le **Annuler** bouton Arrêter la tâche. Notez que l’apparence de la **Annuler** bouton ne change pas immédiatement lorsque vous cliquez dessus. Le `Click` événement ne peut pas se produire jusqu'à ce que la `My.Application.DoEvents` instruction permet le traitement des événements.  
  
    > [!NOTE]
    >  Le `My.Application.DoEvents` méthode ne traite pas les événements de la même manière que le formulaire. Par exemple, dans cette procédure pas à pas, vous devez cliquer sur le **Annuler** bouton deux fois. Pour permettre au formulaire de gérer les événements directement, vous pouvez utiliser le multithreading. Pour plus d’informations, consultez [thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
 Il peut s’avérer intéressant d’exécuter le programme en appuyant sur F11 pour parcourir le code une ligne à la fois. Vous pouvez voir clairement comment l’exécution passe `LongTask`et puis repasse brièvement dans `Form1` chaque fois que le `PercentDone` événement est déclenché.  
  
 Que se passerait-il si, alors que l’exécution a été dans le code de `Form1`, la `LongTask` méthode était de nouveau appelée ? Au pire, un débordement de pile peut se produire si `LongTask` appelées chaque fois que l’événement a été déclenché.  
  
 Vous pouvez provoquer la variable `mWidget` pour gérer les événements d’un autre `Widget` objet en assignant une référence à la nouvelle `Widget` à `mWidget`. En fait, vous pouvez rendre le code dans `Button1_Click` cette opération chaque fois que vous cliquez sur le bouton.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Pour gérer les événements pour un autre objet widget  
  
-   Ajoutez la ligne suivante de code pour le `Button1_Click` procédure, juste avant la ligne `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 Le code ci-dessus crée un `Widget` chaque fois que le bouton est activé. Dès que la `LongTask` méthode se termine, la référence à la `Widget` est libéré et le `Widget` est détruit.  
  
 A `WithEvents` variable peut contenir uniquement une référence d’objet à la fois, donc si vous affectez une autre `Widget` objet `mWidget`, du précédent `Widget` événements d’objet seront n’est plus gérées. Si `mWidget` est la seule variable objet qui contient une référence à l’ancien `Widget`, l’objet est détruit. Si vous souhaitez gérer des événements de plusieurs `Widget` objets, utilisez la `AddHandler` instruction de traitement des événements de chaque objet séparément.  
  
> [!NOTE]
>  Vous pouvez déclarer autant `WithEvents` les variables que vous avez besoin, mais les tableaux de `WithEvents` variables ne sont pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Déclaration et déclenchement des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)   
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
