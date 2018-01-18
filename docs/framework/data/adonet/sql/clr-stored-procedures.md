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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aebc681482482c364f762b12065cf041f4976be9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="clr-stored-procedures"></a>Procédures stockées CLR
Les procédures stockées sont des routines pouvant être utilisées dans les expressions scalaires. Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL (Data Definition Language) et DML (Data Manipulation Language) et retourner des paramètres de sortie.  
  
> [!NOTE]
>  Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C#. Vous devez spécifier pour passer le paramètre par référence et appliquer le \<Out() > attribut pour représenter un paramètre de sortie, comme suit :  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
1.  [Procédures stockées CLR](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’objets SQL Server 2005 dans le Code managé](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
