---
title: "Comment : appeler une fonction Windows qui possède des Types non signés (Visual Basic) | Documents Microsoft"
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
- Windows functions, calling
- unsigned data types
- UShort data type, using
- functions [Visual Basic], calling Windows functions
- ULong data type, using
- UInteger data type, using
- data types [Visual Basic], using
- unsigned types
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types, using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fbff07f4923b0633a2bc9b4fd558d9d51f64370a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Comment : appeler une fonction Windows qui possède des types non signés (Visual Basic)
Si vous consommez une classe, un module ou une structure qui possède des membres de types d’entiers non signés, vous pouvez accéder à ces membres avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Pour appeler une fonction Windows qui prend un type non signé  
  
1.  Utilisez un [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) à [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] quelle bibliothèque contient la fonction, quel est son nom dans cette bibliothèque, ce qui est sa séquence d’appel et comment convertir des chaînes lors de son appel.  
  
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
    >  Le `UInteger`, `ULong`, `UShort`, et `SByte` des types de données ne sont pas dans le cadre de la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), le code conforme CLS ne peut pas consommer un composant qui les utilise.  
  
    > [!IMPORTANT]
    >  Effectue un appel au code non managé, telles que l’interface de programmation d’application Windows (API), expose votre code à des risques de sécurité potentiels.  
  
    > [!IMPORTANT]
    >  Appel de l’API Windows nécessite une autorisation de code non managé, qui peut affecter son exécution dans les situations de confiance partielle. Pour plus d’informations, consultez <xref:System.Security.Permissions.SecurityPermission>et [autorisations d’accès de Code](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</xref:System.Security.Permissions.SecurityPermission>  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type de données Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Type de données UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Procédure pas à pas : appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
