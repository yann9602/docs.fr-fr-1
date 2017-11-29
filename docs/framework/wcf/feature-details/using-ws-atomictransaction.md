---
title: Utilisation de WS-AtomicTransaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7046add86f1255b222640912be02c08b98cb9cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-ws-atomictransaction"></a>Utilisation de WS-AtomicTransaction
WS-AtomicTransaction (WS-AT) est un protocole de transaction interopérable. Ce protocole vous permet de transférer des transactions distribuées à l'aide de messages de service Web et d'assurer la coordination d'infrastructures de transaction hétérogènes de manière interopérable. WS-AT utilise un protocole de validation en deux phases pour un résultat atomique entre les applications distribuées, les gestionnaires de transactions et les gestionnaires de ressources.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], pour permettre l'implémentation du protocole WS-AT, intègre un service de protocole au gestionnaire de transactions Microsoft Distributed Transaction Coordinator (MSDTC). Grâce au protocole WS-AT, les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent transférer des transactions vers d'autres applications, notamment vers des services Web interopérables construits à l'aide de technologies tierces.  
  
 Lorsqu'une transaction est transférée entre une application cliente et une application serveur, le protocole utilisé dépend de la liaison exposée par le serveur sur le point de terminaison sélectionné par le client. Certaines liaisons définies par le système [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifient par défaut le protocole `OleTransactions` comme format de propagation de transaction, tandis que d'autres choisissent par défaut le protocole WS-AT. Vous pouvez également modifier le protocole de transaction utilisé par les liaisons en programmant le protocole de votre choix.  
  
 Le choix du protocole a des conséquences sur :  
  
-   Le format des en-têtes de message utilisé pour transférer la transaction du client au serveur.  
  
-   Le protocole réseau utilisé pour exécuter le protocole de validation en deux phases entre le gestionnaire de transactions du client et la transaction du serveur et ainsi déterminer le résultat final de la transaction.  
  
 Si le serveur et le client ont été créés à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous n'avez pas besoin d'utiliser le protocole WS-AT. Il vous suffit en effet d'utiliser les paramètres par défaut de `NetTcpBinding` et d'activer l'attribut `TransactionFlow` pour que le protocole `OleTransactions` soit utilisé à la place. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md). En revanche, si vous transférez des transactions vers des services Web construits à l’aide de technologies tierces, vous devez utiliser le protocole WS-AT.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration prise en charge de WS-Atomic Transaction](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
