---
title: Prise en charge des transactions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 543ea3d1a0f767a10b36e040155e7e9304aca5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="transaction-support"></a>Prise en charge des transactions
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]prend en charge trois modèles de transaction distincts. Ces modèles sont présentés ci-dessous dans l'ordre d'exécution des contrôles.  
  
## <a name="explicit-local-transaction"></a>Transaction locale explicite  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, si la propriété <xref:System.Data.Linq.DataContext.Transaction%2A> a pour valeur une transaction (`IDbTransaction`), l'appel de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est effectué dans le contexte de la même transaction.  
  
 Il vous appartient de valider ou de restaurer la transaction une fois qu'elle s'est correctement exécutée. La connexion qui correspond à la transaction doit être identique à celle utilisée pour construire le <xref:System.Data.Linq.DataContext>. L'utilisation d'une autre connexion lève une exception.  
  
## <a name="explicit-distributable-transaction"></a>Transaction distribuable explicite  
 Vous pouvez appeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API (y compris mais non limité à <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) dans la portée d’un actif <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]détecte que l’appel est dans l’étendue d’une transaction et qu’il ne crée pas une nouvelle transaction. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]évite également dans ce cas la fermeture de la connexion. Vous pouvez effectuer une requête et exécuter <xref:System.Data.Linq.DataContext.SubmitChanges%2A> dans le contexte de ce type de transaction.  
  
## <a name="implicit-transaction"></a>Transaction implicite  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vérifie si l’appel est dans la portée d’un <xref:System.Transactions.Transaction> ou si le `Transaction` propriété (`IDbTransaction`) est définie sur une transaction locale démarrée par l’utilisateur. Si elle ne détecte aucune transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] démarre une transaction locale (`IDbTransaction`) et l’utilise pour exécuter les commandes SQL générées. Lorsque toutes les commandes SQL ont été exécutées avec succès, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] valide la transaction locale et le retourne.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Guide pratique pour mettre entre parenthèses des soumissions de données à l’aide de transactions](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
