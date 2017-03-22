---
title: "Déclaration et déclenchement des événements (Visual Basic) | Documents Microsoft"
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 233673c1d42684b7caa9042d18fb341a1043a31b
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Procédure pas à pas : déclaration et déclenchement des événements (Visual Basic)
Cette procédure pas à pas montre comment déclarer et déclencher des événements pour une classe nommée `Widget`. Après avoir terminé les étapes, vous souhaiterez lire la rubrique connexe, [procédure pas à pas : gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), qui explique comment utiliser les événements du `Widget` objets à fournir des informations d’état dans une application.  
  
## <a name="the-widget-class"></a>La classe Widget  
 Envisageons pour l’instant que vous avez un `Widget` classe. Votre `Widget` classe a une méthode qui peut prendre beaucoup de temps à exécuter, et vous souhaitez que votre application puisse afficher une sorte d’indicateur d’achèvement.  
  
 Bien sûr, vous pouvez apporter les `Widget` objet affiche une boîte de dialogue de pourcentage d’achèvement, mais vous allaient être bloqués avec cette boîte de dialogue dans chaque projet dans lequel vous avez utilisé la `Widget` classe. Principe de design d’objets consiste à laisser l’application qui utilise un handle d’objet l’interface utilisateur, à moins que le but de l’objet consiste à gérer une formulaire ou boîte de dialogue.  
  
 L’objectif de `Widget` consiste à effectuer d’autres tâches, il est préférable d’ajouter un `PercentDone` événement et laisser la procédure qui appelle `Widget`de méthodes gèrent que des événements et afficher l’état de mises à jour. Le `PercentDone` événement peut également fournir un mécanisme d’annulation de la tâche.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Pour générer l’exemple de code pour cette rubrique  
  
1.  Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Application Windows de projet et créez un formulaire nommé `Form1`.  
  
2.  Ajoutez deux boutons et une étiquette à `Form1`.  
  
3.  Nommez les objets comme indiqué dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Tâche de démarrage|  
    |`Button2`|`Text`|Annuler|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Sur le **projet** menu, choisissez **ajouter une classe** pour ajouter une classe nommée `Widget.vb` au projet.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pour déclarer un événement pour la classe Widget  
  
-   Utilisez le `Event` (mot clé) pour déclarer un événement dans la `Widget` classe. Notez qu’un événement peut avoir `ByVal` et `ByRef` arguments, en tant que `Widget`de `PercentDone` illustre l’événement :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Lorsque l’objet appelant reçoit un `PercentDone` événement, le `Percent` argument contient le pourcentage de la tâche est terminée. Le `Cancel` argument peut être défini sur `True` pour annuler la méthode ayant déclenché l’événement.  
  
> [!NOTE]
>  Vous pouvez déclarer des arguments d’événement comme arguments de procédures, avec les exceptions suivantes : les événements ne peut pas avoir `Optional` ou `ParamArray` arguments et les événements n’ont pas de valeurs de retour.  
  
 Le `PercentDone` événement est déclenché par le `LongTask` procédé de la `Widget` classe. `LongTask`prend deux arguments : la durée pendant laquelle la méthode prétend être active et l’intervalle minimal avant `LongTask` suspendue pour déclencher le `PercentDone` événement.  
  
#### <a name="to-raise-the-percentdone-event"></a>Pour déclencher l’événement PercentDone  
  
1.  Pour simplifier l’accès à la `Timer` propriété utilisée par cette classe, ajoutez une `Imports` en haut de la section des déclarations de votre module de classe, au-dessus de la `Class Widget` instruction.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Ajoutez le code suivant à la classe `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n °&3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Lorsque votre application appelle la `LongTask` (méthode), la `Widget` classe déclenche le `PercentDone` événement chaque `MinimumInterval` secondes. Retourne l’événement `LongTask` vérifie si le `Cancel` argument a la valeur `True`.  
  
 Quelques mises en garde sont nécessaires. Pour plus de simplicité, le `LongTask` procédure suppose que vous connaissez à l’avance combien de temps prendra la tâche. C’est presque jamais le cas. Il peut être difficile de diviser les tâches en segments de même longueur et souvent essentiel pour les utilisateurs est simplement la quantité de temps qui s’écoule avant une indication que quelque chose qui se passe.  
  
 Vous avez peut-être remarqué une autre faille dans cet exemple. Le `Timer` propriété renvoie le nombre de secondes écoulées depuis minuit ; par conséquent, l’application reste bloquée si elle est démarrée juste avant minuit. Une approche plus prudente pour mesurer le temps serait prendre en considération les conditions de limite telles que cela, ou les éviter, à l’aide des propriétés telles que `Now`.  
  
 Maintenant que la `Widget` classe peut déclencher des événements, vous pouvez passer à la procédure suivante. [Procédure pas à pas : Gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) montre comment utiliser `WithEvents` pour associer un gestionnaire d’événements avec le `PercentDone` événement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [Procédure pas à pas : Gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)   
 [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)
