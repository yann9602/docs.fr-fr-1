---
title: "Comment : ajouter une référence de services de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fb075bdb17f0d562d752bc4125141bb0bb2ab9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="6aff7-102">Comment : ajouter une référence de services de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="6aff7-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="6aff7-103">Vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6aff7-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="6aff7-104">De cette manière, vous pouvez accéder plus facilement à un service de données dans une application cliente que vous développez dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6aff7-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="6aff7-105">Lorsque vous complétez cette procédure, les classes de données sont générées selon les métadonnées obtenues auprès du service de données.</span><span class="sxs-lookup"><span data-stu-id="6aff7-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="6aff7-106">Pour plus d’informations, consultez [génération de la bibliothèque de Client de Service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6aff7-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="6aff7-107">Pour ajouter une référence de service de données</span><span class="sxs-lookup"><span data-stu-id="6aff7-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="6aff7-108">(Facultatif) Si le service de données n'appartient pas à la solution et n'est pas déjà en cours d'exécution, démarrez le service de données et notez l'URI du service de données.</span><span class="sxs-lookup"><span data-stu-id="6aff7-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="6aff7-109">Cliquez sur le projet client, puis sélectionnez **ajouter une référence de Service**.</span><span class="sxs-lookup"><span data-stu-id="6aff7-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="6aff7-110">Si le service de données fait partie de la solution actuelle, cliquez sur **Discover**.</span><span class="sxs-lookup"><span data-stu-id="6aff7-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="6aff7-111">ou</span><span class="sxs-lookup"><span data-stu-id="6aff7-111">-or-</span></span>  
  
     <span data-ttu-id="6aff7-112">Dans le **adresse** zone de texte, tapez l’URL de base du service de données, telles que `http://localhost:1234/Northwind.svc`, puis cliquez sur **accédez**.</span><span class="sxs-lookup"><span data-stu-id="6aff7-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="6aff7-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6aff7-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="6aff7-114">Cette opération ajoute un nouveau fichier de code qui contient les classes de données utilisées pour accéder et interagir avec les ressources du service des données sous la forme d'objets.</span><span class="sxs-lookup"><span data-stu-id="6aff7-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aff7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aff7-115">See Also</span></span>  
 [<span data-ttu-id="6aff7-116">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="6aff7-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
