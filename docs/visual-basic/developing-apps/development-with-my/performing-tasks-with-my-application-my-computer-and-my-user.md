---
title: "Exécution de tâches avec My.Application, My.Computer et My.User (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d55e0b3a126f2216d005c7bddbcaefb7d8f0a580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="81b86-102">Exécution de tâches avec My.Application, My.Computer et My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81b86-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="81b86-103">Le centre de trois `My` sont des objets qui fournissent l’accès aux informations et couramment utilisé la fonctionnalité `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), et `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="81b86-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="81b86-104">Vous pouvez utiliser ces objets pour accéder aux informations relatives à l’application en cours, l’application est installée sur l’ordinateur ou l’utilisateur actuel de l’application, respectivement.</span><span class="sxs-lookup"><span data-stu-id="81b86-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="81b86-105">My.Application, My.Computer et My.User</span><span class="sxs-lookup"><span data-stu-id="81b86-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="81b86-106">Les exemples suivants montrent comment les informations peuvent être récupérées à l’aide `My`.</span><span class="sxs-lookup"><span data-stu-id="81b86-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="81b86-107">En plus de la récupération des informations, les membres exposés par ces trois objets vous permettent également d’exécuter des méthodes associées à cet objet.</span><span class="sxs-lookup"><span data-stu-id="81b86-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="81b86-108">Par exemple, vous pouvez accéder à diverses méthodes pour manipuler des fichiers ou de mettre à jour le Registre à l’aide `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="81b86-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="81b86-109">Fichier e/s est considérablement plus facile et plus rapide avec `My`, qui inclut diverses méthodes et propriétés pour la manipulation de fichiers, des répertoires et des lecteurs.</span><span class="sxs-lookup"><span data-stu-id="81b86-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="81b86-110">Le <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objet vous permet de lire des fichiers volumineux structurés qui ont délimitées ou des champs de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="81b86-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="81b86-111">Cet exemple ouvre le `TextFieldParser``reader` et l’utilise pour lire à partir de `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="81b86-111">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="81b86-112">`My.Application`vous permet de modifier la culture de votre application.</span><span class="sxs-lookup"><span data-stu-id="81b86-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="81b86-113">L’exemple suivant montre comment cette méthode peut être appelée.</span><span class="sxs-lookup"><span data-stu-id="81b86-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="81b86-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81b86-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="81b86-115">Comment My dépend du type de projet</span><span class="sxs-lookup"><span data-stu-id="81b86-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
