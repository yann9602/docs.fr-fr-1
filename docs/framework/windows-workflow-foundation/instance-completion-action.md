---
title: "Action d'achèvement de l'instance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d1e0f367ef167e5bf47d0936e0b3200ca7dbe19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="instance-completion-action"></a><span data-ttu-id="5f076-102">Action d'achèvement de l'instance</span><span class="sxs-lookup"><span data-stu-id="5f076-102">Instance Completion Action</span></span>
<span data-ttu-id="5f076-103">Le **Instance Completion Action** propriété du magasin d’instances de Workflow SQL vous permet de spécifier si les données et métadonnées d’instances de workflow sont supprimées de la base de données de persistance après que les instances ont abouti.</span><span class="sxs-lookup"><span data-stu-id="5f076-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="5f076-104">Les valeurs autorisées pour cette propriété sont **DeleteAll** et **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="5f076-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="5f076-105">La liste suivante décrit ces trois options :</span><span class="sxs-lookup"><span data-stu-id="5f076-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="5f076-106">**DeleteAll (par défaut).**</span><span class="sxs-lookup"><span data-stu-id="5f076-106">**DeleteAll (default).**</span></span> <span data-ttu-id="5f076-107">Si la valeur de la propriété est définie sur DeleteAll, les données et métadonnées d'instances de workflow sont supprimées de la base de données de persistance après que les instances ont abouti.</span><span class="sxs-lookup"><span data-stu-id="5f076-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="5f076-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="5f076-108">**DeleteNothing.**</span></span> <span data-ttu-id="5f076-109">Si la valeur de la propriété est définie sur DeleteNothing, les données et métadonnées d'instances de workflow sont conservées dans la base de données de persistance même après que les instances ont abouti.</span><span class="sxs-lookup"><span data-stu-id="5f076-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="5f076-110">Garder les informations d'état de l'instance après que les instances ont abouti entraîne l'augmentation de la taille de la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="5f076-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="5f076-111">À mesure que la taille de la base de données augmente, les opérations de base de données que le sous-système de persistance effectue prennent plus de temps pour s'exécuter, donc vous devez régulièrement vider les informations d'état de l'instance de la base de données de persistance pour optimiser l'exécution de ces services.</span><span class="sxs-lookup"><span data-stu-id="5f076-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
