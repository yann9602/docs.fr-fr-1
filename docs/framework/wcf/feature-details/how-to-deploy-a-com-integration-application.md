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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d6d9103c2d36de81392858fedc249be9f7ae94f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="5fabd-102">Comment : déployer une application d'intégration COM+</span><span class="sxs-lookup"><span data-stu-id="5fabd-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="5fabd-103">Après avoir écrit une application d'intégration COM+, vous pouvez la déployer sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5fabd-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="5fabd-104">Cette rubrique décrit comment déplacer une application d'intégration COM+ d'un ordinateur vers un autre.</span><span class="sxs-lookup"><span data-stu-id="5fabd-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="5fabd-105">Déplacement d'une application d'intégration hébergée COM+</span><span class="sxs-lookup"><span data-stu-id="5fabd-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="5fabd-106">Assurez-vous que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est installé sur les deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5fabd-106">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="5fabd-107">Exportez l'application de l'ordinateur A.</span><span class="sxs-lookup"><span data-stu-id="5fabd-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="5fabd-108">Importez l'application sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="5fabd-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="5fabd-109">Définissez le répertoire racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="5fabd-109">Set the Application Root Directory.</span></span> <span data-ttu-id="5fabd-110">Par convention, il s'agit de %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="5fabd-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="5fabd-111">Copiez les fichiers Application.config et Application.manifest du répertoire racine de l'application sur l'ordinateur A vers le répertoire racine de l'application sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="5fabd-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="5fabd-112">Modifiez les adresses de point de terminaison de service dans le fichier Application.config sur l'ordinateur B pour identifier l'ordinateur approprié.</span><span class="sxs-lookup"><span data-stu-id="5fabd-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="5fabd-113">Par exemple, remplacez http://machineA/MyService par http://machineB/MyService.</span><span class="sxs-lookup"><span data-stu-id="5fabd-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="5fabd-114">Déplacement d'une application d'intégration hébergée sur le Web</span><span class="sxs-lookup"><span data-stu-id="5fabd-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="5fabd-115">Assurez-vous que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est installé sur les deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5fabd-115">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="5fabd-116">Exportez l'application de l'ordinateur A.</span><span class="sxs-lookup"><span data-stu-id="5fabd-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="5fabd-117">Importez l'application sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="5fabd-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="5fabd-118">Créez une racine virtuelle IIS sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="5fabd-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="5fabd-119">Copiez le fichier .svc (componentName.svc) et le fichier Web.config de la racine virtuelle sur l'ordinateur A vers la racine virtuelle que vous venez de créer sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="5fabd-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fabd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fabd-120">See Also</span></span>  
 [<span data-ttu-id="5fabd-121">Intégration de la vue d’ensemble des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="5fabd-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="5fabd-122">Comment : configurer les paramètres de Service COM +</span><span class="sxs-lookup"><span data-stu-id="5fabd-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="5fabd-123">Comment : utiliser l’outil de Configuration de modèle de Service COM +</span><span class="sxs-lookup"><span data-stu-id="5fabd-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
