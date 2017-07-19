---
title: "Notions de base des transactions  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Notions de base des transactions 
Les transactions servent à lier plusieurs tâches ensemble.Par exemple, imaginez qu'une application effectue deux tâches.Une table est d'abord créée dans une base de données.Un objet spécialisé est ensuite appelé pour collecter, formater et insérer des données dans la nouvelle table.Ces deux tâches sont liées et sont même interdépendantes. Cela vous évite de créer une nouvelle table sauf si vous devez y insérer des données.L'exécution des deux tâches au sein de l'étendue d'une seule transaction effectue la connexion entre les deux.Si la seconde tâche échoue, la première est restaurée à un point intervenant avant la création de la nouvelle table.  
  
 Pour garantir un comportement prévisible, toutes les transactions doivent posséder les propriétés ACID de base \(atomicité, cohérence, isolation et durabilité\).Ces propriétés renforcent le rôle des transactions fondamentales en tant que propositions tout\-ou\-rien.Pour plus d'informations sur ACID, consultez [Propriétés ACID](http://go.microsoft.com/fwlink/?LinkId=98791) \(page pouvant être en anglais\).En résumé, les propriétés ACID garantissent la réussite ou l'échec d'un ensemble de tâches en tant qu'unité.En terminologie de traitement de transaction, une transaction est validée ou abandonnée.Pour qu'une transaction soit validée, tous les participants doivent s'assurer que chaque modification apportée aux données est permanente.Ces modifications doivent persister même en cas de panne du système ou de tout autre événement imprévu.Si l'un des participants seulement ne respecte pas cette garantie, l'intégralité de la transaction échoue.Toutes les modifications apportées aux données au sein de l'étendue de la transaction sont restaurées à un point spécifique.  
  
 Une transaction peut être restreinte à une seule ressource de données, telle qu'une base de données ou une file d'attente de messages.Dans ce cas, la transaction locale est gérée par le gestionnaire de transactions fourni par <xref:System.Transactions>, qui permet de générer un gain de performance.Contrôlées par la ressource de données, ces transactions sont efficaces et faciles à gérer.  
  
 Les transactions peuvent également couvrir plusieurs ressources de données.Les transactions distribuées permettent d'intégrer plusieurs opérations se produisant sur différents systèmes en une seule action de réussite ou d'échec.Dans ce cas, les transactions sont coordonnées par le MSDTC \(Microsoft Distributed Transaction Coordinator\) de chaque système.  
  
 Lors du développement d'une application transactionnelle à l'aide des classes fournies par <xref:System.Transactions>, il n'est pas nécessaire de s'interroger sur le type de transaction requise ou sur le gestionnaire de transactions concerné.L'infrastructure <xref:System.Transactions> gère automatiquement ces questions pour vous.  
  
 Lorsque vous créez une transaction, vous pouvez spécifier le niveau d'isolation qui s'y applique.Le niveau d'isolation, défini par la classe <xref:System.Transactions.IsolationLevel>, détermine le niveau d'accès d'autres transactions aux données affectées par votre transaction.  
  
 Vous pouvez créer des transactions à l'aide d'ADO.NET, <xref:System.EnterpriseServices> ou du nouveau modèle de programmation transactionnelle fourni par l'espace de noms <xref:System.Transactions>.La section [Fonctionnalités fournies par System.Transactions ](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) traite des fonctionnalités que vous pouvez utiliser pour écrire votre propre application transactionnelle à l'aide de l'espace de noms <xref:System.Transactions>.  
  
## Voir aussi  
 [Fonctionnalités fournies par System.Transactions ](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)