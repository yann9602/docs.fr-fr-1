---
title: Variables objet dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="fd575-102">Variables objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd575-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="fd575-103">En plus de stockage direct de valeurs, une variable peut faire référence à un objet.</span><span class="sxs-lookup"><span data-stu-id="fd575-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="fd575-104">Vous assignez un objet à une variable pour les mêmes raisons que vous assignez une valeur à une variable :</span><span class="sxs-lookup"><span data-stu-id="fd575-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="fd575-105">Un nom de variable est souvent plus court et plus facile à retenir que le chemin d’accès complet de méthodes et propriétés nécessaires pour accéder à l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="fd575-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="fd575-106">À l’aide d’une variable qui fait référence à un objet est plus efficace qu’en accédant à plusieurs reprises de l’objet lui-même via les méthodes ou propriétés nécessaires.</span><span class="sxs-lookup"><span data-stu-id="fd575-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="fd575-107">Vous pouvez modifier une variable pour faire référence à d’autres objets pendant l’exécution de votre code.</span><span class="sxs-lookup"><span data-stu-id="fd575-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="fd575-108">Raccourcissement du code</span><span class="sxs-lookup"><span data-stu-id="fd575-108">Making Code Shorter</span></span>  
 <span data-ttu-id="fd575-109">Vous pouvez utiliser des variables objets pour réduire le code que vous devez taper.</span><span class="sxs-lookup"><span data-stu-id="fd575-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="fd575-110">L’exemple suivant utilise le chemin d’accès complet de méthodes et propriétés pour accéder à un <xref:System.Windows.Forms.Control> objet.</span><span class="sxs-lookup"><span data-stu-id="fd575-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="fd575-111">Vous pouvez réduire ce code et accélérer l’exécution, si vous utilisez une variable objet pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fd575-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="fd575-112">Vous devez déclarer la variable objet avec la classe spécifique que vous prévoyez d’affecter à ce dernier (`Control` dans ce cas).</span><span class="sxs-lookup"><span data-stu-id="fd575-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="fd575-113">Une fois que vous assignez un objet à la variable, vous pouvez traiter il d’exactement comme l’objet auquel il fait référence.</span><span class="sxs-lookup"><span data-stu-id="fd575-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="fd575-114">Vous pouvez définir ou récupérer les propriétés de l’objet ou utiliser une de ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="fd575-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="fd575-115">L’exemple suivant utilise une variable objet pour simplifier le code dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="fd575-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd575-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd575-116">See Also</span></span>  
 [<span data-ttu-id="fd575-117">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="fd575-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="fd575-118">Guide pratique : accélérer l’accès à un objet comportant un chemin d’accès de qualification long</span><span class="sxs-lookup"><span data-stu-id="fd575-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="fd575-119">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="fd575-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="fd575-120">Assignation des variables objets</span><span class="sxs-lookup"><span data-stu-id="fd575-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="fd575-121">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="fd575-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
