---
title: "&#201;criture d&#39;une application transactionnelle  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &#201;criture d&#39;une application transactionnelle 
En tant que programmeur d'applications transactionnelles, vous pouvez bénéficier des deux modèles de programmation fournis par l'espace de noms <xref:System.Transactions> pour créer une transaction.Vous pouvez utiliser le modèle de programmation explicite à l'aide de la classe <xref:System.Transactions.Transaction> ou le modèle de programmation implicite, dans lequel les transactions sont automatiquement managées par l'infrastructure, à l'aide de la classe <xref:System.Transactions.TransactionScope>.Il est recommandé d'utiliser le modèle de transaction implicite pour le développement.Vous trouverez de plus amples informations sur l'utilisation d'une étendue de transaction dans la rubrique [Implémentation d'une transaction implicite à l'aide de l'étendue de transaction ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md).  
  
 Les deux modèles prennent en charge la validation d'une transaction lorsque le programme atteint un état cohérent.Si la validation réussit, la transaction est validée durablement.Si la validation échoue, la transaction est abandonnée.Si le programme d'application ne parvient pas à terminer la transaction avec succès, il tente d'abandonner et d'annuler les effets de la transaction.  
  
## Dans cette section  
  
### Création d'une transaction  
 L'espace de noms <xref:System.Transactions> fournit deux modèles pour la création d'une transaction.Ces modèles sont présentés dans les rubriques suivantes.  
  
 [Implémentation d'une transaction implicite à l'aide de l'étendue de transaction ](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions implicites à l'aide de la classe <xref:System.Transactions.TransactionScope>.  
  
 [Implémentation d'une transaction explicite à l'aide de CommittableTransaction ](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions explicites à l'aide de la classe <xref:System.Transactions.CommittableTransaction>.  
  
### Remontée de la gestion des transactions  
 Si une transaction doit accéder à une ressource dans un autre domaine d'application ou si vous voulez vous inscrire à un autre gestionnaire de ressources durables, la transaction est automatiquement remontée pour être managée par le MSDTC.La remontée de transactions est présentée dans la rubrique [Remontée de la gestion des transactions ](../../../../docs/framework/data/transactions/transaction-management-escalation.md).  
  
### Accès concurrentiel  
 La rubrique [Gestion de l'accès concurrentiel avec DependentTransaction ](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) explique comment mettre fin à l'accès concurrentiel entre des tâches asynchrones à l'aide de la classe <xref:System.Transactions.DependentTransaction>.  
  
### COM\+ Interop  
 La rubrique [Interopérabilité avec Enterprise Services et les transactions COM\+ ](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) explique comment faire interagir des transactions distribuées avec des transactions COM\+.  
  
### Diagnostics  
 La rubrique [Traces de diagnostic ](../../../../docs/framework/data/transactions/diagnostic-traces.md) explique comment utiliser les codes de traçage générés par l'infrastructure <xref:System.Transactions> pour résoudre les erreurs se produisant dans vos applications.  
  
### Utilisation d'ASP.NET  
 La rubrique [Utilisation de System.Transactions dans ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) explique comment utiliser <xref:System.Transactions> dans une application ASP.NET.