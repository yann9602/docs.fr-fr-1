---
title: Configuration des transactions ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef1d8a9e749c06701aa0a187f81b5b345518c07b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-transaction-configuration"></a>Configuration des transactions ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit trois attributs permettant de configurer des transactions pour un service : `transactionFlow`, `transactionProtocol` et `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Configuration de transactionFlow  
 La plupart des liaisons prédéfinies fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contiennent les attributs `transactionFlow` et `transactionProtocol` afin de vous permettre de configurer la liaison pour qu'elle accepte des transactions entrantes pour un point de terminaison spécifique à l'aide d'un protocole de flux de transaction spécifique. Par ailleurs, l'élément `transactionFlow` et son attribut `transactionProtocol` vous permettent de générer votre propre liaison personnalisée. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les éléments de configuration, consultez [ \<liaison >](../../../../docs/framework/misc/binding.md) et [schéma de Configuration WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 L'attribut `transactionFlow` spécifie si le flux de transaction est activé pour les points de terminaison de service qui utilisent la liaison.  
  
## <a name="configuring-transactionprotocol"></a>Configuration de transactionProtocol  
 L'attribut `transactionProtocol` spécifie le protocole de transaction à utiliser avec les points de terminaison de service qui utilisent la liaison.  
  
 L'exemple suivant présente une section de configuration qui configure la liaison spécifiée pour prendre en charge le flux de transaction, ainsi qu'une utilisation du protocole WS-AtomicTransaction.  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"   
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"   
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a>Configuration de transactionTimeout  
 Vous pouvez configurer l'attribut `transactionTimeout` pour votre service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans l'élément `behavior` du fichier de configuration. Le code suivant montre comment procéder.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 L'attribut `transactionTimeout` spécifie le délai dans lequel une nouvelle transaction créée au niveau du service doit se terminer. Il est utilisé comme délai d'attente <xref:System.Transactions.TransactionScope> pour toute opération qui établit une nouvelle transaction ; si <xref:System.ServiceModel.OperationBehaviorAttribute> est appliqué, la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.  
  
 Le délai d'attente spécifie la durée entre la création de la transaction et l'exécution de la phase 1 du protocole de validation en deux phases.  
  
 Si cet attribut est défini dans une section de configuration de `service`, vous devez appliquer au moins une méthode du service correspondant avec <xref:System.ServiceModel.OperationBehaviorAttribute>, dans lequel la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.  
  
 Notez que la valeur du délai d'attente utilisée est toujours la plus petite entre le paramètre de configuration `transactionTimeout` et la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [\<liaison >](../../../../docs/framework/misc/binding.md)  
 [Schéma de configuration de WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
