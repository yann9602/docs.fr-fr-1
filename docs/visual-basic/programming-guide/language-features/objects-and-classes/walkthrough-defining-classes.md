---
title: "Walkthrough: Defining Classes (Visual Basic) | Microsoft Docs"
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
  - "execution, ending"
  - "objects [Visual Basic], initializing"
  - "Initialize event"
  - "files, closing"
  - "programs, quitting"
  - "code, exiting"
  - "objects [Visual Basic], creating"
  - "program termination"
  - "classes [Visual Basic], walkthroughs"
  - "class modules, walkthroughs"
  - "Terminate event"
  - "execution, stopping"
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Walkthrough: Defining Classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment définir des classes que vous pouvez ensuite utiliser pour créer des objets.  Elle montre également comment ajouter des propriétés et des méthodes à la nouvelle classe et illustre l'initialisation d'un objet.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour définir une classe  
  
1.  Créez un projet en cliquant sur **Nouveau projet** dans le menu **Fichier**.  La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sélectionnez Application Windows dans la liste des modèles de projet [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pour afficher le nouveau projet.  
  
3.  Ajoutez une nouvelle classe au projet en cliquant sur **Ajouter une classe** dans le menu **Projet**.  La boîte de dialogue **Ajouter un nouvel élément** s'affiche alors.  
  
4.  Sélectionnez le modèle **Classe**.  
  
5.  Nommez la nouvelle classe `UserNameInfo.vb`, puis cliquez sur **Ajouter** pour afficher le code de la nouvelle classe.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#5)]  
  
    > [!NOTE]
    >  Vous pouvez utiliser l'**éditeur de code** de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pour ajouter une classe à votre formulaire de démarrage en tapant le mot clé `Class`, suivi du nom de la nouvelle classe.  L'**éditeur de code** fournit une instruction `End Class` correspondante.  
  
6.  Définissez un champ privé pour la classe en ajoutant le code suivant entre les instructions `Class` et `End Class` :  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#7)]  
  
     La déclaration du champ comme `Private` signifie qu'il peut être utilisé uniquement dans la classe.  Vous pouvez rendre les champs disponibles à partir de l'extérieur d'une classe en utilisant des modificateurs d'accès qui fournissent un accès plus large, tel que l'accès `Public`.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Définissez une propriété pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#8)]  
  
8.  Définissez une méthode pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#9)]  
  
9. Définissez un constructeur paramétré pour la nouvelle classe en ajoutant une procédure nommée `Sub New` :  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#10)]  
  
     Le constructeur `Sub New` est appelé automatiquement lorsqu'un objet basé sur cette classe est créé.  Ce constructeur définit la valeur du champ qui contient le nom d'utilisateur.  
  
### Pour créer un bouton permettant de tester la classe  
  
1.  Modifiez le formulaire de démarrage en mode design en cliquant avec le bouton droit sur son nom dans l'**Explorateur de solutions**, puis en cliquant sur **Concepteur de vues**.  Par défaut, le formulaire de démarrage des projets d'application Windows est intitulé Form1.vb.  Le formulaire principal apparaît ensuite.  
  
2.  Ajoutez un bouton au formulaire principal et double\-cliquez dessus pour afficher le code du gestionnaire d'événements `Button1_Click`.  Ajoutez le code suivant pour appeler la procédure de test :  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#12)]  
  
### Pour exécuter l'application  
  
1.  Exécutez l'application en appuyant sur F5.  Cliquez sur le bouton situé sur votre formulaire pour appeler la procédure de test.  Elle affiche un message indiquant que le `UserName` d'origine est « MOORE, BOBBY », parce que la procédure a appelé la méthode `Capitalize` de l'objet.  
  
2.  Cliquez sur **OK** pour fermer le message.  La procédure `Button1 Click` modifie la valeur de la propriété `UserName` et affiche un message qui indique que la nouvelle valeur de `UserName` est « Worden, Joe ».  
  
## Voir aussi  
 [Programmation orientée objet dans Visual Basic](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)