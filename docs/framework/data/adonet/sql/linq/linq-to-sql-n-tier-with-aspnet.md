---
title: Applications multicouches LINQ to SQL avec ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 643f38c495a57dd98c3524eaf82cdbdfe42220c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>Applications multicouches LINQ to SQL avec ASP.NET
Dans les applications [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous utilisez le contrôle serveur Web <xref:System.Web.UI.WebControls.LinqDataSource> . Ce contrôle gère la plus grande part de la logique dont il doit disposer pour exécuter des requêtes sur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passer les données au navigateur, les récupérer et les soumettre à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> qui met ensuite à jour la base de données. Vous configurez simplement le contrôle dans le balisage et le contrôle gère tous les transferts de données entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et le navigateur. Le contrôle gérant les interactions avec la couche Présentation et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gérant les communications avec la couche Données, votre tâche principale dans les applications multicouches [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] est l'écriture de votre logique métier personnalisée.  
  
 Pour plus d’informations sur `LINQDataSource`, consultez [Vue d’ensemble du contrôle serveur web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## <a name="see-also"></a>Voir aussi  
 [Multicouches et des Applications distantes avec LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
