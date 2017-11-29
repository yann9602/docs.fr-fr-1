---
title: "Comment : créer et utiliser des assemblys à l’aide de la ligne de commande (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Comment : créer et utiliser des assemblys à l’aide de la ligne de commande (Visual Basic)
Un assembly, ou une bibliothèque de lien dynamique (DLL), est lié à votre programme au moment de l’exécution. Pour illustrer la génération et l’utilisation d’une DLL, considérez le scénario suivant :  
  
-   `MathLibrary.DLL` : fichier bibliothèque qui contient les méthodes à appeler au moment de l’exécution. Dans cet exemple, la DLL contient deux méthodes, `Add` et `Multiply`.  
  
-   `Add` : fichier source qui contient la méthode `Add`. Il retourne la somme de ses paramètres. La classe `AddClass` qui contient la méthode `Add` est un membre de l’espace de noms `UtilityMethods`.  
  
-   `Mult` : code source qui contient la méthode `Multiply`. Il retourne le produit de ses paramètres. La classe `MultiplyClass` qui contient la méthode `Multiply` est également un membre de l’espace de noms `UtilityMethods`.  
  
-   `TestCode` : fichier qui contient la méthode `Main`. Il utilise les méthodes dans le fichier DLL pour calculer la somme et le produit des arguments d’exécution.  
  
## <a name="example"></a>Exemple  
  
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
  
 Ce fichier contient l’algorithme qui utilise les méthodes de la DLL, `Add` et `Multiply`. Il commence par analyser les arguments entrés à partir de la ligne de commande, `num1` et `num2`. Il calcule ensuite la somme en utilisant la méthode `Add` sur la classe `AddClass`, et le produit en utilisant la méthode `Multiply` sur la classe `MultiplyClass`.  
  
 Notez que la `Imports` instruction au début du fichier vous permet d’utiliser les noms de classe non qualifiés pour référencer les méthodes de la DLL au moment de la compilation, comme suit :  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Sinon, vous devez utiliser les noms qualifiés complets, comme suit :  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Exécution  
 Pour exécuter le programme, entrez le nom du fichier EXE, suivi de deux nombres, comme suit :  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour générer le fichier `MathLibrary.DLL`, compilez les deux fichiers `Add` et `Mult` à l’aide de la ligne de commande.  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 Le [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) option du compilateur indique au compilateur de générer une DLL au lieu d’un fichier EXE. Le [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) option du compilateur suivie d’un nom de fichier est utilisée pour spécifier le nom du fichier DLL. Sinon, le compilateur utilise le premier fichier (`Add.vb`) comme nom de la DLL.  
  
 Pour générer le fichier exécutable, `TestCode.exe`, utilisez la ligne de commande suivante :  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 L’option du compilateur **/out** indique au compilateur qu’il faut générer un fichier EXE, et spécifie le nom du fichier de sortie (`TestCode.exe`). Cette option du compilateur est facultative. Le [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur spécifie le fichier DLL ou les fichiers que ce programme utilise.  
  
 Pour plus d’informations sur la génération à partir de la ligne de commande, consultez et [génération à partir de la ligne de commande](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Création d’une classe pour contenir des fonctions DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
