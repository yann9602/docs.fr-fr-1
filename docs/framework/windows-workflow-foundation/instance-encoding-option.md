---
title: Option d'encodage d'instance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a874f88b787a99af0461ff47c3ae246442af2f19
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="d8cc7-102">Option d'encodage d'instance</span><span class="sxs-lookup"><span data-stu-id="d8cc7-102">Instance Encoding Option</span></span>
<span data-ttu-id="d8cc7-103">Le **Option d’encodage d’Instance** propriété du magasin d’instances de Workflow SQL vous permet de spécifier si le fournisseur de persistance SQL doit compresser les informations d’état du flux de travail d’instance à l’aide de l’algorithme GZip avant d’enregistrer le informations dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="d8cc7-104">Les valeurs autorisées pour cette propriété sont : Gzip et Aucun.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="d8cc7-105">La valeur par défaut est None.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-105">The default value is None.</span></span> <span data-ttu-id="d8cc7-106">La liste suivante décrit ces trois options.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="d8cc7-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-107">**GZip**.</span></span> <span data-ttu-id="d8cc7-108">Le fournisseur de persistance encode les informations d'état à l'aide de l'algorithme Gzip avant de rendre les informations d'état persistantes dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="d8cc7-109">**Aucun**.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-109">**None**.</span></span> <span data-ttu-id="d8cc7-110">Le fournisseur de persistance n'encode pas les informations d'état avant d'enregistrer les informations dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="d8cc7-111">L'encodage des informations de l'état de l'instance du workflow à l'aide du Gzip réduit la consommation de mémoire dans la base de données SQL ainsi que la consommation réseau si la base de données réside sur un autre ordinateur sur le réseau différent de l'ordinateur sur lequel l'hôte du service de workflow s'exécute.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="d8cc7-112">Obtenir une aide générale consiste à définir le **Option d’encodage d’Instance** propriété **aucun** si l’état d’instance de flux de travail est faible.</span><span class="sxs-lookup"><span data-stu-id="d8cc7-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
