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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ef1ec16005bf0a7967d396054ae23c1023143c2a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="853a3-102">Procédure pas à pas : création et implémentation d'interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="853a3-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>
<span data-ttu-id="853a3-103">Les interfaces décrivent les caractéristiques des propriétés, méthodes et événements, mais laissent les détails d’implémentation aux structures ou classes.</span><span class="sxs-lookup"><span data-stu-id="853a3-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="853a3-104">Cette procédure pas à pas montre comment déclarer et implémenter une interface.</span><span class="sxs-lookup"><span data-stu-id="853a3-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="853a3-105">Cette procédure pas à pas ne fournit pas d’informations sur la création d’une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="853a3-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a><span data-ttu-id="853a3-106">Pour définir une interface</span><span class="sxs-lookup"><span data-stu-id="853a3-106">To define an interface</span></span>  
  
1.  <span data-ttu-id="853a3-107">Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet d’Application Windows.</span><span class="sxs-lookup"><span data-stu-id="853a3-107">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="853a3-108">Ajoutez un nouveau module au projet en cliquant sur **ajouter un Module** sur la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="853a3-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="853a3-109">Nommez le nouveau module `Module1.vb` sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="853a3-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="853a3-110">Le code pour le nouveau module s’affiche.</span><span class="sxs-lookup"><span data-stu-id="853a3-110">The code for the new module is displayed.</span></span>  
  
4.  <span data-ttu-id="853a3-111">Définissez une interface nommée `TestInterface` dans `Module1` en tapant `Interface TestInterface` entre les `Module` et `End Module` instructions et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="853a3-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="853a3-112">Le **éditeur de Code** en retrait le `Interface` (mot clé) et ajoute une `End Interface` instruction pour former un bloc de code.</span><span class="sxs-lookup"><span data-stu-id="853a3-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5.  <span data-ttu-id="853a3-113">Définir une propriété, une méthode et un événement pour l’interface en insérant le code suivant entre les `Interface` et `End Interface` instructions :</span><span class="sxs-lookup"><span data-stu-id="853a3-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     <span data-ttu-id="853a3-114">[!code-vb[VbVbalrOOP&#98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-114">[!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="853a3-115">Implémentation</span><span class="sxs-lookup"><span data-stu-id="853a3-115">Implementation</span></span>  
 <span data-ttu-id="853a3-116">Vous pouvez remarquer que la syntaxe utilisée pour déclarer des membres d’interface est différente de la syntaxe utilisée pour déclarer des membres de classe.</span><span class="sxs-lookup"><span data-stu-id="853a3-116">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="853a3-117">Cette différence reflète le fait que les interfaces ne peuvent pas contenir de code d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="853a3-117">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
#### <a name="to-implement-the-interface"></a><span data-ttu-id="853a3-118">Pour implémenter l’interface</span><span class="sxs-lookup"><span data-stu-id="853a3-118">To implement the interface</span></span>  
  
1.  <span data-ttu-id="853a3-119">Ajoutez une classe nommée `ImplementationClass` en ajoutant l’instruction suivante aux `Module1`, après le `End Interface` instruction, mais avant la `End Module` instruction et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="853a3-119">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     <span data-ttu-id="853a3-120">[!code-vb[VbVbalrOOP&#99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-120">[!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]</span></span>  
  
     <span data-ttu-id="853a3-121">Si vous travaillez dans l’environnement de développement intégré, le **éditeur de Code** fournit une mise en correspondance `End Class` instruction lorsque vous appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="853a3-121">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2.  <span data-ttu-id="853a3-122">Ajoutez le code suivant `Implements` instruction `ImplementationClass`, qui nomme l’interface que la classe implémente :</span><span class="sxs-lookup"><span data-stu-id="853a3-122">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     <span data-ttu-id="853a3-123">[!code-vb[100 VbVbalrOOP](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-123">[!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]</span></span>  
  
     <span data-ttu-id="853a3-124">Lorsque indiqués séparément des autres éléments en haut d’une classe ou une structure, la `Implements` instruction indique que la classe ou structure implémente une interface.</span><span class="sxs-lookup"><span data-stu-id="853a3-124">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="853a3-125">Si vous travaillez dans l’environnement de développement intégré, le **éditeur de Code** implémente les membres de classe requis par `TestInterface` lorsque vous appuyez sur entrée, et vous pouvez ignorer l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="853a3-125">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3.  <span data-ttu-id="853a3-126">Si vous ne travaillez pas dans l’environnement de développement intégré, vous devez implémenter tous les membres de l’interface `MyInterface`.</span><span class="sxs-lookup"><span data-stu-id="853a3-126">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="853a3-127">Ajoutez le code suivant à `ImplementationClass` pour implémenter `Event1`, `Method1`, et `Prop1`:</span><span class="sxs-lookup"><span data-stu-id="853a3-127">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     <span data-ttu-id="853a3-128">[!code-vb[VbVbalrOOP&#101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-128">[!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]</span></span>  
  
     <span data-ttu-id="853a3-129">La `Implements` instruction nomme l’interface et le membre d’interface implémenté.</span><span class="sxs-lookup"><span data-stu-id="853a3-129">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4.  <span data-ttu-id="853a3-130">Complétez la définition de `Prop1` en ajoutant un champ privé à la classe qui a stocké la valeur de propriété :</span><span class="sxs-lookup"><span data-stu-id="853a3-130">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     <span data-ttu-id="853a3-131">[!code-vb[VbVbalrOOP&#102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-131">[!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]</span></span>  
  
     <span data-ttu-id="853a3-132">Retourne la valeur de la `pval` à partir de la propriété accesseur get.</span><span class="sxs-lookup"><span data-stu-id="853a3-132">Return the value of the `pval` from the property get accessor.</span></span>  
  
     <span data-ttu-id="853a3-133">[!code-vb[VbVbalrOOP&#103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-133">[!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]</span></span>  
  
     <span data-ttu-id="853a3-134">Définissez la valeur de `pval` dans la propriété accesseur set.</span><span class="sxs-lookup"><span data-stu-id="853a3-134">Set the value of `pval` in the property set accessor.</span></span>  
  
     <span data-ttu-id="853a3-135">[!code-vb[VbVbalrOOP&#104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-135">[!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]</span></span>  
  
5.  <span data-ttu-id="853a3-136">Complétez la définition de `Method1` en ajoutant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="853a3-136">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     <span data-ttu-id="853a3-137">[!code-vb[VbVbalrOOP&#105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-137">[!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]</span></span>  
  
#### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="853a3-138">Pour tester l’implémentation de l’interface</span><span class="sxs-lookup"><span data-stu-id="853a3-138">To test the implementation of the interface</span></span>  
  
1.  <span data-ttu-id="853a3-139">Avec le bouton droit de l’écran de démarrage pour votre projet dans le **l’Explorateur de solutions**, puis cliquez sur **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="853a3-139">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="853a3-140">L’éditeur affiche la classe de votre formulaire de démarrage.</span><span class="sxs-lookup"><span data-stu-id="853a3-140">The editor displays the class for your startup form.</span></span> <span data-ttu-id="853a3-141">Par défaut, le formulaire de démarrage est appelé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="853a3-141">By default, the startup form is called `Form1`.</span></span>  
  
2.  <span data-ttu-id="853a3-142">Ajoutez le code suivant `testInstance` champ la `Form1` classe :</span><span class="sxs-lookup"><span data-stu-id="853a3-142">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     <span data-ttu-id="853a3-143">[!code-vb[VbVbalrOOP&#120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-143">[!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]</span></span>  
  
     <span data-ttu-id="853a3-144">En déclarant `testInstance` en tant que `WithEvents`, la `Form1` classe peut traiter ses événements.</span><span class="sxs-lookup"><span data-stu-id="853a3-144">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3.  <span data-ttu-id="853a3-145">Ajoutez le Gestionnaire d’événements suivant à la `Form1` classe pour gérer les événements déclenchés par `testInstance`:</span><span class="sxs-lookup"><span data-stu-id="853a3-145">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     <span data-ttu-id="853a3-146">[!code-vb[VbVbalrOOP&#106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-146">[!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]</span></span>  
  
4.  <span data-ttu-id="853a3-147">Ajoutez une sous-routine nommée `Test` à la `Form1` classe à tester la classe d’implémentation :</span><span class="sxs-lookup"><span data-stu-id="853a3-147">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     <span data-ttu-id="853a3-148">[!code-vb[VbVbalrOOP&#107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-148">[!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]</span></span>  
  
     <span data-ttu-id="853a3-149">Le `Test` procédure crée une instance de la classe qui implémente `MyInterface`, attribue cette instance vers le `testInstance` champ, définit une propriété et exécute une méthode via l’interface.</span><span class="sxs-lookup"><span data-stu-id="853a3-149">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5.  <span data-ttu-id="853a3-150">Ajoutez du code pour appeler le `Test` procédure à partir de la `Form1 Load` procédure de votre formulaire de démarrage :</span><span class="sxs-lookup"><span data-stu-id="853a3-150">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     <span data-ttu-id="853a3-151">[!code-vb[VbVbalrOOP&#108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="853a3-151">[!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]</span></span>  
  
6.  <span data-ttu-id="853a3-152">Exécuter le `Test` procédure en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="853a3-152">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="853a3-153">Le message « Prop1 a été définie à 9 » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="853a3-153">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="853a3-154">Après avoir cliqué sur OK, le message « The X parameter for Method1 est 5 » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="853a3-154">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="853a3-155">Cliquez sur OK, le message « le Gestionnaire d’événements interceptée l’événement » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="853a3-155">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853a3-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="853a3-156">See Also</span></span>  
 <span data-ttu-id="853a3-157">[Implements (instruction)](../../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="853a3-157">[Implements Statement](../../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="853a3-158"> [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="853a3-158"> [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md) </span></span>  
<span data-ttu-id="853a3-159"> [Interface, instruction](../../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="853a3-159"> [Interface Statement](../../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="853a3-160"> [Event (instruction)](../../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="853a3-160"> [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md)</span></span>

