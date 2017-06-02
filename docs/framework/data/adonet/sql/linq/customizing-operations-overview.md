---
title: "Personnalisation d&#39;op&#233;rations&#160;: vue d&#39;ensemble | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Personnalisation d&#39;op&#233;rations&#160;: vue d&#39;ensemble
Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère du SQL dynamique pour les opérations d'insertion, de mise à jour et de suppression selon le mappage. Dans la pratique cependant, vous souhaiterez généralement ajouter votre propre logique métier pour des raisons de sécurité, de validation, etc.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] propose, entre autres, les techniques suivantes pour la personnalisation de ces opérations.  
  
## Options de chargement  
 Dans vos requêtes, vous pouvez déterminer quelle quantité de données liées à votre cible principale est récupérée lorsque vous vous connectez à la base de données.  Cette fonctionnalité est implémentée en grande partie à l'aide de <xref:System.Data.Linq.DataLoadOptions>.  Pour plus d'informations, consultez [Comparaison entre le chargement différé et le chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## Méthodes partielles  
 Dans son mappage par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des méthodes partielles qui vous permettent d'implémenter votre logique métier.  Pour plus d'informations, consultez [Ajout d'une logique métier à l'aide de méthodes partielles](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## Procédures stockées et fonctions définies par l'utilisateur  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge l'utilisation de procédures stockées et de fonctions définies par l'utilisateur.  Les procédures stockées sont couramment utilisées pour personnaliser des opérations.  Pour plus d'informations, consultez [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## Voir aussi  
 [Personnalisation des opérations d'insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)