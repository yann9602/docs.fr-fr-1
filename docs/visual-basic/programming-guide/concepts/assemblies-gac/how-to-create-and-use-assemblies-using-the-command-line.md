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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 363bca806736e5540165ea96e9b4fe60d0968098
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Comment : créer et utiliser des assemblys à l’aide de la ligne de commande (Visual Basic)
Un assembly ou une bibliothèque de lien dynamique (DLL), est liée à votre programme au moment de l’exécution. Pour illustrer la génération et l’utilisation d’une DLL, considérez le scénario suivant :  
  
-   `MathLibrary.DLL`: Le fichier bibliothèque qui contient les méthodes à appeler au moment de l’exécution. Dans cet exemple, la DLL contient deux méthodes, `Add` et `Multiply`.  
  
-   `Add`: Le fichier source qui contient la méthode `Add`. Il retourne la somme de ses paramètres. La classe `AddClass` qui contient la méthode `Add` est un membre de l’espace de noms `UtilityMethods`.  
  
-   `Mult`: Le code source qui contient la méthode `Multiply`. Il retourne le produit de ses paramètres. La classe `MultiplyClass` qui contient la méthode `Multiply` est également un membre de l’espace de noms `UtilityMethods`.  
  
-   `TestCode`: Le fichier qui contient le `Main` (méthode). Il utilise les méthodes dans le fichier DLL pour calculer la somme et le produit des arguments d’exécution.  
  
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
  
 Ce fichier contient l’algorithme qui utilise les méthodes de la DLL, `Add` et `Multiply`. Il commence par analyser les arguments entrés à partir de la ligne de commande `num1` et `num2`. Il calcule ensuite la somme en utilisant la `Add` méthode sur le `AddClass` (classe) et le produit à l’aide de la `Multiply` méthode sur la `MultiplyClass` classe.  
  
 Notez que la `Imports` instruction au début du fichier vous permet d’utiliser les noms de classes non qualifiés pour référencer les méthodes de la DLL au moment de la compilation, comme suit :  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 Dans le cas contraire, vous devez utiliser les noms qualifiés complets, comme suit :  
  
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
  
 Le [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) option du compilateur indique au compilateur de générer une DLL au lieu d’un fichier EXE. Le [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) option du compilateur suivie d’un nom de fichier est utilisée pour spécifier le nom du fichier DLL. Dans le cas contraire, le compilateur utilise le premier fichier (`Add.vb`) comme nom de la DLL.  
  
 Pour générer le fichier exécutable, `TestCode.exe`, utilisez la ligne de commande suivante :  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 Le **/out** option du compilateur indique au compilateur de générer un fichier EXE et spécifie le nom du fichier de sortie (`TestCode.exe`). Cette option du compilateur est facultative. Le [Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur spécifie les fichiers DLL que ce programme utilise.  
  
 Pour plus d’informations sur la génération à partir de la ligne de commande, consultez la page et [génération à partir de la ligne de commande](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Création d’une classe pour contenir des fonctions DLL](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)
