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
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="aba41-102">Comment : supprimer une ressource système (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aba41-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="aba41-103">Vous pouvez utiliser un `Using` bloc pour garantir que le système supprime une ressource lorsque votre code quitte le bloc.</span><span class="sxs-lookup"><span data-stu-id="aba41-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="aba41-104">Cela est utile si vous utilisez une ressource système qui consomme une grande quantité de mémoire ou d’autres composants également à utiliser.</span><span class="sxs-lookup"><span data-stu-id="aba41-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="aba41-105">Pour supprimer une connexion de base de données lorsque votre code est terminé avec lui</span><span class="sxs-lookup"><span data-stu-id="aba41-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="aba41-106">Veillez à inclure les [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour la connexion de base de données au début de votre fichier source (dans ce cas, <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="aba41-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="aba41-107">Créer un `Using` bloc avec le `Using` et `End Using` instructions.</span><span class="sxs-lookup"><span data-stu-id="aba41-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="aba41-108">À l’intérieur du bloc, placez le code qui traite de la connexion de base de données.</span><span class="sxs-lookup"><span data-stu-id="aba41-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="aba41-109">Déclarez la connexion et de créer une instance de celui-ci dans le cadre de la `Using` instruction.</span><span class="sxs-lookup"><span data-stu-id="aba41-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="aba41-110">Le système supprime la ressource quelle que soit la manière dont vous quittez le bloc, y compris le cas d’une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="aba41-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="aba41-111">Notez que vous ne pouvez pas accéder aux `sqc` d’en dehors de la `Using` bloquer, car sa portée est limitée au bloc.</span><span class="sxs-lookup"><span data-stu-id="aba41-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="aba41-112">Vous pouvez utiliser cette même technique sur une ressource système telles que le handle de fichier ou un wrapper COM.</span><span class="sxs-lookup"><span data-stu-id="aba41-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="aba41-113">Vous utilisez un `Using` bloquer lorsque vous souhaitez que de laisser la ressource disponible pour d’autres composants après avoir quitté le `Using` bloc.</span><span class="sxs-lookup"><span data-stu-id="aba41-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba41-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aba41-114">See Also</span></span>  
 <xref:System.Data.SqlClient.SqlConnection>  
 [<span data-ttu-id="aba41-115">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="aba41-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="aba41-116">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="aba41-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="aba41-117">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="aba41-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="aba41-118">Autres structures de contrôle</span><span class="sxs-lookup"><span data-stu-id="aba41-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="aba41-119">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="aba41-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="aba41-120">Using (instruction)</span><span class="sxs-lookup"><span data-stu-id="aba41-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
