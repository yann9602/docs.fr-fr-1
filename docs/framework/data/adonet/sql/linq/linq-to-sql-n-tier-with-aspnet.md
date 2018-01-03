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
ms.workload: dotnet
ms.openlocfilehash: 477af694874ada4ae24fda0f1dbfac824a5aadbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="73684-102">Applications multicouches LINQ to SQL avec ASP.NET</span><span class="sxs-lookup"><span data-stu-id="73684-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="73684-103">Dans les applications [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous utilisez le contrôle serveur Web <xref:System.Web.UI.WebControls.LinqDataSource> .</span><span class="sxs-lookup"><span data-stu-id="73684-103">In [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="73684-104">Ce contrôle gère la plus grande part de la logique dont il doit disposer pour exécuter des requêtes sur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], passer les données au navigateur, les récupérer et les soumettre à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> qui met ensuite à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="73684-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="73684-105">Vous configurez simplement le contrôle dans le balisage et le contrôle gère tous les transferts de données entre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et le navigateur.</span><span class="sxs-lookup"><span data-stu-id="73684-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="73684-106">Le contrôle gérant les interactions avec la couche Présentation et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gérant les communications avec la couche Données, votre tâche principale dans les applications multicouches [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] est l'écriture de votre logique métier personnalisée.</span><span class="sxs-lookup"><span data-stu-id="73684-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="73684-107">Pour plus d’informations sur `LINQDataSource`, consultez [Vue d’ensemble du contrôle serveur web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="73684-107">For more information about `LINQDataSource`, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73684-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73684-108">See Also</span></span>  
 [<span data-ttu-id="73684-109">Applications multicouches et distantes avec LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="73684-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
