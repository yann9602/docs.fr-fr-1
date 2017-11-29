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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5803b034eeecac66aa20951c5167b9e666f1fa8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="c4038-102">Option d'encodage d'instance</span><span class="sxs-lookup"><span data-stu-id="c4038-102">Instance Encoding Option</span></span>
<span data-ttu-id="c4038-103">Le **Option d’encodage d’Instance** propriété du magasin d’instances de Workflow SQL vous permet de spécifier si le fournisseur de persistance SQL doit compresser les informations d’état du flux de travail d’instance à l’aide de l’algorithme GZip avant d’enregistrer le informations dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="c4038-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="c4038-104">Les valeurs autorisées pour cette propriété sont : Gzip et Aucun.</span><span class="sxs-lookup"><span data-stu-id="c4038-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="c4038-105">La valeur par défaut est None.</span><span class="sxs-lookup"><span data-stu-id="c4038-105">The default value is None.</span></span> <span data-ttu-id="c4038-106">La liste suivante décrit ces trois options.</span><span class="sxs-lookup"><span data-stu-id="c4038-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="c4038-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="c4038-107">**GZip**.</span></span> <span data-ttu-id="c4038-108">Le fournisseur de persistance encode les informations d'état à l'aide de l'algorithme Gzip avant de rendre les informations d'état persistantes dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="c4038-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="c4038-109">**Aucun**.</span><span class="sxs-lookup"><span data-stu-id="c4038-109">**None**.</span></span> <span data-ttu-id="c4038-110">Le fournisseur de persistance n'encode pas les informations d'état avant d'enregistrer les informations dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="c4038-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="c4038-111">L'encodage des informations de l'état de l'instance du workflow à l'aide du Gzip réduit la consommation de mémoire dans la base de données SQL ainsi que la consommation réseau si la base de données réside sur un autre ordinateur sur le réseau différent de l'ordinateur sur lequel l'hôte du service de workflow s'exécute.</span><span class="sxs-lookup"><span data-stu-id="c4038-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="c4038-112">Obtenir une aide générale consiste à définir le **Option d’encodage d’Instance** propriété **aucun** si l’état d’instance de flux de travail est faible.</span><span class="sxs-lookup"><span data-stu-id="c4038-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
