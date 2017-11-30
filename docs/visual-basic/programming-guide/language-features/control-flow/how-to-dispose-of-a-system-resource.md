---
title: "Comment : supprimer une ressource système (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5b5c65c9d123c6f481852eb249cb4d479a180c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Comment : supprimer une ressource système (Visual Basic)
Vous pouvez utiliser un `Using` bloc pour garantir que le système supprime une ressource lorsque votre code quitte le bloc. Cela est utile si vous utilisez une ressource système qui consomme une grande quantité de mémoire ou d’autres composants également à utiliser.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Pour supprimer une connexion de base de données lorsque votre code est terminé avec lui  
  
1.  Veillez à inclure les [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour la connexion de base de données au début de votre fichier source (dans ce cas, <xref:System.Data.SqlClient>).  
  
2.  Créer un `Using` bloc avec le `Using` et `End Using` instructions. À l’intérieur du bloc, placez le code qui traite de la connexion de base de données.  
  
3.  Déclarez la connexion et de créer une instance de celui-ci dans le cadre de la `Using` instruction.  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Le système supprime la ressource quelle que soit la manière dont vous quittez le bloc, y compris le cas d’une exception non gérée.  
  
     Notez que vous ne pouvez pas accéder aux `sqc` d’en dehors de la `Using` bloquer, car sa portée est limitée au bloc.  
  
     Vous pouvez utiliser cette même technique sur une ressource système telles que le handle de fichier ou un wrapper COM. Vous utilisez un `Using` bloquer lorsque vous souhaitez que de laisser la ressource disponible pour d’autres composants après avoir quitté le `Using` bloc.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.SqlClient.SqlConnection>  
 [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Using (instruction)](../../../../visual-basic/language-reference/statements/using-statement.md)
