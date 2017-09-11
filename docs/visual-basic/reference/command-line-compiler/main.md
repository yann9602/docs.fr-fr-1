---
title: /main | Documents Microsoft
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
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
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
ms.openlocfilehash: 61aa78e131ba8903035f630a540f49848f1acd3f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="main"></a><span data-ttu-id="0991c-102">/main</span><span class="sxs-lookup"><span data-stu-id="0991c-102">/main</span></span>
<span data-ttu-id="0991c-103">Spécifie la classe ou le module qui contient le `Sub Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="0991c-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0991c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0991c-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="0991c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0991c-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="0991c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0991c-106">Required.</span></span> <span data-ttu-id="0991c-107">Une qualification complète de la classe ou le module qui contient le `Sub Main` appelé au démarrage du programme.</span><span class="sxs-lookup"><span data-stu-id="0991c-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="0991c-108">Cela peut être sous la forme **présentée** ou **/main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="0991c-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0991c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="0991c-109">Remarks</span></span>  
 <span data-ttu-id="0991c-110">Utilisez cette option lorsque vous créez un fichier exécutable ou un programme exécutable Windows.</span><span class="sxs-lookup"><span data-stu-id="0991c-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="0991c-111">Si le **/main** option est omise, le compilateur recherche partagé valide `Sub Main` dans tous les modules et les classes publiques.</span><span class="sxs-lookup"><span data-stu-id="0991c-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="0991c-112">Consultez la page [procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) pour en savoir plus sur les différentes formes de la `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="0991c-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="0991c-113">Lors de la `location` est une classe qui hérite de <xref:System.Windows.Forms.Form>, le compilateur fournit une valeur par défaut `Main` procédure qui démarre l’application si la classe n’a pas `Main` procédure.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="0991c-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="0991c-114">Cela vous permet de compiler du code à la ligne de commande qui a été créée dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="0991c-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 <span data-ttu-id="0991c-115">[!code-vb[VbVbalrCompiler&#16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0991c-115">[!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span></span>  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="0991c-116">Pour définir /main dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="0991c-116">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="0991c-117">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="0991c-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0991c-118">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0991c-118">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="0991c-119">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="0991c-119">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="0991c-120">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="0991c-120">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="0991c-121">Assurez-vous que le **activer l’infrastructure d’application** case à cocher n’est pas activée.</span><span class="sxs-lookup"><span data-stu-id="0991c-121">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="0991c-122">Modifiez la valeur dans la **objet de démarrage** boîte.</span><span class="sxs-lookup"><span data-stu-id="0991c-122">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0991c-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="0991c-123">Example</span></span>  
 <span data-ttu-id="0991c-124">Le code suivant compile `T2.vb` et `T3.vb`, en spécifiant que la `Sub Main` procédure se trouve dans le `Test2` (classe).</span><span class="sxs-lookup"><span data-stu-id="0991c-124">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="0991c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0991c-125">See Also</span></span>  
 <span data-ttu-id="0991c-126">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0991c-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0991c-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="0991c-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="0991c-128"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="0991c-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="0991c-129"> [NIB : Version de Visual Basic Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span><span class="sxs-lookup"><span data-stu-id="0991c-129"> [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span></span>  
<span data-ttu-id="0991c-130"> [Procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="0991c-130"> [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span></span>
