---
title: "Définition des Classes (Visual Basic) | Documents Microsoft"
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
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
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
ms.openlocfilehash: aeaa5c2bb85c1a642da15c6a29546cf065380e27
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a>Procédure pas à pas : définition des classes (Visual Basic)
Cette procédure pas à pas montre comment définir des classes que vous pouvez ensuite utiliser pour créer des objets. Il vous montre comment ajouter des propriétés et des méthodes à la nouvelle classe et vous montre comment initialiser un objet.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a>Pour définir une classe  
  
1.  Créer un projet en cliquant sur **nouveau projet** sur la **fichier** menu. La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sélectionnez Application Windows dans la liste des [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour afficher le nouveau projet de modèles de projet.  
  
3.  Ajoutez une nouvelle classe au projet en cliquant sur **ajouter une classe** sur la **projet** menu. Le **ajouter un nouvel élément** boîte de dialogue s’affiche.  
  
4.  Sélectionnez le **classe** modèle.  
  
5.  Nommez la nouvelle classe `UserNameInfo.vb`, puis cliquez sur **ajouter** pour afficher le code de la nouvelle classe.  
  
     [!code-vb[VbVbalrOOP n °&5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Vous pouvez utiliser la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **éditeur de Code** pour ajouter une classe à votre formulaire de démarrage en tapant le `Class` (mot clé), suivie du nom de la nouvelle classe. Le **éditeur de Code** fournit un correspondant `End Class` instruction pour vous.  
  
6.  Définissez un champ privé pour la classe en ajoutant le code suivant entre les `Class` et `End Class` instructions :  
  
     [!code-vb[VbVbalrOOP&#7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Déclaration du champ comme `Private` signifie qu’il peut être utilisé uniquement dans la classe. Vous pouvez rendre champs accessibles en dehors d’une classe à l’aide des modificateurs d’accès comme `Public` qui fournissent un accès plus. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Définir une propriété pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP n °&8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Définissez une méthode pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP&#9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Définissez un constructeur paramétré pour la nouvelle classe en ajoutant une procédure nommée `Sub New`:  
  
     [!code-vb[VbVbalrOOP&#10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     Le `Sub New` est appelé automatiquement lorsqu’un objet basé sur cette classe est créé. Ce constructeur définit la valeur du champ qui contient le nom d’utilisateur.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Pour créer un bouton pour tester la classe  
  
1.  Modifiez le formulaire de démarrage en mode design en double-cliquant sur son nom dans **l’Explorateur de solutions** , puis en cliquant sur **Concepteur de vues**. Par défaut, le formulaire de démarrage pour les projets d’Application Windows est intitulé Form1.vb. Le formulaire principal s’affiche alors.  
  
2.  Ajoutez un bouton au formulaire principal et double-cliquez dessus pour afficher le code pour le `Button1_Click` Gestionnaire d’événements. Ajoutez le code suivant pour appeler la procédure de test :  
  
     [!code-vb[VbVbalrOOP&#12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Pour exécuter votre application  
  
1.  Exécutez votre application en appuyant sur F5. Cliquez sur le bouton du formulaire pour appeler la procédure de test. Il affiche un message indiquant que l’original `UserName` est « MOORE, BOBBY », parce que la procédure appelée la `Capitalize` méthode de l’objet.  
  
2.  Cliquez sur **OK** pour fermer la boîte de message. Le `Button1 Click` procédure modifie la valeur de la `UserName` propriété et affiche un message indiquant que la nouvelle valeur de `UserName` est « Worden, Joe ».  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)   
 [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

