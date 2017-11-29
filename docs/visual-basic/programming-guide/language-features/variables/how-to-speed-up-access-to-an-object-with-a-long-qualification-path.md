---
title: "Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="700a8-102">Comment : accélérer l’accès à un objet comportant un chemin d’accès de qualification long (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="700a8-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="700a8-103">Si vous accédez fréquemment à un objet qui requiert un chemin d’accès de qualification de plusieurs méthodes et propriétés, vous pouvez accélérer votre code en évitant de répéter le chemin d’accès de qualification.</span><span class="sxs-lookup"><span data-stu-id="700a8-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="700a8-104">Il existe deux façons, vous pouvez éviter de répéter le chemin d’accès de qualification.</span><span class="sxs-lookup"><span data-stu-id="700a8-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="700a8-105">Vous pouvez l’attribuer à une variable, ou vous pouvez l’utiliser dans un `With`... `End With` bloc.</span><span class="sxs-lookup"><span data-stu-id="700a8-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="700a8-106">Pour accélérer l’accès à un objet très qualifié en l’assignant à une variable</span><span class="sxs-lookup"><span data-stu-id="700a8-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="700a8-107">Déclarez une variable du type de l’objet auquel vous accédez fréquemment.</span><span class="sxs-lookup"><span data-stu-id="700a8-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="700a8-108">Spécifiez le chemin d’accès de qualification dans la partie de l’initialisation de la déclaration.</span><span class="sxs-lookup"><span data-stu-id="700a8-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="700a8-109">Utilisez la variable pour accéder aux membres de l’objet.</span><span class="sxs-lookup"><span data-stu-id="700a8-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="700a8-110">Pour accélérer l’accès à un objet très qualifié à l’aide de With... Bloc de fin avec</span><span class="sxs-lookup"><span data-stu-id="700a8-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="700a8-111">Placez le chemin d’accès de qualification dans un `With` instruction.</span><span class="sxs-lookup"><span data-stu-id="700a8-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="700a8-112">Accéder aux membres de l’objet à l’intérieur de la `With` bloquer, avant la `End With` instruction.</span><span class="sxs-lookup"><span data-stu-id="700a8-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="700a8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="700a8-113">See Also</span></span>  
 [<span data-ttu-id="700a8-114">Variables objets</span><span class="sxs-lookup"><span data-stu-id="700a8-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="700a8-115">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="700a8-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
