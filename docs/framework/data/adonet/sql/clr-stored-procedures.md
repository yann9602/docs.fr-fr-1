---
title: "Procédures stockées CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1e55222c16d223a86e1e11ce2b985ec0f4d8eaa3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="f7f8a-102">Procédures stockées CLR</span><span class="sxs-lookup"><span data-stu-id="f7f8a-102">CLR Stored Procedures</span></span>
<span data-ttu-id="f7f8a-103">Les procédures stockées sont des routines pouvant être utilisées dans les expressions scalaires.</span><span class="sxs-lookup"><span data-stu-id="f7f8a-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="f7f8a-104">Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="f7f8a-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7f8a-105">Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="f7f8a-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="f7f8a-106">Vous devez spécifier pour passer le paramètre par référence et appliquer le \<Out() > attribut pour représenter un paramètre de sortie, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f7f8a-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="f7f8a-107">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="f7f8a-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="f7f8a-108">**Documentation en ligne de SQL Server**</span><span class="sxs-lookup"><span data-stu-id="f7f8a-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="f7f8a-109">Procédures stockées CLR</span><span class="sxs-lookup"><span data-stu-id="f7f8a-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="f7f8a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7f8a-110">See Also</span></span>  
 [<span data-ttu-id="f7f8a-111">Création d’objets SQL Server 2005 dans le Code managé</span><span class="sxs-lookup"><span data-stu-id="f7f8a-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="f7f8a-112">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="f7f8a-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
