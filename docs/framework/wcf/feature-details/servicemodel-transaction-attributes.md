---
title: "Attributs de transaction ServiceModel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transactions (WCF), ServiceModel (attributs)"
ms.assetid: 1e0d2436-6ae5-439b-9765-a448d6f60000
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Attributs de transaction ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit des propriétés sur les trois attributs <xref:System.ServiceModel> standard qui vous permettent de configurer le comportement des transactions d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
## TransactionFlowAttribute  
 L'attribut <xref:System.ServiceModel.TransactionFlowAttribute> spécifie la disposition d'une opération de contrat de service à accepter les transactions entrantes provenant d'un client.L'attribut fournit ce contrôle à l'aide de la propriété suivante : les transactions utilisent l'énumération <xref:System.ServiceModel.TransactionFlowOption> pour spécifier si une transaction entrante est <xref:System.ServiceModel.TransactionFlowOption>, <xref:System.ServiceModel.TransactionFlowOption> ou <xref:System.ServiceModel.TransactionFlowOption>.  
  
 C'est le seul attribut qui associe des opérations de service à des interactions externes avec un client.Les attributs décrits dans les sections suivantes concernent l'utilisation de transactions dans l'exécution de l'opération.  
  
## ServiceBehaviorAttribute  
 L'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> spécifie le comportement d'exécution interne d'une implémentation de contrat de service.Les propriétés spécifiques aux transactions de cet attribut incluent :  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> spécifie s'il faut terminer une transaction inachevée à la fermeture de la session.La valeur par défaut de cette propriété est `false`.Si cette propriété a la valeur `true`, et que la session entrante a été arrêtée normalement et n'a pas été fermée en raison d'erreurs client ou réseau, toute transaction inachevée est correctement exécutée.Sinon, si cette propriété a la valeur `false` ou si la session n'a pas été correctement fermée, toute transaction inachevée est restaurée à la fermeture de la session.Si cette propriété a la valeur `true`, le canal entrant doit être basé sur la session.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> spécifie si l'instance de service sous\-jacente est diffusée à la fin de l'exécution d'une transaction.La valeur par défaut de cette propriété est `true`.Le message entrant suivant provoque la création d'une nouvelle instance sous\-jacente, en ignorant les états par transaction que l'instance précédente a pu avoir.La diffusion d'une instance de service est une action interne effectuée par le service et n'a aucun impact sur les connexions ou sessions existantes que les clients ont pu établir.Cette fonctionnalité est équivalente à la fonction d'activation juste\-à\-temps fournie par COM\+.Si la propriété a la valeur `true`, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> doit être égal à <xref:System.ServiceModel.ConcurrencyMode>.Sinon, le service lève une exception de validation de configuration non valide au démarrage.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> spécifie le niveau d'isolation à utiliser pour les transactions dans le service ; cette propriété prend l'une des valeurs <xref:System.Transactions.IsolationLevel>.Si la propriété de niveau d'isolation locale est autre que <xref:System.Transactions.IsolationLevel>, le niveau d'isolation d'une transaction entrante doit correspondre au paramètre de cette propriété locale.Sinon, la transaction entrante est rejetée, et une erreur est renvoyée au client.Si <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`, et qu'aucune transaction n'est transmise, cette propriété détermine la valeur <xref:System.Transactions.IsolationLevel> à utiliser pour la transaction créée localement.Si <xref:System.Transactions.IsolationLevel> a la valeur <xref:System.Transactions.IsolationLevel>, <xref:System.Transactions.IsolationLevel><xref:System.Transactions.IsolationLevel> est utilisé.  
  
-   <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> spécifie le délai dans lequel une nouvelle transaction créée au niveau du service doit s'exécuter.Si au terme de ce délai la transaction n'a pas été exécutée, elle échouera.<xref:System.TimeSpan> est utilisé comme délai d'attente <xref:System.Transactions.TransactionScope> pour les opérations dont <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true` et pour lesquelles une nouvelle transaction a été créée.Le délai d'attente correspond à la durée maximale autorisée entre la création de la transaction et l'exécution de la phase 1 du protocole de validation en deux phases.La valeur du délai d'attente utilisée est toujours la valeur la plus petite entre la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> et le paramètre de configuration `transactionTimeout`.  
  
## OperationBehaviorAttribute  
 L'attribut <xref:System.ServiceModel.OperationBehaviorAttribute> spécifie les comportements des méthodes dans l'implémentation de service.Vous pouvez l'utiliser pour indiquer le comportement d'exécution spécifique de l'opération.Les propriétés de cet attribut n'affectent pas la description WSDL \(Web Service Description Language\) du contrat de service, et sont purement des éléments du modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui activent des fonctions courantes que les développeurs devraient sinon implémenter eux\-mêmes.  
  
 Cet attribut a les propriétés spécifiques aux transactions suivantes :  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> spécifie si une méthode doit s'exécuter dans une étendue de transaction active.La valeur par défaut est `false`.Si l'attribut <xref:System.ServiceModel.OperationBehaviorAttribute> n'est pas défini pour une méthode, cela implique également que cette méthode ne s'exécutera pas dans une transaction.Si une étendue de transaction n'est pas requise pour une opération, les transactions présentes dans l'en\-tête de message ne sont pas activées et restent en tant qu'éléments de <xref:System.ServiceModel.OperationContext.IncomingMessageProperties%2A> de <xref:System.ServiceModel.OperationContext>.Si une étendue de transaction est requise pour une opération, la source de la transaction est dérivée de l'un des éléments suivants :  
  
    -   Si une transaction est transmise à partir du client, la méthode est exécutée sous une étendue de transaction créée à l'aide de cette transaction distribuée.  
  
    -   Avec un transport de mise en file d'attente, la transaction permettant de supprimer le message de la file d'attente est utilisée.Notez que la transaction utilisée n'est pas une transaction passée, en ce sens qu'elle n'a pas été fournie par l'expéditeur d'origine du message.  
  
    -   Un transport personnalisé peut fournir une transaction à l'aide de `TransportTransactionProperty`.  
  
    -   Si aucun des éléments ci\-dessus ne fournit de source externe à une transaction, une nouvelle instance <xref:System.Transactions.Transaction> est créée immédiatement avant d'appeler la méthode.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> spécifie si la transaction dans laquelle la méthode s'exécute est automatiquement effectuée si aucune exception non prise en charge n'est levée.Si cette propriété a la valeur `true`, l'infrastructure appelante marque automatiquement la transaction comme étant « exécutée » si la méthode utilisateur retourne une valeur sans lever d'exception.Si cette propriété a la valeur `false`, la transaction est jointe à l'instance et est uniquement marquée comme étant « exécutée » si le client appelle une méthode suivante marquée avec cette propriété définie à la valeur `true`, ou si une méthode suivante appelle explicitement <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>.Si aucune de ces conditions n'est vérifiée, la transaction n'est jamais « exécutée », et la tâche contenue n'est pas validée, sauf si la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionAutoCompleteOnSessionClose%2A> a la valeur `true`.Si cette propriété a la valeur `true`, vous devez utiliser un canal avec une session, et <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> doit avoir la valeur <xref:System.ServiceModel.InstanceContextMode>.