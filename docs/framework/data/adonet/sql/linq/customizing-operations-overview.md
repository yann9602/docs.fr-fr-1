---
title: "Personnalisation d'opérations : vue d'ensemble"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9776daa28b0a7ffcd3b721f004f5b9a44dd09f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-overview"></a>Personnalisation d'opérations : vue d'ensemble
Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour les opérations d'insertion, de mise à jour et de suppression selon le mappage. Dans la pratique cependant, vous souhaiterez généralement ajouter votre propre logique métier pour des raisons de sécurité, de validation, etc.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]techniques de personnalisation de ces opérations sont les suivantes.  
  
## <a name="loading-options"></a>Options de chargement  
 Dans vos requêtes, vous pouvez déterminer quelle quantité de données liées à votre cible principale est récupérée lorsque vous vous connectez à la base de données. Cette fonctionnalité est implémentée en grande partie à l'aide de <xref:System.Data.Linq.DataLoadOptions>. Pour plus d’informations, consultez [différée / chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Méthodes partielles  
 Dans son mappage par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des méthodes partielles qui vous permettent d'implémenter votre logique métier. Pour plus d’informations, consultez [Ajout d’entreprise logique par à l’aide de méthodes partielles](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procédures stockées et fonctions définies par l'utilisateur  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]prend en charge l’utilisation de procédures stockées et fonctions définies par l’utilisateur. Les procédures stockées sont couramment utilisées pour personnaliser des opérations. Pour plus d’informations, consultez [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
