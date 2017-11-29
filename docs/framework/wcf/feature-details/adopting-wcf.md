---
title: Adoption de Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 15fc02882148054fe53534c75905f51cfffe68fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="adopting-windows-communication-foundation"></a>Adoption de Windows Communication Foundation
Vous pouvez choisir d'utiliser [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour tout nouveau développement, en continuant de maintenir à jour les applications existantes développées à l'aide d'ASP.NET. Étant donné que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a été conçu pour faciliter au mieux la communication avec des applications développées avec le .NET Framework dans tous les scénarios, il peut faire office d'outil standard pour résoudre une large gamme de problèmes de communication du logiciel qu'ASP.NET ne peut résoudre de la même manière.  
  
 Les nouvelles applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être déployées sur les mêmes ordinateurs que services Web ASP.NET existants. Si les services Web ASP.NET existants utilisent une version du .NET Framework antérieure à la version 2.0, vous pouvez utiliser l'outil ASP.NET IIS Registration pour déployer sélectivement le .NET Framework 2.0 dans les applications IIS dans lesquelles de nouvelles applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seront hébergées. Cet outil est documenté à [ASP.NET IIS Registration Tool (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), et a une interface utilisateur intégrée de la console de gestion IIS 6.0.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être utilisé pour ajouter de nouvelles fonctionnalités aux services Web ASP.NET existants en ajoutant des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configurés pour s'exécuter en mode de compatibilité ASP.NET avec les applications de services Web ASP.NET existant dans IIS. En raison du mode de compatibilité ASP.NET, le code des nouveaux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut consulter et mettre à jour les mêmes informations d'état d'application que le code ASP.NET préexistant, en utilisant la classe <xref:System.Web.HttpContext>. Les applications peuvent également partager les mêmes bibliothèques de classes.  
  
 Les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent utiliser des services Web ASP.NET. Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configurés avec <xref:System.ServiceModel.BasicHttpBinding> peuvent être utilisés par les clients des services Web ASP.NET. Les services Web ASP.NET peuvent co-exister avec les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut même être utilisé pour ajouter des fonctionnalités aux services Web ASP.NET existants. Étant donné toutes les manières dont [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et les services Web ASP.NET peuvent être utilisés ensemble, vous pouvez effectuer une migration des services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seulement si vous avez besoin des fonctionnalités fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et pas par les services Web ASP.NET.  
  
 Même les rares fois où cela est nécessaire, dites-vous bien qu'effectuer une migration de code d'une technologie à une autre est rarement la bonne solution. L'adoption d'une nouvelle technologie permet de satisfaire de nouvelles spécifications qui ne peuvent pas être satisfaites avec la technologie antérieure, et dans ce cas, le mieux à faire est de concevoir une nouvelle solution qui satisfait l'ensemble des spécifications récemment étendues. La nouvelle conception bénéficie de votre expérience avec le système existant et du savoir-faire acquis depuis que ce système a été conçu. La nouvelle conception peut également profiter de l'intégralité des possibilités offertes par les nouvelles technologies plutôt que de reproduire l'ancienne conception sur la nouvelle plate-forme. Après le prototypage des éléments clés de la nouvelle conception, il devient plus facile de réutiliser le code du système existant dans le nouveau.  
  
 Pour les rares fois où le portage des services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est la solution appropriée, la section suivante fournit quelques indications sur la marche à suivre. Elle propose des conseils sur la manière de migrer des services et des clients.  
  
 Pour une analyse complète sur la façon de migrer des Services Web ASP.NET existants vers WCF, consultez [des Services Web ASP.NET et Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). Cette section décrit comment implémenter un service WCF conforme à partir des métadonnées de votre service Web ASP.NET, et comment effectuer une migration de service Web ASP.NET et de code client vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : récupérer les métadonnées et implémenter un Service conforme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Comment : migrer du Code de Service Web ASP.NET vers Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Comment : migrer le Code de Client de Service Web ASP.NET vers Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
