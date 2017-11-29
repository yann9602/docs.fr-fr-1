---
title: "Comment : définir la chaîne de connexion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 757b70d99a7f2b499d4ad5aab2be2bb61b28af0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="902fa-102">Comment : définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="902fa-102">How to: Define the Connection String</span></span>
<span data-ttu-id="902fa-103">Cette rubrique montre comment définir la chaîne utilisée pour la connexion à un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="902fa-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="902fa-104">Cette rubrique est basée sur le [vente AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="902fa-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="902fa-105">Le modèle de vente AdventureWorks Sales Model est utilisé dans toutes les rubriques liées aux tâches de la documentation [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="902fa-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="902fa-106">Cette rubrique suppose que vous avez déjà configuré le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et défini le modèle de vente AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="902fa-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="902fa-107">Pour plus d’informations, consultez [Comment : définir manuellement les fichiers de modèle et de mappage](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span><span class="sxs-lookup"><span data-stu-id="902fa-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="902fa-108">Les procédures décrites dans cette rubrique sont également incluses dans [Comment : configurer manuellement un projet Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span><span class="sxs-lookup"><span data-stu-id="902fa-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="902fa-109">Si vous utilisez l'Assistant [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] dans un projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)], il génère automatiquement un fichier .edmx et configure le projet pour qu'il utilise [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="902fa-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="902fa-110">Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="902fa-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="902fa-111">Pour définir la chaîne de connexion Entity Framework</span><span class="sxs-lookup"><span data-stu-id="902fa-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="902fa-112">Ouvrez le fichier de configuration de l'application (app.config) du projet et ajoutez la chaîne de connexion suivante :</span><span class="sxs-lookup"><span data-stu-id="902fa-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="902fa-113">Si votre projet n’a pas un fichier de configuration d’application, vous pouvez ajouter une catégorie en sélectionnant **ajouter un nouvel élément** à partir de la **projet** menu, en sélectionnant le **général** catégorie, en sélectionnant **fichier de Configuration d’Application**, puis en cliquant sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="902fa-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902fa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="902fa-114">See Also</span></span>  
 [<span data-ttu-id="902fa-115">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="902fa-115">Quickstart</span></span>](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="902fa-116">Comment : créer un fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="902fa-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="902fa-117">Outils ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="902fa-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
