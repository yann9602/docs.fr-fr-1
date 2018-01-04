---
title: "Comment : déployer une application d'intégration COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aca9df2be74dba308d3c4e4eb1c61b3e1afaa580
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a>Comment : déployer une application d'intégration COM+
Après avoir écrit une application d'intégration COM+, vous pouvez la déployer sur un autre ordinateur. Cette rubrique décrit comment déplacer une application d'intégration COM+ d'un ordinateur vers un autre.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Déplacement d'une application d'intégration hébergée COM+  
  
1.  Assurez-vous que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est installé sur les deux ordinateurs.  
  
2.  Exportez l'application de l'ordinateur A.  
  
3.  Importez l'application sur l'ordinateur B.  
  
4.  Définissez le répertoire racine de l'application. Par convention, il s'agit de %PROGRAMFILES%/ComPlus Applications/{AppGUID}.  
  
5.  Copiez les fichiers Application.config et Application.manifest du répertoire racine de l'application sur l'ordinateur A vers le répertoire racine de l'application sur l'ordinateur B.  
  
6.  Modifiez les adresses de point de terminaison de service dans le fichier Application.config sur l'ordinateur B pour identifier l'ordinateur approprié. Par exemple, remplacez http://machineA/MyService par http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Déplacement d'une application d'intégration hébergée sur le Web  
  
1.  Assurez-vous que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est installé sur les deux ordinateurs.  
  
2.  Exportez l'application de l'ordinateur A.  
  
3.  Importez l'application sur l'ordinateur B.  
  
4.  Créez une racine virtuelle IIS sur l'ordinateur B.  
  
5.  Copiez le fichier .svc (componentName.svc) et le fichier Web.config de la racine virtuelle sur l'ordinateur A vers la racine virtuelle que vous venez de créer sur l'ordinateur B.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’intégration à des applications COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Guide pratique pour configurer des paramètres de service COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Guide pratique pour utiliser l’outil de configuration de modèle de service COM+](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
