---
title: "Création et implémentation d’Interfaces (Visual Basic) | Documents Microsoft"
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
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
ms.openlocfilehash: 076bc8d33e97286c31f27a2016e39a25e9cec22c
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Procédure pas à pas : création et implémentation d'interfaces (Visual Basic)
Les interfaces décrivent les caractéristiques des propriétés, méthodes et événements, mais laissent les détails d’implémentation aux structures ou classes.  
  
 Cette procédure pas à pas montre comment déclarer et implémenter une interface.  
  
> [!NOTE]
>  Cette procédure pas à pas ne fournit pas d’informations sur la création d’une interface utilisateur.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a>Pour définir une interface  
  
1.  Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet d’Application Windows.  
  
2.  Ajoutez un nouveau module au projet en cliquant sur **ajouter un Module** sur la **projet** menu.  
  
3.  Nommez le nouveau module `Module1.vb` sur **ajouter**. Le code pour le nouveau module s’affiche.  
  
4.  Définissez une interface nommée `TestInterface` dans `Module1` en tapant `Interface TestInterface` entre les `Module` et `End Module` instructions et appuyez sur ENTRÉE. Le **éditeur de Code** en retrait le `Interface` (mot clé) et ajoute une `End Interface` instruction pour former un bloc de code.  
  
5.  Définir une propriété, une méthode et un événement pour l’interface en insérant le code suivant entre les `Interface` et `End Interface` instructions :  
  
     [!code-vb[VbVbalrOOP&#98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>Implémentation  
 Vous pouvez remarquer que la syntaxe utilisée pour déclarer des membres d’interface est différente de la syntaxe utilisée pour déclarer des membres de classe. Cette différence reflète le fait que les interfaces ne peuvent pas contenir de code d’implémentation.  
  
#### <a name="to-implement-the-interface"></a>Pour implémenter l’interface  
  
1.  Ajoutez une classe nommée `ImplementationClass` en ajoutant l’instruction suivante aux `Module1`, après le `End Interface` instruction, mais avant la `End Module` instruction et appuyez sur ENTRÉE :  
  
     [!code-vb[VbVbalrOOP&#99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     Si vous travaillez dans l’environnement de développement intégré, le **éditeur de Code** fournit une mise en correspondance `End Class` instruction lorsque vous appuyez sur ENTRÉE.  
  
2.  Ajoutez le code suivant `Implements` instruction `ImplementationClass`, qui nomme l’interface que la classe implémente :  
  
     [!code-vb[100 VbVbalrOOP](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     Lorsque indiqués séparément des autres éléments en haut d’une classe ou une structure, la `Implements` instruction indique que la classe ou structure implémente une interface.  
  
     Si vous travaillez dans l’environnement de développement intégré, le **éditeur de Code** implémente les membres de classe requis par `TestInterface` lorsque vous appuyez sur entrée, et vous pouvez ignorer l’étape suivante.  
  
3.  Si vous ne travaillez pas dans l’environnement de développement intégré, vous devez implémenter tous les membres de l’interface `MyInterface`. Ajoutez le code suivant à `ImplementationClass` pour implémenter `Event1`, `Method1`, et `Prop1`:  
  
     [!code-vb[VbVbalrOOP&#101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     La `Implements` instruction nomme l’interface et le membre d’interface implémenté.  
  
4.  Complétez la définition de `Prop1` en ajoutant un champ privé à la classe qui a stocké la valeur de propriété :  
  
     [!code-vb[VbVbalrOOP&#102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     Retourne la valeur de la `pval` à partir de la propriété accesseur get.  
  
     [!code-vb[VbVbalrOOP&#103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     Définissez la valeur de `pval` dans la propriété accesseur set.  
  
     [!code-vb[VbVbalrOOP&#104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  Complétez la définition de `Method1` en ajoutant le code suivant.  
  
     [!code-vb[VbVbalrOOP&#105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>Pour tester l’implémentation de l’interface  
  
1.  Avec le bouton droit de l’écran de démarrage pour votre projet dans le **l’Explorateur de solutions**, puis cliquez sur **afficher le Code**. L’éditeur affiche la classe de votre formulaire de démarrage. Par défaut, le formulaire de démarrage est appelé `Form1`.  
  
2.  Ajoutez le code suivant `testInstance` champ la `Form1` classe :  
  
     [!code-vb[VbVbalrOOP&#120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     En déclarant `testInstance` en tant que `WithEvents`, la `Form1` classe peut traiter ses événements.  
  
3.  Ajoutez le Gestionnaire d’événements suivant à la `Form1` classe pour gérer les événements déclenchés par `testInstance`:  
  
     [!code-vb[VbVbalrOOP&#106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  Ajoutez une sous-routine nommée `Test` à la `Form1` classe à tester la classe d’implémentation :  
  
     [!code-vb[VbVbalrOOP&#107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     Le `Test` procédure crée une instance de la classe qui implémente `MyInterface`, attribue cette instance vers le `testInstance` champ, définit une propriété et exécute une méthode via l’interface.  
  
5.  Ajoutez du code pour appeler le `Test` procédure à partir de la `Form1 Load` procédure de votre formulaire de démarrage :  
  
     [!code-vb[VbVbalrOOP&#108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  Exécuter le `Test` procédure en appuyant sur F5. Le message « Prop1 a été définie à 9 » s’affiche. Après avoir cliqué sur OK, le message « The X parameter for Method1 est 5 » s’affiche. Cliquez sur OK, le message « le Gestionnaire d’événements interceptée l’événement » s’affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Implements (instruction)](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Interface, instruction](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Event (instruction)](../../../../visual-basic/language-reference/statements/event-statement.md)

