---
title: "Proc&#233;dure&#160;: sp&#233;cifier les membres dont les conflits d&#39;acc&#232;s concurrentiel doivent &#234;tre v&#233;rifi&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: sp&#233;cifier les membres dont les conflits d&#39;acc&#232;s concurrentiel doivent &#234;tre v&#233;rifi&#233;s
Appliquez l'un des trois enums à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sur un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour spécifier les membres à inclure dans les contrôles de mise à jour de la détection de conflits d'accès concurrentiel optimiste.  
  
 La propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> \(mappée au moment du design\) est utilisée avec des fonctionnalités d'accès concurrentiel à l'exécution dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Pour plus d'informations, consultez [Accès concurrentiel optimiste : vue d'ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Les valeurs membres d'origine sont comparées avec l'état actuel de la base de données tant qu'aucun membre n'est désigné comme `IsVersion=true`.  Pour plus d'informations, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### Pour utiliser systématiquement ce membre pour détecter les conflits  
  
1.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2.  Affectez la valeur `Always` à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### Pour ne jamais utiliser ce membre pour détecter des conflits  
  
1.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2.  Affectez la valeur `Never` à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### Pour utiliser ce membre pour détecter des conflits uniquement lorsque l'application a modifié la valeur du membre  
  
1.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2.  Affectez la valeur `WhenChanged` à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
## Exemple  
 L'exemple suivant spécifie que les objets `HomePage` ne doivent jamais être testés pendant des contrôles de mise à jour.  Pour plus d'informations, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## Voir aussi  
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)