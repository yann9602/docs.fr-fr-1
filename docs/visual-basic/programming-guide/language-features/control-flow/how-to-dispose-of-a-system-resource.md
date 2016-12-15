---
title: "How to: Dispose of a System Resource (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Using statement, disposing of system resources"
  - "Visual Basic code, control flow"
  - "system resources, disposing of"
  - "resources [Visual Basic], disposing of system"
  - "system resources"
  - "Using statement, Using...End Using"
  - "Using block"
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Dispose of a System Resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser un bloc `Using` pour vous assurer que le système supprime une ressource lorsque votre code quitte le bloc.  Cette opération est utile si vous utilisez une ressource système qui consomme une grande quantité de mémoire ou que d'autres composants souhaitent également utiliser.  
  
### Pour supprimer une connexion de base de données lorsque votre code a fini de l'utiliser  
  
1.  Assurez\-vous d'inclure l'[Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) appropriée pour la connexion de base de données au début de votre fichier source \(dans le cas présent, <xref:System.Data.SqlClient>\).  
  
2.  Créez un bloc `Using` avec les instructions `Using` et `End Using` À l'intérieur du bloc, insérez le code qui traite de la connexion de base de données.  
  
3.  Déclarez la connexion et créez\-en une instance dans le cadre de l'instruction `Using`.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Le système supprime la ressource quelle que soit la manière dont vous quittez le bloc, y compris en cas d'exception non gérée.  
  
     Notez que vous ne pouvez pas accéder à `sqc` à l'extérieur du bloc `Using`, car sa portée est limitée au bloc.  
  
     Vous pouvez utiliser cette même technique sur une ressource système, telle qu'un handle de fichier ou un wrapper COM.  Vous utilisez un bloc `Using` lorsque vous souhaitez être sûr de laisser la ressource à la disposition d'autres composants après avoir quitté le bloc `Using`.  
  
## Voir aussi  
 <xref:System.Data.SqlClient.SqlConnection>   
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)