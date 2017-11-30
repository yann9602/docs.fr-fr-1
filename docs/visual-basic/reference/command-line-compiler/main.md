---
title: /main
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2697b837a536b1b879196bd10843a2b76314747a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="main"></a><span data-ttu-id="88349-102">/main</span><span class="sxs-lookup"><span data-stu-id="88349-102">/main</span></span>
<span data-ttu-id="88349-103">Spécifie la classe ou le module qui contient la procédure `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="88349-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88349-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88349-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="88349-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="88349-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="88349-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="88349-106">Required.</span></span> <span data-ttu-id="88349-107">Qualification complète de la classe ou le module qui contient le `Sub Main` procédure qui est appelée lorsque le programme démarre.</span><span class="sxs-lookup"><span data-stu-id="88349-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="88349-108">Cela peut être sous la forme **présentée** ou **/main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="88349-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88349-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="88349-109">Remarks</span></span>  
 <span data-ttu-id="88349-110">Utilisez cette option lorsque vous créez un fichier exécutable ou un programme exécutable Windows.</span><span class="sxs-lookup"><span data-stu-id="88349-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="88349-111">Si le **/main** option est omise, le compilateur recherche partagé valide `Sub Main` dans tous les modules et les classes publiques.</span><span class="sxs-lookup"><span data-stu-id="88349-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="88349-112">Consultez [procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) pour en savoir plus sur les différentes formes de la `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="88349-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="88349-113">Lorsque `location` est une classe qui hérite de <xref:System.Windows.Forms.Form>, le compilateur fournit une valeur par défaut `Main` procédure qui démarre l’application si la classe n’a pas `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="88349-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="88349-114">Cela vous permet de compiler du code à la ligne de commande qui a été créée dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="88349-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="88349-115">Pour définir l’option /main dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="88349-115">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="88349-116">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="88349-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="88349-117">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="88349-117">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="88349-118">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="88349-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="88349-119">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="88349-119">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="88349-120">Assurez-vous que le **activer l’infrastructure d’application** case à cocher n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="88349-120">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="88349-121">Modifiez la valeur dans la **objet de démarrage** boîte.</span><span class="sxs-lookup"><span data-stu-id="88349-121">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88349-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="88349-122">Example</span></span>  
 <span data-ttu-id="88349-123">Le code suivant compile `T2.vb` et `T3.vb`, en spécifiant que le `Sub Main` procédure se trouve dans le `Test2` classe.</span><span class="sxs-lookup"><span data-stu-id="88349-123">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="88349-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88349-124">See Also</span></span>  
 [<span data-ttu-id="88349-125">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88349-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="88349-126">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88349-126">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="88349-127">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="88349-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="88349-128">NIB : Version de Visual Basic de Hello, World</span><span class="sxs-lookup"><span data-stu-id="88349-128">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="88349-129">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88349-129">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
