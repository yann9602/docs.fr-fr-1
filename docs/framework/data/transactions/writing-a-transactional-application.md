---
title: "Écriture d’une application transactionnelle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec8537c4fdf80ffe448bba1376eacf519d67bcbe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="writing-a-transactional-application"></a>Écriture d’une application transactionnelle
En tant que programmeur d'applications transactionnelles, vous pouvez bénéficier des deux modèles de programmation fournis par l'espace de noms <xref:System.Transactions> pour créer une transaction. Vous pouvez utiliser le modèle de programmation explicit à l’aide de la <xref:System.Transactions.Transaction> classe ou le modèle de programmation implicit dans lequel les transactions sont gérées automatiquement par l’infrastructure, à l’aide de la <xref:System.Transactions.TransactionScope> classe. Nous vous recommandons d’utiliser le modèle de transaction implicite pour le développement. Vous trouverez plus d’informations sur l’utilisation d’une étendue de transaction dans le [mise en œuvre d’une Transaction implicite à l’aide de la portée de Transaction](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) rubrique.  
  
 Les deux modèles prennent en charge la validation d'une transaction lorsque le programme atteint un état cohérent. Si la validation réussit, la transaction est validée durablement. Si la validation échoue, la transaction est abandonnée. Si le programme d'application ne parvient pas à terminer la transaction avec succès, il tente d'abandonner et d'annuler les effets de la transaction.  
  
## <a name="in-this-section"></a>Dans cette section  
  
### <a name="creating-a-transaction"></a>Création d'une transaction  
 L'espace de noms <xref:System.Transactions> fournit deux modèles pour la création d'une transaction. Ces modèles sont présentés dans les rubriques suivantes.  
  
 [Implémentation d’une Transaction implicite à l’aide de la portée de Transaction](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions implicites à l'aide de la classe <xref:System.Transactions.TransactionScope>.  
  
 [Implémentation d’une Transaction explicite à l’aide de CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Décrit comment l'espace de noms <xref:System.Transactions> prend en charge la création de transactions explicites à l'aide de la classe <xref:System.Transactions.CommittableTransaction>.  
  
### <a name="escalating-transaction-management"></a>Remontée de la gestion des transactions  
 Si une transaction doit accéder à une ressource dans un autre domaine d'application ou si vous voulez vous inscrire à un autre gestionnaire de ressources durables, la transaction est automatiquement remontée pour être managée par le MSDTC. Escalade de verrous de transaction est traitée dans le [Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md) rubrique.  
  
### <a name="concurrency"></a>Concurrence  
 La rubrique [Managing Concurrency with DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) montre la réalisation de la concurrence entre des tâches asynchrones à l’aide de la <xref:System.Transactions.DependentTransaction> classe.  
  
### <a name="com-interop"></a>COM+ Interop  
 La rubrique [l’interopérabilité avec les Services d’entreprise et les Transactions COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) illustre comment vous pouvez effectuer vos transactions distribuées interagissent avec les transactions COM +.  
  
### <a name="diagnostics"></a>Diagnostics  
 [Suivis de diagnostic](../../../../docs/framework/data/transactions/diagnostic-traces.md) décrit comment vous pouvez utiliser les codes de trace générés par le <xref:System.Transactions> infrastructure pour résoudre les erreurs dans vos applications.  
  
### <a name="working-within-aspnet"></a>Utilisation d'ASP.NET  
 Le [à l’aide de System.Transactions dans ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) rubrique décrit comment vous pouvez utiliser avec succès <xref:System.Transactions> à l’intérieur d’une application ASP.NET.
