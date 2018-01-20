---
title: "Remarques sur le déploiement (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d38f90822746c08d576879ab35fa0984e439640b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="deployment-considerations-entity-framework"></a>Remarques sur le déploiement (Entity Framework)
Cette rubrique fournit des informations sur le déploiement d’applications qui utilisent ADO.NET Entity Framework pour l’accès aux données. Pour plus d’informations sur l’Entity Framework, consultez [mise en route](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework propose un ensemble d’outils qui s’intègrent à Visual Studio et facilitent le développement dans cet environnement. Pour plus d’informations, consultez [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527). Cette rubrique ne décrit pas comment utiliser des technologies spécifiques pour déployer une application Entity Framework.  
  
 Visual Studio propose des fonctions de distribution et de déploiement d'applications, comme le déploiement ClickOnce. Pour plus d’informations, consultez [déploiement d’Applications et composants](/visualstudio/deployment/deploying-applications-services-and-components) dans la documentation de Visual Studio.  
  
 Vous devez tenir compte des points suivants lorsque vous déployez une application qui utilise Entity Framework :  
  
-   Entity Framework est un composant du .NET Framework depuis la version .NET Framework 3.5 Service Pack 1 (SP1). Vous devez vous assurer que .NET Framework SP1 ou une version ultérieure est installée lors du déploiement d'une application Entity Framework.  
  
-   Lorsqu'un modèle conceptuel est généré par l'Assistant EDM, une chaîne de connexion est créée dans le fichier de configuration de l'application. Les fichiers de mappage et de modèle peuvent être incorporés comme ressources d'application ou ils peuvent être copiés dans le répertoire de sortie. Par défaut, ils sont déployés en tant que ressources d'application incorporées. Utilisez la propriété `Metadata Artifact Processing` du fichier du concepteur d'entités pour sélectionner l'une de ces options. Pour plus d’informations, consultez [Comment : copie de fichiers de modèle et de mappage dans le répertoire de sortie](http://msdn.microsoft.com/library/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Vérifiez que les informations de mappage et de modèle (exprimées dans les langages CSDL (Conceptual Schema Definition Language), SSDL (Store Schema Definition Language) et MSL (Mapping Specification Language)) sont déployées avec l'application et dans l'emplacement spécifié par la chaîne de connexion. Pour plus d’informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Lorsque vous incorporez des informations de mappage et de modèle en tant que ressources d'application, vous devez recompiler et redéployer l'application chaque fois que le modèle conceptuel est mis à jour.  
  
-   Entity Framework étant un composant du .NET Framework, il peut ainsi être redistribué avec votre application si le contrat de licence du .NET Framework l’autorise.  
  
## <a name="see-also"></a>Voir aussi  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Points à prendre en considération pour le développement et le déploiement](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
