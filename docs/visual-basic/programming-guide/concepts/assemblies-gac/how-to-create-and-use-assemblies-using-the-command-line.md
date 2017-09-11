---
title: "Comment : créer et utiliser des assemblys à l’aide de la ligne de commande (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 69e9cab9dda1fefe8bee3dc46b541313d1d80e58
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="df235-102">Comment : créer et utiliser des assemblys à l’aide de la ligne de commande (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df235-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="df235-103">Un assembly ou une bibliothèque de lien dynamique (DLL), est liée à votre programme au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="df235-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="df235-104">Pour illustrer la génération et l’utilisation d’une DLL, considérez le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="df235-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="df235-105">`MathLibrary.DLL`: Le fichier bibliothèque qui contient les méthodes à appeler au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="df235-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="df235-106">Dans cet exemple, la DLL contient deux méthodes, `Add` et `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="df235-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="df235-107">`Add`: Le fichier source qui contient la méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="df235-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="df235-108">Il retourne la somme de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="df235-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="df235-109">La classe `AddClass` qui contient la méthode `Add` est un membre de l’espace de noms `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="df235-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="df235-110">`Mult`: Le code source qui contient la méthode `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="df235-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="df235-111">Il retourne le produit de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="df235-111">It returns the product of its parameters.</span></span> <span data-ttu-id="df235-112">La classe `MultiplyClass` qui contient la méthode `Multiply` est également un membre de l’espace de noms `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="df235-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="df235-113">`TestCode`: Le fichier qui contient le `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="df235-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="df235-114">Il utilise les méthodes dans le fichier DLL pour calculer la somme et le produit des arguments d’exécution.</span><span class="sxs-lookup"><span data-stu-id="df235-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df235-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="df235-115">Example</span></span>  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 <span data-ttu-id="df235-116">Ce fichier contient l’algorithme qui utilise les méthodes de la DLL, `Add` et `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="df235-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="df235-117">Il commence par analyser les arguments entrés à partir de la ligne de commande `num1` et `num2`.</span><span class="sxs-lookup"><span data-stu-id="df235-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="df235-118">Il calcule ensuite la somme en utilisant la `Add` méthode sur le `AddClass` (classe) et le produit à l’aide de la `Multiply` méthode sur la `MultiplyClass` classe.</span><span class="sxs-lookup"><span data-stu-id="df235-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="df235-119">Notez que la `Imports` instruction au début du fichier vous permet d’utiliser les noms de classes non qualifiés pour référencer les méthodes de la DLL au moment de la compilation, comme suit :</span><span class="sxs-lookup"><span data-stu-id="df235-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="df235-120">Dans le cas contraire, vous devez utiliser les noms qualifiés complets, comme suit :</span><span class="sxs-lookup"><span data-stu-id="df235-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="df235-121">Exécution</span><span class="sxs-lookup"><span data-stu-id="df235-121">Execution</span></span>  
 <span data-ttu-id="df235-122">Pour exécuter le programme, entrez le nom du fichier EXE, suivi de deux nombres, comme suit :</span><span class="sxs-lookup"><span data-stu-id="df235-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="df235-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="df235-123">Compiling the Code</span></span>  
 <span data-ttu-id="df235-124">Pour générer le fichier `MathLibrary.DLL`, compilez les deux fichiers `Add` et `Mult` à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="df235-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="df235-125">Le [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) option du compilateur indique au compilateur de générer une DLL au lieu d’un fichier EXE.</span><span class="sxs-lookup"><span data-stu-id="df235-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="df235-126">Le [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) option du compilateur suivie d’un nom de fichier est utilisée pour spécifier le nom du fichier DLL.</span><span class="sxs-lookup"><span data-stu-id="df235-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="df235-127">Dans le cas contraire, le compilateur utilise le premier fichier (`Add.vb`) comme nom de la DLL.</span><span class="sxs-lookup"><span data-stu-id="df235-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="df235-128">Pour générer le fichier exécutable, `TestCode.exe`, utilisez la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="df235-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="df235-129">Le **/out** option du compilateur indique au compilateur de générer un fichier EXE et spécifie le nom du fichier de sortie (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="df235-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="df235-130">Cette option du compilateur est facultative.</span><span class="sxs-lookup"><span data-stu-id="df235-130">This compiler option is optional.</span></span> <span data-ttu-id="df235-131">Le [Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur spécifie les fichiers DLL que ce programme utilise.</span><span class="sxs-lookup"><span data-stu-id="df235-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="df235-132">Pour plus d’informations sur la génération à partir de la ligne de commande, consultez la page et [génération à partir de la ligne de commande](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="df235-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df235-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df235-133">See Also</span></span>  
 <span data-ttu-id="df235-134">[Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="df235-134">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="df235-135"> [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="df235-135"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="df235-136"> [Création d’une classe pour contenir des fonctions DLL](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)</span><span class="sxs-lookup"><span data-stu-id="df235-136"> [Creating a Class to Hold DLL Functions](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)</span></span>
