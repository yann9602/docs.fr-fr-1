---
title: "Sécurité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0063497bc500a11d59dd88e0cb7d738d5c4bb6e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="security"></a>Sécurité
Le magasin d'instances de workflow SQL utilise les rôles de sécurité de base de données suivants pour sécuriser l'accès aux informations d'état de l'instance dans la base de données de persistance.  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**. Ce rôle dispose d'un accès en lecture et en écriture aux vues publiques et de droits d'exécution sur les procédures stockées impliquées dans la création, le chargement et l'enregistrement des instances.  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**. Ce rôle dispose d'un accès en lecture seule aux vues publiques.  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ce rôle a des droits d'exécution aux procédures stockées impliquées dans le processus de l'activation de l'instance. Pour plus d’informations sur l’activation de l’instance, consultez [activation d’Instance](../../../docs/framework/windows-workflow-foundation/instance-activation.md). Le compte d'utilisateur sous lequel un hôte générique (tel que le service de gestion du flux de travail de [!INCLUDE[dublin](../../../includes/dublin-md.md)]) doit être ajouté à ce rôle de base de données.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]sécurité pour les magasins de persistance avec Windows Server AppFabric, consultez [Configuration de la sécurité pour les magasins de persistance dans AppFabric](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Un client qui a accès à ses propres données d'instance dans le magasin d'instances a accès à toutes les autres instances dans le même magasin d'instances. Le magasin d'instances ne prend pas en charge les autorisations de sécurité au niveau de l'instance. Vous devez créer des magasins d'instances distincts et mapper des groupes/utilisateurs différents pour avoir accès aux différents magasins.
