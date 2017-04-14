---
title: "Proc&#233;dures stock&#233;es CLR | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Proc&#233;dures stock&#233;es CLR
Les procédures stockées sont des routines pouvant être utilisées dans les expressions scalaires.  Elles peuvent retourner des résultats tabulaires et des messages au client, invoquer des instructions DDL \(Data Definition Language\) et DML \(Data Manipulation Language\) et retourner des paramètres de sortie.  
  
> [!NOTE]
>  Microsoft Visual Basic ne prend pas en charge les paramètres de sortie de la même manière que Microsoft Visual C\#.  Vous devez spécifier qu'il faut passer le paramètre par référence et appliquer l'attribut \<Out\(\)\> pour représenter un paramètre de sortie, comme suit :  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
1.  [Procédures stockées CLR](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## Voir aussi  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/fr-fr/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)