---
title: LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cdd3f21d8b02c24db24d2efd08487ef1a290e022
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] facilite et accélère l'interrogation de données mises en cache dans un objet <xref:System.Data.DataSet>. Plus précisément, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifie l’interrogation en permettant aux développeurs d’écrire des requêtes dans le langage de programmation, à la place d’à l’aide d’un langage de requête distincte. Cela est particulièrement utile pour [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] développeurs peuvent désormais tirer parti de la vérification de la syntaxe de la compilation, les types statiques et prise en charge de IntelliSense fournis par le [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] dans les requêtes.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] peut également être utilisé pour interroger des données qui ont été consolidées à partir d'une ou plusieurs sources de données. Cela permet plusieurs scénarios qui requièrent de la flexibilité dans la manière dont les données sont représentées et gérées, comme l'interrogation de données agrégées localement et la mise en cache en couche intermédiaire dans les applications Web. En particulier, les applications génériques de création de rapports, d'analyse et de business intelligence requièrent cette méthode de manipulation.  
  
 Le [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fonctionnalité est exposée principalement via les méthodes d’extension dans le <xref:System.Data.DataRowExtensions> et <xref:System.Data.DataTableExtensions> classes. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]s’appuie sur et utilise existants [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture et n’est pas censé remplacer [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] dans le code d’application. Le code ADO.NET 2.0 existant continuera à fonctionner dans une application [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. La relation de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] avec [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] et le magasin de données est illustrée dans le diagramme suivant.  
  
 ![LINQ to DataSet est basé sur le fournisseur ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Référence  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ et ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
