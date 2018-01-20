---
title: "Comment : appeler une fonction Windows qui possède des types non signés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 78e6789e7def5deeb8394e3aefecfdc187ec6ef6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Comment : appeler une fonction Windows qui possède des types non signés (Visual Basic)
Si vous consommez une classe, un module ou une structure qui possède des membres de types d’entiers non signés, vous pouvez accéder à ces membres avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Pour appeler une fonction Windows qui prend un type non signé  
  
1.  Utilisez un [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) indiquer [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bibliothèque qui conserve la fonction, ce qui est son nom dans cette bibliothèque, quelle est sa séquence d’appel et comment convertir des chaînes lors de son appel.  
  
2.  Dans le `Declare` instruction, utilisez `UInteger`, `ULong`, `UShort`, ou `Byte` selon le cas pour chaque paramètre avec un type non signé.  
  
3.  Consultez la documentation de la fonction Windows que vous appelez pour rechercher les noms et valeurs de constantes. Bon nombre d'entre elles sont définies dans le fichier WinUser.h.  
  
4.  Déclarez les constantes nécessaires dans votre code. Nombreuses constantes Windows sont des valeurs non signées de 32 bits, et vous devez déclarer `As``UInteger`.  
  
5.  Appelez la fonction de façon normale. L’exemple suivant appelle la fonction Windows `MessageBox`, qui prend un argument d’entier non signé.  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     Vous pouvez tester la fonction `messageThroughWindows` avec le code suivant.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  Le `UInteger`, `ULong`, `UShort`, et `SByte` des types de données ne sont pas dans le cadre de la [indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md) (CLS), un code conforme CLS ne peut pas consommer un composant qui les utilise.  
  
    > [!IMPORTANT]
    >  Effectue un appel au code non managé, telles que l’interface de programmation d’application Windows (API), expose votre code à des risques de sécurité potentiels.  
  
    > [!IMPORTANT]
    >  Appel de l’API Windows requiert l’autorisation de code non managé, ce qui peut affecter son exécution dans les situations de confiance partielle. Pour plus d’informations, consultez <xref:System.Security.Permissions.SecurityPermission> et [autorisations d’accès de Code](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Integer (type de données)](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [UInteger (type de données)](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Procédure pas à pas : appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
