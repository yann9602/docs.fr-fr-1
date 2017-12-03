---
title: Magasin d'instances de workflow SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 638ad75155bae30f3cd1d126d27e8e0542026ab0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="sql-workflow-instance-store"></a>Magasin d'instances de workflow SQL
Le [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] est fourni avec le magasin d'instances de workflow SQL, qui permet aux workflows de rendre les informations d'état persistantes à propos des instances de workflow dans SQL Server 2005 ou dans une base de données SQL Server 2008. Cette fonctionnalité est implémentée principalement dans le formulaire de la classe <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, qui dérive de la classe <xref:System.Runtime.DurableInstancing.InstanceStore> abstraite de l'infrastructure de persistance. La fonctionnalité de magasin d'instances de workflow SQL constitue un fournisseur de persistance SQL, qui est une implémentation concrète de l'API de persistance qu'un hôte utilise pour envoyer des commandes de persistance au magasin.  
  
 Le SQL Workflow Instance Store prend en charge à la fois les workflows auto-hébergés ou les services de workflow qui utilisent <xref:System.Activities.WorkflowApplication> ou <xref:System.ServiceModel.WorkflowServiceHost> et les services hébergés dans WAS qui utilisent <xref:System.ServiceModel.WorkflowServiceHost>. Vous pouvez configurer par programmation la fonctionnalité de magasin d'instances de workflow SQL pour les services auto-hébergés à l'aide du modèle objet exposé par la fonctionnalité. Vous pouvez configurer cette fonctionnalité pour les services hébergés à la fois par programmation par <xref:System.ServiceModel.WorkflowServiceHost> à l'aide du modèle objet et également en utilisant un fichier de configuration XML.  
  
 La fonctionnalité de magasin d’instances de flux de travail de SQL (**SqlWorkflowInstanceStore** classe) n’implémente pas <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> et n’offre donc pas prise en charge de la persistance de services WCF durables en dehors du workflow. Il n'implémente pas également <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> et d'où n'offre pas support de persistance pour 3.x workflows. La fonctionnalité prend uniquement en charge la persistance pour les services de workflow et les workflow WF 4.0 (et version ultérieure). La fonctionnalité ne prend pas en charge les bases de données autres que SQL Server 2005 et SQL Server 2008.  
  
 Les rubriques de cette section décrivent les propriétés et fonctionnalités du magasin d'instances de workflow SQL et vous fournissent des détails sur la configuration du magasin.  
  
 Windows Server AppFabric fournit son propre magasin d'instances et des outils pour simplifier la configuration et l'utilisation du magasin d'instances. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]consultez [magasin d’instances Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201201). [!INCLUDE[crabout](../../../includes/crabout-md.md)]voir de la base de données de persistance App Fabric SQL Server [base de données de persistance App Fabric SQL Server](http://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés du magasin d’instances de workflow SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Guide pratique pour activer la persistance SQL dans les workflows et les services de workflow](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Activation d’instance](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Prise en charge des requêtes](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Stocker l’extensibilité](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Sécurité](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [Base de données de persistance SQL Server](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de persistance](http://go.microsoft.com/fwlink/?LinkID=177735)
