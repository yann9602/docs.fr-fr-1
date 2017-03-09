---
title: "How to: Call a Windows Function that Takes Unsigned Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Windows functions, calling"
  - "unsigned data types"
  - "UShort data type, using"
  - "functions [Visual Basic], calling Windows functions"
  - "ULong data type, using"
  - "UInteger data type, using"
  - "data types [Visual Basic], using"
  - "unsigned types"
  - "data types [Visual Basic], unsigned"
  - "data types [Visual Basic], numeric"
  - "unsigned types, using"
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Si vous consommez une classe, un module ou une structure qui a des membres de types d'entiers non signés, vous pouvez accéder à ces membres avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
### Pour appeler une fonction Windows qui prend un type non signé  
  
1.  Utilisez une [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) pour indiquer à [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] quelle bibliothèque contient la fonction, quel est son nom dans cette bibliothèque, quelle est sa séquence d'appel et comment convertir des chaînes lors de son appel.  
  
2.  Dans l'instruction `Declare`, utilisez `UInteger`, `ULong`, `UShort` ou `Byte` selon le cas pour chaque paramètre avec un type non signé.  
  
3.  Pour déterminer les noms et les valeurs des constantes de la fonction Windows que vous appelez, consultez la documentation relative à cette fonction.  Une grande partie de ces noms et valeurs sont définis dans le fichier WinUser.h.  
  
4.  Déclarez les constantes nécessaires dans votre code.  De nombreuses constantes Windows sont des valeurs non signées de 32 bits, que vous devez déclarer  `As` `UInteger`.  
  
5.  Appelez la fonction de manière normale.  L'exemple suivant appelle la fonction Windows `MessageBox`, qui prend un argument d'entier non signé.  
  
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
  
     Vous pouvez tester la fonction `messageThroughWindows` à l'aide du code suivant.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  Les types de données `UInteger`, `ULong`, `UShort` et `SByte` ne faisant pas partie de la [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), le code conforme CLS ne peut pas consommer un composant qui les utilise.  
  
    > [!IMPORTANT]
    >  Le fait d'appeler du code non managé, tel que l'interface de programmation d'application Windows \(API\), expose votre code à des problèmes de sécurité potentiels.  
  
    > [!IMPORTANT]
    >  L'appel de l'API Windows nécessite une autorisation de code non managée, qui peut affecter son exécution dans les situations d'un niveau de confiance partiel.  Pour plus d'informations, consultez <xref:System.Security.Permissions.SecurityPermission> et [Code Access Permissions](http://msdn.microsoft.com/fr-fr/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## Voir aussi  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)