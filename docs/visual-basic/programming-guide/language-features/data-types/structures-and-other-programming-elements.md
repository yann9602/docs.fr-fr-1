---
title: "Structures and Other Programming Elements (Visual Basic) | Microsoft Docs"
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
  - "structures, arrays"
  - "procedures, structures as arguments to"
  - "objects [Visual Basic], structure elements"
  - "arrays [Visual Basic], structure elements"
  - "nested structures"
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Structures and Other Programming Elements (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez utiliser des structures avec des tableaux, des objets, des procédures, mais aussi les unes avec les autres.  Les interactions utilisent la même syntaxe que ces éléments pris individuellement.  
  
> [!NOTE]
>  Vous ne pouvez initialiser aucun des éléments de structure dans la déclaration de structure.  Vous pouvez assigner des valeurs uniquement aux éléments d'une variable qui a été déclarée comme un type structure.  
  
## Structures et tableaux  
 Une structure peut contenir un tableau comme un ou plusieurs de ses éléments.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Pour accéder aux valeurs d'un tableau dans une structure, procédez comme pour accéder à une propriété d'un objet.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Vous pouvez également déclarer un tableau de structures.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Dim allSystems(100) As systemInfo  
```  
  
 Suivez les mêmes règles pour accéder aux composants de cette architecture de données.  L'exemple suivant illustre ce comportement.  
  
```vb#  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## Structures et objets  
 Une structure peut contenir un objet comme un ou plusieurs de ses éléments.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Dans une déclaration de ce type, utilisez une classe d'objet spécifique de préférence à `Object`.  
  
## Structures et procédures  
 Vous pouvez passer une structure comme un argument de procédure.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 Dans l'exemple précédent, la structure est passée *par référence*, ce qui permet à la procédure de modifier ses éléments de sorte que les modifications prennent effet dans le code appelant.  Pour protéger une structure contre de telles modifications, passez\-la par valeur.  
  
 Vous pouvez également retourner une structure d'une procédure `Function`.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## Structures dans d'autres structures  
 Les structures peuvent contenir d'autres structures.  L'exemple suivant illustre ce comportement.  
  
```vb#  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb#  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 Vous pouvez également utiliser cette technique pour encapsuler une structure définie dans un module à l'intérieur d'une autre structure définie dans un module différent.  
  
 Les structures peuvent s'imbriquer dans d'autres structures sans limite de profondeur.  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)