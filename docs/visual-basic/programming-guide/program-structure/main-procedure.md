---
title: "Procédure Main dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="e9526-102">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9526-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="e9526-103">Toutes les applications Visual Basic doivent contenir une procédure appelée `Main`.</span><span class="sxs-lookup"><span data-stu-id="e9526-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="e9526-104">Cette procédure sert de point de départ et contrôle général pour votre application.</span><span class="sxs-lookup"><span data-stu-id="e9526-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="e9526-105">Le .NET Framework appelle votre `Main` procédure lorsqu’il a chargé votre application et est prêt à passer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e9526-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="e9526-106">Sauf si vous créez une application Windows Forms, vous devez écrire le `Main` procédure pour les applications qui s’exécutent sur leurs propres.</span><span class="sxs-lookup"><span data-stu-id="e9526-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="e9526-107">`Main`contient le code qui s’exécute en premier.</span><span class="sxs-lookup"><span data-stu-id="e9526-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="e9526-108">Dans `Main`, vous pouvez déterminer quel formulaire doit d’abord être chargé au démarrage du programme, savoir si une copie de votre application est déjà en cours d’exécution sur le système, définir un ensemble de variables pour votre application ou ouvrir une base de données requise par l’application.</span><span class="sxs-lookup"><span data-stu-id="e9526-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="e9526-109">Configuration requise pour la procédure principale</span><span class="sxs-lookup"><span data-stu-id="e9526-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="e9526-110">Un fichier qui s’exécute sur sa propre (généralement avec l’extension .exe) doit contenir un `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="e9526-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="e9526-111">Une bibliothèque (par exemple avec l’extension .dll) ne s’exécute pas son propre et ne requiert pas un `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="e9526-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="e9526-112">La configuration requise pour les différents types de projets que vous pouvez créer est les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e9526-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="e9526-113">Applications console s’exécutent leurs propres, et vous devez fournir au moins un `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="e9526-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="e9526-114">.</span><span class="sxs-lookup"><span data-stu-id="e9526-114">.</span></span>  
  
-   <span data-ttu-id="e9526-115">Applications Windows Forms s’exécutent sur leurs propres.</span><span class="sxs-lookup"><span data-stu-id="e9526-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="e9526-116">Toutefois, le compilateur Visual Basic génère automatiquement un `Main` procédure telle une application et que vous n’avez pas besoin d’écrire un.</span><span class="sxs-lookup"><span data-stu-id="e9526-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="e9526-117">Bibliothèques de classes ne nécessitent pas une `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="e9526-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="e9526-118">Il s’agit notamment des bibliothèques de contrôles Windows et les bibliothèques de contrôles Web.</span><span class="sxs-lookup"><span data-stu-id="e9526-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="e9526-119">Les applications Web sont déployées en tant que bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="e9526-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="e9526-120">Déclaration de la procédure principale</span><span class="sxs-lookup"><span data-stu-id="e9526-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="e9526-121">Il existe quatre méthodes pour déclarer le `Main` procédure.</span><span class="sxs-lookup"><span data-stu-id="e9526-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="e9526-122">Il peut accepter des arguments ou non, et elle peut retourner une valeur ou non.</span><span class="sxs-lookup"><span data-stu-id="e9526-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9526-123">Si vous déclarez `Main` dans une classe, vous devez utiliser le `Shared` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="e9526-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="e9526-124">Dans un module, `Main` n’est pas nécessaire de `Shared`.</span><span class="sxs-lookup"><span data-stu-id="e9526-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="e9526-125">La façon la plus simple consiste à déclarer un `Sub` procédure qui n’a pas été acceptent des arguments ou une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="e9526-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="e9526-126">`Main`peut également retourner un `Integer` valeur, que le système d’exploitation utilise comme code de sortie de votre programme.</span><span class="sxs-lookup"><span data-stu-id="e9526-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="e9526-127">Autres programmes peuvent tester ce code en examinant la valeur ERRORLEVEL Windows.</span><span class="sxs-lookup"><span data-stu-id="e9526-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="e9526-128">Pour retourner un code de sortie, vous devez déclarer `Main` comme un `Function` procédure au lieu d’un `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="e9526-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="e9526-129">`Main`peut également prendre une `String` tableau en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="e9526-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="e9526-130">Chaque chaîne dans le tableau contient un des arguments de ligne de commande utilisés pour appeler votre programme.</span><span class="sxs-lookup"><span data-stu-id="e9526-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="e9526-131">Vous pouvez effectuer des actions différentes en fonction de leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="e9526-131">You can take different actions depending on their values.</span></span>  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="e9526-132">Vous pouvez déclarer `Main` à examiner les arguments de ligne de commande, mais pas retourner un code de sortie, comme suit.</span><span class="sxs-lookup"><span data-stu-id="e9526-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e9526-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9526-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="e9526-134">Structure d’un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9526-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="e9526-135">/main</span><span class="sxs-lookup"><span data-stu-id="e9526-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="e9526-136">Shared</span><span class="sxs-lookup"><span data-stu-id="e9526-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="e9526-137">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="e9526-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e9526-138">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="e9526-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="e9526-139">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="e9526-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="e9526-140">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="e9526-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
