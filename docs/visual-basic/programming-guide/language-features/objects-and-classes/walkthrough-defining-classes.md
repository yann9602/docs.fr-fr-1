---
title: "Définition de Classes (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Procédure pas à pas : définition des classes (Visual Basic)
Cette procédure pas à pas montre comment définir des classes que vous pouvez ensuite utiliser pour créer des objets. Il vous montre comment ajouter des propriétés et méthodes pour la nouvelle classe et vous montre comment initialiser un objet.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a>Pour définir une classe  
  
1.  Créez un projet en cliquant sur **nouveau projet** sur la **fichier** menu. La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sélectionnez l’Application Windows à partir de la liste des [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour afficher le nouveau projet, les modèles de projet.  
  
3.  Ajoutez une nouvelle classe au projet en cliquant sur **ajouter une classe** sur la **projet** menu. La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
4.  Sélectionnez le **classe** modèle.  
  
5.  Nommez la nouvelle classe `UserNameInfo.vb`, puis cliquez sur **ajouter** pour afficher le code pour la nouvelle classe.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Vous pouvez utiliser la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **éditeur de Code** pour ajouter une classe à votre formulaire de démarrage en tapant le `Class` (mot clé), suivi du nom de la nouvelle classe. Le **éditeur de Code** fournit correspondante `End Class` instruction pour vous.  
  
6.  Définir un champ privé pour la classe en ajoutant le code suivant entre les `Class` et `End Class` instructions :  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Déclaration du champ comme `Private` signifie qu’il peut être utilisé uniquement dans la classe. Vous pouvez rendre les champs accessibles en dehors d’une classe à l’aide des modificateurs d’accès comme `Public` qui fournissent un accès plus. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Définissez une propriété pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Définissez une méthode pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Définir un constructeur paramétrable pour la nouvelle classe en ajoutant une procédure nommée `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     Le `Sub New` constructeur est appelé automatiquement lorsqu’un objet basé sur cette classe est créé. Ce constructeur définit la valeur du champ qui contient le nom d’utilisateur.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Pour créer un bouton pour tester la classe  
  
1.  Modifiez le formulaire de démarrage en mode design en cliquant sur son nom dans **l’Explorateur de solutions** , puis en cliquant sur **Concepteur de vue**. Par défaut, le formulaire de démarrage pour les projets d’Application Windows nommé Form1.vb. Le formulaire principal s’affiche alors.  
  
2.  Ajouter un bouton au formulaire principal et double-cliquez dessus pour afficher le code pour le `Button1_Click` Gestionnaire d’événements. Ajoutez le code suivant pour appeler la procédure de test :  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Pour exécuter votre application  
  
1.  Exécutez votre application en appuyant sur F5. Cliquez sur le bouton sur le formulaire pour appeler la procédure de test. Il affiche un message indiquant que l’original `UserName` est « MOORE, BOBBY », car la procédure appelée la `Capitalize` méthode de l’objet.  
  
2.  Cliquez sur **OK** pour fermer la boîte de message. Le `Button1 Click` procédure modifie la valeur de la `UserName` propriété et affiche un message indiquant que la nouvelle valeur de `UserName` est « Worden, Joe ».  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
