---
title: Magasins d'instances
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c794c6e20b479ea4686caba29704f8851d108432
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="instance-stores"></a>Magasins d'instances
Un magasin d'instances est un conteneur logique d'instances. Il s'agit de l'endroit où les données et les métadonnées d'instance sont stockées. Un magasin d'instances n'implique pas de stockage physique dédié. Il peut contenir des informations durables dans une base de données SQL Server ou des informations d'état non durables dans une mémoire. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] est fourni avec le magasin d'instances de workflow SQL, lequel est une implémentation concrète d'un magasin d'instances qui permet aux workflows de rendre des données et des métadonnées d'instance persistantes dans une base de données SQL Server 2005 ou 2008. En outre, Windows Server AppFabric fournit également une implémentation concrète d'un magasin d'instances. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Magasin d’instances Windows Server App Fabric, les requêtes et les fournisseurs de contrôle](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 L'API de persistance est l'interface entre un hôte et un magasin d'instances qui permet à l'hôte d'envoyer des demandes de commande (par exemple, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> et <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) au magasin d'instances. L'implémentation concrète de cette API est appelée fournisseur de persistance. Le fournisseur de persistance reçoit des demandes d'un hôte et modifie le magasin d'instances.  
  
 Les hôtes et les magasins d'instances sont enfichables afin qu'un hôte puisse être utilisé avec de nombreux magasins d'instances et qu'un magasin d'instances puisse être utilisé avec de nombreux hôtes. Un magasin d’instances est généralement optimisé pour les modèles d’utilisation d’un hôte particulier, bien que le magasin d’instances et l’hôte puissent évoluer sur des cycles de vie indépendants. Par exemple, le **WorkflowServiceHost** et **SqlWorkflowInstanceStore** sont conçus pour bien fonctionner ensemble. Vous pouvez créer votre propre magasin d’instances pour rendre persistantes les données et métadonnées d’instances de service de flux de travail et utiliser ce magasin d’instances avec le **WorkflowServiceHost**. Par exemple, vous pouvez créer un OracleWorkflowInstanceStore qui laisse des workflows rendre les informations persistantes dans une base de données Oracle au lieu de les enregistrer dans une base de données SQL Server.  
  
 Il est courant que les hôtes soient étendus avec des fonctionnalités supplémentaires qui modifient les objets rendus persistants. Par exemple, un système de persistance d’instance peut avoir un hôte de flux de travail, une extension qui prend en charge l’opération « Suspend » et un magasin d’instances SQL.  L'hôte de workflow peut envoyer une commande standard telle que Save ou Load pour enregistrer ou charger un workflow à partir d'un magasin d'instances ou pour enregistrer un workflow dans un magasin d'instances. L'extension d'interruption peut ajouter une sémantique supplémentaire aux commandes pour enregistrer et charger des instances de workflow afin qu'une instance de workflow interrompue ne puisse pas être chargée. Le fournisseur de persistance du magasin d'instances SQL comprend les commandes d'enregistrement et de chargement des instances de workflow et implémente ces commandes en appelant des procédures stockées appropriées qui modifient les tables d'objets persistants dans une base de données SQL Server.  
  
 Un hôte agit comme un propriétaire d'instance dans un magasin d'instances. Il peut se comporter comme le propriétaire de plusieurs instances avec plusieurs magasins d'instances en même temps. L'hôte fournit des GUID pour les clés d'instance associées aux instances. Une clé d'instance est un alias unique qui identifie une instance. Le système de persistance crée, met à jour et supprime les informations de propriétaire d'instance à mesure qu'il exécute les commandes demandées par les hôtes.  
  
 La liste suivante répertorie les étapes importantes de l'interaction de l'hôte avec le magasin d'instances :  
  
1.  Obtenir un **InstanceStore** à partir d’un fournisseur de persistance.  

2.  Obtenir le handle à une instance en appelant le <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> méthode sur le **InstanceStore**.  
  
3.  Appeler des commandes sur le handle d’instance en appelant le <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> méthode sur le **InstanceStore**.  
  
4.  Examinez le <xref:System.Runtime.DurableInstancing.InstanceView> retourné par **InstanceStore.Execute** pour déterminer les résultats des commandes.
