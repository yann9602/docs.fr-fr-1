---
title: "Prise en charge des transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Prise en charge des transactions
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge trois modèles de transaction distincts.  Ces modèles sont présentés ci\-dessous dans l'ordre d'exécution des contrôles.  
  
## Transaction locale explicite  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, si la propriété <xref:System.Data.Linq.DataContext.Transaction%2A> a pour valeur une transaction \(`IDbTransaction`\), l'appel de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est effectué dans le contexte de la même transaction.  
  
 Il vous appartient de valider ou de restaurer la transaction une fois qu'elle s'est correctement exécutée.  La connexion qui correspond à la transaction doit être identique à celle utilisée pour construire le <xref:System.Data.Linq.DataContext>.  L'utilisation d'une autre connexion lève une exception.  
  
## Transaction distribuable explicite  
 Vous pouvez appeler des API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] \(y compris, mais de manière non limitative, <xref:System.Data.Linq.DataContext.SubmitChanges%2A>\) dans l'étendue d'un type <xref:System.Transactions.Transaction> actif.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] détecte que l'appel est dans l'étendue d'une transaction et ne crée pas de nouvelle transaction.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] évite également de fermer la connexion dans ce cas.  Vous pouvez effectuer une requête et exécuter <xref:System.Data.Linq.DataContext.SubmitChanges%2A> dans le contexte de ce type de transaction.  
  
## Transaction implicite  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vérifie si l'appel se trouve dans la portée d'une <xref:System.Transactions.Transaction> ou si la propriété `Transaction` \(`IDbTransaction`\) a pour valeur une transaction locale démarrée par l'utilisateur.  S'il ne détecte aucune transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] démarre une transaction locale \(`IDbTransaction`\) et l'utilise pour exécuter les commandes SQL générées.  Lorsque toutes les commandes SQL ont été exécutées correctement, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] valide la transaction locale et les retours.  
  
## Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [Procédure : mettre entre parenthèses des soumissions de données à l'aide de transactions](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)