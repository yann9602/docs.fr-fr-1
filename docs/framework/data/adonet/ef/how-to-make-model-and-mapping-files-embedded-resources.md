---
title: "Comment : transformer les fichiers modèle et les fichiers de mappage en ressources incorporées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 60c17ebbdd4b7e7f460855d4888a922da9c953d2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="1e99b-102">Comment : transformer les fichiers modèle et les fichiers de mappage en ressources incorporées</span><span class="sxs-lookup"><span data-stu-id="1e99b-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="1e99b-103">Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] vous permet de déployer des fichiers de mappage et de modèle en tant que ressources incorporées d’une application.</span><span class="sxs-lookup"><span data-stu-id="1e99b-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="1e99b-104">L'assembly comprenant les fichiers de mappage et de modèle incorporés doit être chargé dans le même domaine d'application que la connexion d'entité.</span><span class="sxs-lookup"><span data-stu-id="1e99b-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="1e99b-105">Pour plus d’informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="1e99b-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="1e99b-106">Par défaut, les outils [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] incorporent les fichiers de mappage et de modèle.</span><span class="sxs-lookup"><span data-stu-id="1e99b-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="1e99b-107">Lorsque vous définissez manuellement les fichiers de mappage et de modèle, utilisez cette procédure pour garantir que les fichiers sont déployés en tant que ressources incorporées avec une application [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e99b-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e99b-108">Pour conserver des ressources incorporées, vous devez répéter cette procédure chaque fois que les fichiers de mappage et de modèle sont modifiés.</span><span class="sxs-lookup"><span data-stu-id="1e99b-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="1e99b-109">Pour incorporer les fichiers de mappage et de modèle</span><span class="sxs-lookup"><span data-stu-id="1e99b-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="1e99b-110">Dans **l’Explorateur de solutions**, sélectionnez le fichier conceptuel (.csdl).</span><span class="sxs-lookup"><span data-stu-id="1e99b-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="1e99b-111">Dans le **propriétés** volet, définissez **Action de génération** à **ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="1e99b-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="1e99b-112">Répétez les étapes 1 et 2 pour le fichier de stockage (.ssdl) et le fichier de mappage (.msl).</span><span class="sxs-lookup"><span data-stu-id="1e99b-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="1e99b-113">Dans **l’Explorateur de solutions**, double-cliquez sur le fichier App.config et modifiez le `Metadata` paramètre dans le `connectionString` attribut basé sur l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="1e99b-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="1e99b-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="1e99b-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="1e99b-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="1e99b-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="1e99b-116">Pour plus d’informations, consultez [Chaînes de connexion](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="1e99b-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e99b-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e99b-117">Example</span></span>  
 <span data-ttu-id="1e99b-118">Fait référence à la chaîne de connexion pour les fichiers de mappage et de modèle incorporés le [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="1e99b-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="1e99b-119">Cette chaîne de connexion est stockée dans le fichier App.config du projet.</span><span class="sxs-lookup"><span data-stu-id="1e99b-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="1e99b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e99b-120">See Also</span></span>  
 [<span data-ttu-id="1e99b-121">Modélisation et mappage</span><span class="sxs-lookup"><span data-stu-id="1e99b-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="1e99b-122">Guide pratique pour définir la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="1e99b-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="1e99b-123">Guide pratique pour créer une chaîne de connexion EntityConnection</span><span class="sxs-lookup"><span data-stu-id="1e99b-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="1e99b-124">Outils ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="1e99b-124">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
